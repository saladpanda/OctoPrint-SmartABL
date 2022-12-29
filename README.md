# SmartABL

Simple plugin to improve auto bed leveling, adding some conditions
in order to minimize the number of ABLs triggered.

## How it works?

The plugin replaces `G29` from ***.gcode** and check the bed mesh
in memory.
- If mesh is updated, `M429 S1` is sent in order to load bed mesh from memory.
- If mesh is outdated or doesn't exist, `G29` and `M500` are sent in order to
generate a new mesh and save it to eeprom, respectively.

References:
- [G29](https://marlinfw.org/docs/gcode/G029.html)
- [M420](https://marlinfw.org/docs/gcode/M420.html)
- [M500](https://marlinfw.org/docs/gcode/M500.html)

Credits to [Oscar](https://3dprinting.stackexchange.com/a/15953/27154)
for the idea.

## Setup

Install via the bundled [Plugin Manager](https://docs.octoprint.org/en/master/bundledplugins/pluginmanager.html)
or manually using this URL:

    https://github.com/scmanjarrez/OctoPrint-SmartABL/archive/master.zip

## Configuration

By default, SmartABL **does not change** the behaviour of the
auto bed leveling. User *must* change default values in settings:

**Days**
- **force** (disabled): Force bed mesh update if the `after days`
condition is met.
- **after**(1): Days after last print before forcing mesh update.

**Prints**
- **force** (disabled): Force bed mesh update if the `after prints` condition is met.
- **after**(5): Prints completed before forcing mesh update.

**Events**
- **failed** (disabled): Take into account `PrintFailed` events
in the `prints` counter. Otherwise, only `PrintDone` (successful prints)
are taken into account.

<div align="center">
    <img alt="Screenshot of SmartABL settings panel" src="plugins.octoprint.org/assets/img/plugins/SmartABL/settings.png" width="90%"></img>
</div>

## Support me
You find this plugin helpful and want to support me?

<a href="https://ko-fi.com/Zuzumebachi">
    <img alt="Ko-fi link to support me" src="plugins.octoprint.org/assets/img/plugins/SmartABL/kofi_button_red.png" width="25%"></img>
</a>

## License

    SmartABL  Copyright (C) 2022 scmanjarrez.
    This program comes with ABSOLUTELY NO WARRANTY; for details check below.
    This is free software, and you are welcome to redistribute it
    under certain conditions; check below for details.

[LICENSE](LICENSE)
