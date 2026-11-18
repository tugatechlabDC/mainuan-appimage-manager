<div align="center">

<img src="assets/icons/128x128/org.mainuan.appimagemanager.png" width="96" alt="Ícone do Mainuan AppImage Manager">

# Mainuan AppImage Manager

[![License: GPL-3.0+](https://img.shields.io/badge/License-GPL--3.0%2B-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Version](https://img.shields.io/badge/version-1.0.3-green.svg)]()

AppImage integration manager for Mainuan Linux.

</div>

## Description

Mainuan AppImage Manager lets you easily integrate AppImage applications into your Mainuan Linux desktop. Select any AppImage file, and the manager moves it to `~/AppImages/`, extracts its icon and metadata, and creates a `.desktop` entry so the app appears in your application menu — no manual steps needed.

## Screenshots

<div align="center">
  <img src="assets/screenshots/screenshot1.png" width="80%" alt="Mainuan AppImage Manager"/>
</div>

## Features

- **Add AppImages**: File chooser or drag & drop → moved to `~/AppImages/` automatically, with the option to copy instead of move and keep the original file
- **Metadata extraction**: icon, name, version and description extracted from the AppImage itself
- **Icon storage**: icons saved persistently to `~/AppImages/.icons/`
- **Desktop integration**: `.desktop` file created in `~/.local/share/applications/`
- **Type detection**: Supports AppImage Type 1 (ISO9660) and Type 2 (SquashFS)
- **Universal detection**: recognises AppImages installed by any source (Mainuan Welcome, manual placement, etc.)
- **Integrate**: one-click integration for AppImages already in `~/AppImages/`
- **Auto-refresh**: file monitor watches `~/AppImages/` and `~/.local/share/applications/` — no manual refresh needed
- **Run**: launch any managed AppImage from the manager
- **Delete**: remove the AppImage, icon and desktop entry in one click
- **Properties**: edit name, version, description, categories and update URL for each AppImage
- **Run as root**: mark any AppImage to launch with `pkexec` — PolicyKit authentication dialog appears on launch
- **Automatic updates**: checks GitHub, GitLab and Codeberg release APIs, direct URL comparison, or embedded `appimageupdatetool` info
- **Check All Updates**: inspect all AppImages with a configured update source in one click; update them all from the same dialog
- **Internationalisation**: ships with 9 languages (pt-PT, pt-BR, de, en, es, fr, it, ro, ru)
- **Mainuan UI**: consistent dark theme matching the Mainuan Linux ecosystem

## Requirements

- Python 3.10+
- GTK+ 3
- python3-gi
- `p7zip-full` (recommended, for faster metadata extraction)

## Installation

The Mainuan AppImage Manager is already installed on the Mainuan Linux ISO or available on the Mainuan Store.

On another Kubuntu/Ubuntu 26.04 system, download the `.deb` and the `SHA256SUMS` from
[latest release](https://github.com/mainuan/mainuan-appimage-manager/releases/latest),
check and install:

```bash
sha256sum --check --ignore-missing SHA256SUMS
sudo apt install ./mainuan-appimage-manager_1.0.3.deb

```bash
git clone https://github.com/mainuan/mainuan-appimage-manager.git
cd mainuan-appimage-manager
python3 main.py
```
## Usage

Open **Mainuan AppImage Manager** from your application menu (under the System/Settings category) or run:

```bash
mainuan-appimage-manager
```

The program has no command-line options; everything is handled via the interface
(`man mainuan-appimage-manager`). The administrator password is requested via `pkexec`.

## Structure

```
mainuan-appimage-manager/
├── assets/           # Icons, themes and desktop file
├── config/           # Constants
├── core/             # AppImage logic (integration, extraction, management)
├── debian/           # Deb packaging data
├── ui/               # GTK3 interface
└── utils/            # Environment detection
```

## How it works

1. User selects an `.AppImage` file via the file chooser
2. The file is moved to `~/AppImages/`
3. Metadata is extracted using `7zz` or `--appimage-extract`
4. The icon is saved to `~/AppImages/.icons/`
5. A `.desktop` file is written to `~/.local/share/applications/`
6. The app appears in the application menu immediately

## 🆕 New in version 1.0.3 (November 17, 2026)

## Contributing

Report issues in [Issues](https://github.com/mainuan/mainuan-appimage-manager/issues)
and submit changes via pull request to the `main` branch. Every PR must pass the
[CI](https://github.com/mainuan/mainuan-appimage-manager/actions/workflows/ci.yml)
checks, which must all be green (passing). Document any visible changes in
[CHANGELOG.md](CHANGELOG.md) and `debian/changelog`.

## Créditos

- David Caixinha ([@tugatechlabDC](https://github.com/tugatechlabDC)): developer and maintainer of the package (`debian/control`).


This project is licensed under the GPL-3.0 License — see the `debian/copyright` file for details.
