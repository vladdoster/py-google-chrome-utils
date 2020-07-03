# py-chrome-export [![Build Status](https://travis-ci.org/vladdoster/py-chrome-export.svg?branch=master)](https://travis-ci.org/vladdoster/py-chrome-export)

Python scripts to convert [Google Chrome]’s bookmarks and history to the [standard HTML-ish bookmarks file format][format] or [github markdown].

[Google Chrome]: http://www.google.com/chrome/
[format]: https://msdn.microsoft.com/en-us/library/aa753582(v=vs.85).aspx
[github markdown]: https://github.github.com/gfm/

The functionality to do this for bookmarks is already built into Chrome (select Bookmarks&nbsp;→ Bookmarks Manager, then click “Organize” and select “Export Bookmarks…”).

## Installation

### Arch Linux

    sudo pacman -S py-chrome-exporter

### Homebrew

If you have [Homebrew] installed, you can install these scripts with

    brew install py-chrome-exporter

[Homebrew]: https://brew.sh

### Manual installation

1. Download the .zip or .tar.gz file for the [latest release] and extract it.

2. Run the `Makefile` to install `chrome-exporter` and accompanying `man` page.

    sudo make install


[latest release]: https://github.com/vladdoster/py-chrome-exporter/releases/latest

## Usage

These scripts require Python 3.2 or later. They should work on Linux, macOS, and Windows.

### Bookmarks script

The usage is

    py-chrome-exporter bookmarks [input_file] output_file

If you do not specify an input file, the script will try to open the default Chrome bookmarks file.

The script will ignore URLs that start with “javascript:”.

### History script

The usage is

    py-chrome-exporter history [input_file] output_file

If you do not specify an input file, the script will try to open the default Chrome history file.

The script will ignore history entries with empty titles.

## Notes for developers

To test changes to the scripts, run `bash test/run_tests`. This script runs both programs and verifies that their output is identical to what is expected. If you have already installed the programs somewhere and want to test those copies, run `bash test/run_tests /path/to/bin`, where `/path/to/bin` is the directory where `py-chrome-exporter` is located.

The man pages are written in Markdown; run `make man` to use Pandoc to convert them into the man format. The generated versions are checked into Git so that users don’t have to install Pandoc.

## Version history
* 2.0.3 (2020-07-02)
    - Dropped Python 2 support due to it reaching EOL. 
    - Condensed {bookmark,history}-export into single cli tool.
    - Added -d/--debug flags
    - Changed print statements to use logging module.
    - Changed name from `chrome-export` to `py-chrome-exporter`
* 2.0.2 (2019-06-15)
    - Added man pages and made the testing script more flexible. No changes to functionality.
* 2.0.1 (2018-02-09)
    - Fixed an error that occurred when trying to open the default bookmarks file under Python 2.7. (Thanks [Hridoy Sankar Dutta](https://github.com/hridaydutta123)!)
* 2.0 (2018-02-05)
    - Renamed the project from “py-chrome-bookmarks” to “chrome-export”; renamed “py-chrome-bookmarks.py” to “export-chrome-bookmarks”; and renamed “py-chrome-history.py” to “export-chrome-history”. There were no changes in functionality.
* 1.2.1 (2017-06-02)
    - Fixed a Unicode decoding error under Windows 7. (Thanks [Boburmirzo Hamraqulov](https://github.com/bzimor)!)
* 1.2 (2017-01-26)
    - Added support for Python 3, dropped support for Python 2.6 and earlier, and made this all clear in the readme.
    - Giving an input filename is now optional for both scripts. If you omit the input filename then the scripts will try to open Chrome’s bookmarks or history file automatically.
    - The history script now makes a copy of the input file before opening it. Previously, it was necessary either to make a copy yourself or to quit Chrome before running the script. (The history file is a SQLite database and it isn’t possible for two programs to have it open at the same time.)
* 1.1 (2011-04-06)
    - Added help and version text (and started counting versions).
    - Added some checking for errors while opening the input or output files.
* 1.0
    - Initial release

## Author

The inital programs were created by [Benjamin Esham](https://esham.io).

Extended functionality by [Vlad Doster](http://vdoster.com)

This project is [hosted on GitHub](https://github.com/vladdoster/py-chrome-export). Please feel free to submit pull requests.

## License

Copyright © 2020 Vlad Doster. This program is released under the ISC license, which you can find in the file LICENSE.md.
