# Apple T1 support
This fork for supports Apple T1 chip present in A1707. Requires appletbdrm installed from [here](https://github.com/sunplex07/appletbdrm.git)
It contains breaking changes for T2 (messed up T2 udev rules that I was too lazy to fix).

# Install
1. run install.sh from appletbdrm.
2. build with 

    `cargo build --release`
3. copy over the executable 

    `sudo install -Dm755 target/release/tiny-dfr /usr/bin/tiny-dfr`
4. copy over udev rules and systemd services 

    `/bin/cp -r etc/* /etc/`
5. copy over all the button graphics 

    `sudo cp -r share/* /usr/share/`
6. reload rules and services

    `sudo udevadm control --reload-rules && sudo udevadm trigger && sudo systemctl daemon-reload && sudo systemctl restart tiny-dfr.service`

Touchbar should work now (tested on Arch kernel 6.19.12).

# tiny-dfr
The most basic dynamic function row daemon possible


## Dependencies
cairo, libinput, freetype, fontconfig, librsvg 2.59 or later, uinput enabled in kernel config

## License

tiny-dfr is licensed under the MIT license, as included in the [LICENSE](LICENSE) file.

* Copyright The Asahi Linux Contributors

Please see the Git history for authorship information.

tiny-dfr embeds Google's [material-design-icons](https://github.com/google/material-design-icons)
which are licensed under [Apache License Version 2.0](LICENSE.material)
Some icons are derivatives of material-icons, with edits made by kekrby.
