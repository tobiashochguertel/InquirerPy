# InquirerPy (published as **InquirerPrompt**)

> **🍴 Community-Maintained Fork**
>
> This is a community fork of [kazhala/InquirerPy](https://github.com/kazhala/InquirerPy), maintained at
> [`tobiashochguertel/InquirerPy`](https://github.com/tobiashochguertel/InquirerPy).
>
> The original project is a fantastic library that we rely on and deeply appreciate. Unfortunately the upstream
> has been quiet for some time, and the community has accumulated valuable bug fixes, compatibility updates,
> and feature contributions that have not been reviewed or merged. Rather than letting those improvements go to
> waste, we decided to maintain this fork so that InquirerPy stays healthy and up-to-date for everyone.
>
> **Our goal is to contribute all improvements back upstream** — if the original author becomes active again
> we will happily defer to them. Until then, we are keeping the lights on here. 🙏
>
> | Item | Detail |
> |------|--------|
> | Upstream | [kazhala/InquirerPy](https://github.com/kazhala/InquirerPy) @ `0.3.4` (last commit Nov 2022) |
> | This fork | [tobiashochguertel/InquirerPy](https://github.com/tobiashochguertel/InquirerPy) |
> | Install | `pip install InquirerPrompt` (import still: `import InquirerPy`) |
> | Docs | [InquirerPrompt.readthedocs.io](https://InquirerPrompt.readthedocs.io) |
>
> If you are the original author and would like to resume ownership or collaborate, please open an issue — we
> would love to work together!

---

[![CI](https://github.com/tobiashochguertel/InquirerPy/workflows/CI/badge.svg)](https://github.com/tobiashochguertel/InquirerPy/actions?query=workflow%3ACI)
[![Coverage](https://codecov.io/gh/tobiashochguertel/InquirerPy/branch/master/graph/badge.svg)](https://codecov.io/gh/tobiashochguertel/InquirerPy)
[![Version](https://img.shields.io/pypi/pyversions/InquirerPrompt)](https://pypi.org/project/InquirerPrompt/)
[![PyPi](https://img.shields.io/pypi/v/InquirerPrompt)](https://pypi.org/project/InquirerPrompt/)
[![Upstream](https://img.shields.io/badge/upstream-kazhala%2FInquirerPy-blue)](https://github.com/kazhala/InquirerPy)

Documentation: [InquirerPrompt.readthedocs.io](https://InquirerPrompt.readthedocs.io)

<!-- start intro -->

## Introduction

`InquirerPy` is a Python port of the famous [Inquirer.js](https://github.com/SBoudrias/Inquirer.js/) (A collection of common interactive command line user interfaces).
This project is a re-implementation of the [PyInquirer](https://github.com/CITGuru/PyInquirer) project, with bug fixes of known issues, new prompts, backward compatible APIs
as well as more customisation options.

<!-- end intro -->

![Demo](https://github.com/kazhala/gif/blob/master/InquirerPy-demo.gif)

## Motivation

[PyInquirer](https://github.com/CITGuru/PyInquirer) is a great Python port of [Inquirer.js](https://github.com/SBoudrias/Inquirer.js/), however, the project is slowly reaching
to an unmaintained state with various issues left behind and no intention to implement more feature requests. I was heavily relying on this library for other projects but
could not proceed due to the limitations.

Some noticeable ones that bother me the most:

- hard limit on `prompt_toolkit` version 1.0.3
- various color issues
- various cursor issues
- No options for VI/Emacs navigation key bindings
- Pagination option doesn't work

This project uses python3.7+ type hinting with focus on resolving above issues while providing greater customisation options.

## Requirements

### OS

Leveraging [prompt_toolkit](https://github.com/prompt-toolkit/python-prompt-toolkit), `InquirerPy` works cross platform for all OS. Although Unix platform may have a better experience than Windows.

### Python

```
python >= 3.7
```

## Getting Started

Checkout full documentation **[here](https://InquirerPrompt.readthedocs.io/)**.

### Install

```sh
pip3 install InquirerPy
```

### Quick Start

#### Classic Syntax (PyInquirer)

```python
from InquirerPy import prompt

questions = [
    {"type": "input", "message": "What's your name:", "name": "name"},
    {"type": "confirm", "message": "Confirm?", "name": "confirm"},
]
result = prompt(questions)
name = result["name"]
confirm = result["confirm"]
```

#### Alternate Syntax

```python
from InquirerPy import inquirer

name = inquirer.text(message="What's your name:").execute()
confirm = inquirer.confirm(message="Confirm?").execute()
```

<!-- start migration -->

## Migrating from PyInquirer

Most APIs from [PyInquirer](https://github.com/CITGuru/PyInquirer) should be compatible with `InquirerPy`. If you have discovered more incompatible APIs, please
create an issue or directly update README via a pull request.

### EditorPrompt

`InquirerPy` does not support [editor](https://github.com/CITGuru/PyInquirer#editor---type-editor) prompt as of now.

### CheckboxPrompt

The following table contains the mapping of incompatible parameters.

| PyInquirer      | InquirerPy      |
| --------------- | --------------- |
| pointer_sign    | pointer         |
| selected_sign   | enabled_symbol  |
| unselected_sign | disabled_symbol |

### Style

Every style keys from [PyInquirer](https://github.com/CITGuru/PyInquirer) is present in `InquirerPy` except the ones in the following table.

| PyInquirer | InquirerPy |
| ---------- | ---------- |
| selected   | pointer    |

Although `InquirerPy` support all the keys from [PyInquirer](https://github.com/CITGuru/PyInquirer), the styling works slightly different.
Please refer to the [Style](https://InquirerPrompt.readthedocs.io/en/latest/pages/style.html) documentation for detailed information.

<!-- end migration -->

## Similar projects

### questionary

[questionary](https://github.com/tmbo/questionary) is a fantastic fork which supports `prompt_toolkit` 3.0.0+ with performance improvement and more customisation options.
It's already a well established and stable library.

Comparing with [questionary](https://github.com/tmbo/questionary), `InquirerPy` offers even more customisation options in styles, UI as well as key bindings. `InquirerPy` also provides a new
and powerful [fuzzy](https://InquirerPrompt.readthedocs.io/en/latest/pages/prompts/fuzzy.html) prompt.

### python-inquirer

[python-inquirer](https://github.com/magmax/python-inquirer) is another great Python port of [Inquirer.js](https://github.com/SBoudrias/Inquirer.js/). Instead of using `prompt_toolkit`, it
leverages the library `blessed` to implement the UI.

Before implementing `InquirerPy`, this library came up as an alternative. It's a more stable library comparing to the original [PyInquirer](https://github.com/CITGuru/PyInquirer), however
it has a rather limited customisation options and an older UI which did not solve the issues I was facing described in the [Motivation](#Motivation) section.

Comparing with [python-inquirer](https://github.com/magmax/python-inquirer), `InquirerPy` offers a slightly better UI,
more customisation options in key bindings and styles, providing pagination as well as more prompts.

## Credit

This project is based on the great work done by the following projects & their authors.

- [PyInquirer](https://github.com/CITGuru/PyInquirer)
- [prompt_toolkit](https://github.com/prompt-toolkit/python-prompt-toolkit)

## License

This project is licensed under [MIT](https://github.com/kazhala/InquirerPy/blob/master/LICENSE).
