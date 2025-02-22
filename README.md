# mdcat

Fancy `cat` for Markdown (that is, [CommonMark][]):

```
$ mdcat sample.md
```

![mdcat showcase with different colour themes][sxs]

mdcat in [kitty], with Tango Light, [Solarized] Light, and [Dracula] (from left to
right), and [PragmataPro] as font.

[CommonMark]: http://commonmark.org
[Solarized]: http://ethanschoonover.com/solarized
[dracula]: https://draculatheme.com/iterm/
[kitty]: https://sw.kovidgoyal.net/kitty/index.html
[PragmataPro]: https://www.fsd.it/shop/fonts/pragmatapro/
[sxs]: ./screenshots/side-by-side.png

## Features

`mdcat` works best with [iTerm2] or [Kitty], and a good terminal font with italic characters.
Then it

* nicely renders all basic CommonMark syntax (no [tables][#2] or [footnotes][#1] though),
* highlights code blocks with [syntect],
* shows [links][osc8], and also images inline in supported terminals (see above, where "Rust" is a clickable link!),
* adds jump marks for headings in [iTerm2] (jump forwards and backwards with <key>⇧⌘↓</key> and <key>⇧⌘↑</key>).

| Terminal                   |  Basic syntax | Syntax highlighting | Images | Jump marks |
| :------------------------- | :-----------: | :-----------------: | :----: | :--------: |
| Basic ANSI                 | ✓             | ✓                   |        |            |
| Windows [ConEmu][]         | ✓             | ✓                   |        |            |
| Windows 10 console         | ✓             | ✓                   |        |            |
| Generic VTE 0.50 or newer¹ | ✓             | ✓                   |        |            |
| [Terminology][]            | ✓             | ✓                   | ✓      |            |
| [iTerm2][]                 | ✓             | ✓                   | ✓ 2)   | ✓          |
| [kitty][]                  | ✓             | ✓                   | ✓ 2)   |            |
| [WezTerm][]                | ✓             | ✓                   | ✓ 2)   |            |
| [foot][]                   | ✓             | ✓                   |        |            |

1) VTE is Gnome’s terminal emulation library used by many popular terminal emulators on Linux, including Gnome Terminal, Xfce Terminal, Tilix, etc.
2) SVG images require `rsvg-convert` from librsvg.

Not supported:

* CommonMark extensions: [Footnotes][#1] and [tables][#2]
* [Re-filling paragraphs][#4]

[syntect]: https://github.com/trishume/syntect
[osc8]: https://gist.github.com/egmontkob/eb114294efbcd5adb1944c9f3cb5feda
[Terminology]: http://terminolo.gy
[ConEmu]: https://conemu.github.io
[iterm2]: https://www.iterm2.com
[WezTerm]: https://wezfurlong.org/wezterm/
[foot]: https://codeberg.org/dnkl/foot/

## Usage

Try `mdcat --help` or read the [mdcat(1)](./mdcat.1.adoc) manpage.

## Installation

* 3rd party packages:
    * [Homebrew]: `brew install mdcat`
    * [MacPorts]: `sudo port install mdcat`
    * [Arch Linux]: `pacman -S mdcat`
    * Void Linux: `xbps-install -S mdcat`
    * Nixpkgs: `nix-env -i mdcat`
    * [Scoop]: `scoop install mdcat`
    * [Chocolatey]: `choco install mdcat`
* You can also build `mdcat` manually with `cargo install mdcat`.

## Requirements

For image type detection either the `file` tool with support for `--brief` and `--mime-type` flags must be available in `$PATH`.

[Homebrew]: https://brew.sh
[MacPorts]: https://www.macports.org
[Arch Linux]: https://www.archlinux.org/packages/community/x86_64/mdcat/
[scoop]: https://github.com/lukesampson/scoop
[chocolatey]: https://github.com/chocolatey

## Troubleshooting

`mdcat` can output extensive tracing information when asked to.
Run a **debug build** of `mdcat` with `$MDCAT_LOG=trace` for complete tracing information, or with `$MDCAT_LOG=mdcat::render=trace` to trace only rendering.

**Note:** Tracing information is mostly elided in release builds; use a debug build for complete output.

## Future plans

- [ ] Figure out a better way to show HTML [#3].
- [ ] CommonMark extensions: Footnotes [#1].
- [ ] CommonMark extensions: Tables [#2].
- [ ] Ignore soft wraps and wrap inline text a column limit instead [#4].

[#1]: https://github.com/swsnr/mdcat/issues/1
[#2]: https://github.com/swsnr/mdcat/issues/2
[#3]: https://github.com/swsnr/mdcat/issues/3
[#4]: https://github.com/swsnr/mdcat/issues/4

## License

Copyright Sebastian Wiesner <sebastian@swsnr.de>

Binaries are subject to the terms of the Mozilla Public
License, v. 2.0, see [LICENSE](LICENSE).

Most of the source is subject to the terms of the Mozilla Public
License, v. 2.0, see [LICENSE](LICENSE), unless otherwise noted;
some files are subject to the terms of the Apache 2.0 license,
see <http://www.apache.org/licenses/LICENSE-2.0>
