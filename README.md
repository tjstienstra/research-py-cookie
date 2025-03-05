# Minimal Cookie for a Scientific Python Project
This template aims to provide a minimal setup for a scientific project in pure Python.
[scientific-python/cookie] has been used as a starting point, which I would recommend if one prefers a more extensive setup.

However, as this cookie isn't aimed at publishing a package, there are some changes to minimize the codebase.
Major changes are:
- Hatchling has been assumed, but it should be changed to [uv] in the future.
- Removal of the noxfile because I have the preference of staying closer to the actual tools being used.
- Removal of sphinx documentation. Most projects won't start out with this and I would consider switching to MkDocs.
- Removal of mypy. Though I love type hinting, it just seems that one ends up fighting the type checker a few times too often. I would like to include a type checker in the future, but before doing so I should research the different options and setups.
- CD workflow has been removed because I don't expect these kind of projects to be released on PyPi.
- Include all ruff rules. I prefer the approach of adhering to all rules and just ignoring those which are impractical.

TODO: Auto creating the notebooks directory based on a boolean introduced some problems, so it has been excluded from the template at the moment.

## Getting started
Create your project using [copier], [cookiecutter] or [cruft], e.g.:
```bash
cruft create https://github.com/tjstienstra/research-py-cookie
```

## Useful Commands
Make sure you have installed [uv]. To install something as a tool like copier, use:
```bash
uv tool install cruft
```
To create an environment including all optional dependencies while also specifying the Python version, use:
```bash
uv sync --all-extras --python 3.13
```
Don't forget to install the precommit hooks:
```bash
pre-commit install
```
To run ruff you can, while also fixing simple problems, use:
```bash
ruff check --fix
```
and:
```bash
ruff format
```
[pytest-xdist] is useful if you like to use multiple CPUs:
```bash
pytest -n auto
```

## VS Code Setings
Below are some settings I like to use in my Python projects.
I'm using `Git Bash` as my default terminal, while having a local `.bashrc` file to set local aliases like `alias rc='ruff check'`.
Additionally, I prefer wrapping in general unless I want to maintain a certain line length and auto whitespace formatting is for consistency.
```json
{
  "terminal.integrated.defaultProfile.windows": "Git Bash",
  "rewrap.autoWrap.enabled": true,
  "files.trimTrailingWhitespace": true,
  "code-eol.crlfCharacter": "↵",
  "editor.renderWhitespace": "all",
  "[markdown]": {
    "editor.defaultFormatter": "GitHub.copilot",
    "editor.rulers": [88],
    "editor.wordWrap": "off",
    "editor.formatOnSave": true
  },
  "[python]": {
    "editor.defaultFormatter": "charliermarsh.ruff",
    "editor.rulers": [88],
    "editor.wordWrap": "off",
    "editor.formatOnSave": true
  },
  "[git-commit]": {
    "editor.rulers": [50, 72],
    "editor.wordWrap": "off"
  },
  "git.autofetch": true,
  "terminal.integrated.profiles.windows": {
    "Git Bash": {
      "source": "Git Bash",
      "args": ["--init-file", "${workspaceFolder}/.bashrc"]
    }
  },
}
```

<!-- prettier-ignore-start -->
[cookiecutter]:             https://www.cookiecutter.io/
[cruft]:                    https://cruft.github.io/cruft/
[copier]:                   https://copier.readthedocs.io/en/stable/
[scientific-python/cookie]: https://github.com/scientific-python/cookie
[uv]:                       https://docs.astral.sh/uv/
[uv-dependencies]:          https://docs.astral.sh/uv/concepts/projects/dependencies/
[pytest-xdist]:             https://pypi.org/project/pytest-xdist/
[mypy-prof-settings]:       https://careers.wolt.com/en/blog/tech/professional-grade-mypy-configuration
<!-- prettier-ignore-end -->
