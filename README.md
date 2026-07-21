# Quick Terminal 2.5.0

Quick Terminal is a compact pure Python application built with GTK4, PyGObject, and the GTK4 VTE 3.91 widget. It modernizes the earlier GTK3 version.

**Author:** JJ Posti — [techtimejourney.net](https://www.techtimejourney.net)  
**License:** GPL-2.0-or-later  
**Installed command:** `terminal`

<img width="776" height="428" alt="Image" src="https://github.com/user-attachments/assets/699dd70e-5a72-454c-aa4b-95dd4b327b49" />

Theme example, these can be changed during runtime. See more from screenshots folder.

## Features

- Native GTK4 application and window lifecycle
- Movable, scrollable VTE terminal tabs
- Double-click an existing tab title to open a new tab in the same directory
- Asynchronous, cancellable shell startup
- New tabs inherit the current terminal directory
- `/bin/bash` as the default shell, with `$SHELL` and `/bin/sh` fallbacks
- GTK4 actions, menus, dialogs, clipboard support, and file drops
- LWM Graphite, LWM Dark, and LWM Blue themes
- Bounded 1,024-line scrollback buffer per tab
- Signal-safe tab removal through the GTK idle loop
- Bytecode-free source archives and Debian package payload
- Desktop entry, AppStream metadata, icon, manual page, tests, and Debian packaging

## Quick start

### 1. Install runtime dependencies

Quick Terminal requires Python 3.11 or newer, GTK 4.10 or newer, and VTE 0.76 or newer through the `Vte 3.91` introspection namespace.

#### Debian 13 (Trixie)

```bash
sudo apt update
sudo apt install bash python3 python3-gi gir1.2-gtk-4.0 gir1.2-vte-3.91
```

#### Arch Linux

```bash
sudo pacman -S --needed bash python python-gobject gtk4 vte4
```

#### Fedora

```bash
sudo dnf install bash python3 python3-gobject gtk4 vte291-gtk4
```

### 2. Extract and run from source

```bash
tar -xzf quick-terminal.tar.gz
cd quick-terminal-2.5.0
./bin/terminal
```

You can also run:

```bash
python3 ./bin/terminal
```

To extract, enter the project directory, and run the full Debian build in one command:

```bash
tar -xzf ./quick-terminal.tar.gz && cd quick-terminal-2.5.0 && make all
```

### 3. View help or version information

```bash
./bin/terminal --help
./bin/terminal --version
```

## Themes

Available themes:

- **LWM Graphite** — graphite surfaces with restrained steel accents
- **LWM Dark** — near-black surfaces with the LWM blue accent
- **LWM Blue** — deep-blue surfaces with white interface and terminal text


Settings are at:

```text
~/.config/quick-terminal/settings.json
```

## Keyboard shortcuts

| Action | Shortcut |
| --- | --- |
| New tab | `Ctrl+Shift+T` |
| Close tab | `Ctrl+Shift+W` |
| Copy | `Ctrl+Shift+C` |
| Paste | `Ctrl+Shift+V` |
| Select all | `Ctrl+Shift+A` |
| Quit | `Ctrl+Q` |

Double-click a tab title to open a new tab in that tab’s current directory. Right-click inside a terminal to access copy, paste, selection, and tab actions.

## Building a Debian package

Install the build dependencies on Debian 13:

```bash
sudo apt update
sudo apt install build-essential debhelper python3
```

From the project root, run either:

```bash
make all
```

or:

```bash
dpkg-buildpackage -us -uc -b
```

Install the generated package:

```bash
sudo apt install ../quick-terminal_2.5.0-1_all.deb
```

The package installs the `terminal` command at `/usr/bin/terminal` and stores application modules under `/usr/lib/quick-terminal`. Runtime dependencies are declared in `debian/control`.

Quick Terminal does not use `dh-python` or install itself into `dist-packages`, which prevents automatic compilation of project bytecode.

## Make targets

```text
make all             Run the complete build workflow
make run             Run the application from the source tree - make all omits this
make check           Run syntax, metadata, test, mode, and bytecode checks
make tests           Run dependency-free unit tests
make gui-check       Run the GTK4/VTE import and Xvfb tab-interaction probe
make deb             Build the Debian package with dpkg-buildpackage
make bytecode-check  Audit the project for Python bytecode
make bytecode-clean  Remove project bytecode
make clean           Remove generated build, package, and cache files
```

## Why the source is distributed as a tar.gz archive

The project is wrapped in a `tar.gz` archive so that downloading the repository as a ZIP does not alter or corrupt files used by the Python test suite. Extract the archive before running, testing, or building the project.

## License

Copyright © 2017–2026 JJ Posti, techtimejourney.net.

Quick Terminal is free software. You may redistribute it and modify it under the terms of the GNU General Public License, version 2 or, at your option, any later version.

The complete GPL version 2 text is available in `COPYING`. See `Copyright` and `debian/copyright` for the project notice and Debian package metadata.
