Dead Links: A Plugin for Pelican
================================

[![Build Status](https://img.shields.io/github/actions/workflow/status/pelican-plugins/deadlinks/main.yml?branch=main)](https://github.com/pelican-plugins/deadlinks/actions)
[![PyPI Version](https://img.shields.io/pypi/v/pelican-deadlinks)](https://pypi.org/project/pelican-deadlinks/)
[![Downloads](https://img.shields.io/pypi/dm/pelican-deadlinks)](https://pypi.org/project/pelican-deadlinks/)
![License](https://img.shields.io/pypi/l/pelican-deadlinks?color=blue)

This Pelican plugin scans links and check their status codes. For responses such as 403 or 404, the plugin adds a `disabled` class to the anchor, extends the anchor with a `span` label, and prints a warning to the console logger.

Installation
------------

This plugin can be installed via:

    python -m pip install pelican-deadlinks

As long as you have not explicitly added a `PLUGINS` setting to your Pelican settings file, then the newly-installed plugin should be automatically detected and enabled. Otherwise, you must add `deadlinks` to your existing `PLUGINS` list. For more information, please see the [How to Use Plugins](https://docs.getpelican.com/en/latest/plugins.html#how-to-use-plugins) documentation.

Usage
-----

To enable the dead link checker, set the `DEADLINKS_VALIDATION` option in your Pelican settings file to `True`. Alternatively, if you don’t want to validate links every time, you can selectively enable link validation at run-time via:

    pelican content -e DEADLINKS_VALIDATION=true

Additionally, the following options can be changed:

```python
DEADLINKS_OPTIONS = {
    "archive": True,
    "classes": ["custom-class1", "disabled"],
    "labels": True,
    "timeout_duration_ms": 1000,
    "timeout_is_error": False,
}
```

Options:

| Name | Description | Default value |
| ------ | ----------- | ------------- |
| `archive` | True/False. When enabled invalid links will be replaced with proper archive.org entry | True |
| `classes` | List of classes to be add to anchor element | Empty list |
| `labels` | Insert bootstrap's label after the anchor element | False |
| `timeout_duration_ms` | Time in ms after which request is considered as timed out | 1000 |
| `timeout_is_error` | True/False. When enabled every time out is considered as dead link | False |

Contributing
------------

Contributions are welcome and much appreciated. Every little bit helps. You can contribute by improving the documentation, adding missing features, and fixing bugs. You can also help out by reviewing and commenting on [existing issues][].

To start contributing to this plugin, review the [Contributing to Pelican][] documentation, beginning with the **Contributing Code** section.

[existing issues]: https://github.com/pelican-plugins/deadlinks/issues
[Contributing to Pelican]: https://docs.getpelican.com/en/latest/contribute.html

License
-------

This project is licensed under the MIT license.
