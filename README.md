# Waybar Nordvpn script

Simple daemon and cli wrapper for for [NordVPN](https://nordvpn.com/) to be
used in [Waybar](https://github.com/Alexays/Waybar) or any similar system bar.

## Usage

### nvpn

```sh
nvpn
# or
nvpn <options for nordvpn>
```

In case the script is called _without_ arguments, the connection will be toggled
by calling `nordvpn connect` or `nordvpn disconnect`.

In case the script is called _with_ arguments, all of those will be passed through to `nordvpn`, also
triggering the update in the system bar module.

### nvpnd

```sh
nvpnd
```

The `nvpn` script should be symlinked to `nvpnd` to function as a daemon. It
will output a status message upon receiving `SIGUSR1`, which is automatically
handled by `nvpn`.

## Configuration

For Waybar:
```json
{
    "custom/nordvpn": {
        "exec": "/path/to/nvpnd",
        "exec-on-event": false,
        "on-click": "/path/to/nvpn"
    }
}
```

You can also use other names for the script, but then the variables `NVPN_CLI`
and `NVPN_DAEMON` should be modified in the script.

## Dependencies
 - [nordvpn cli client](https://nordvpn.com/download/linux/)
 - awk, find (usually on your computer already)
