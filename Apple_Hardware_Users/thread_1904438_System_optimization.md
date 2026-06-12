---
title: "System optimization"
date: 2012-01-04
forum: Apple Hardware Users
---

### Post by DARKAD on 2012-01-04
I just wondering if my system configuration is right optimized just for music production:

Ubuntustudio 64bit 11.10 on a macbook 4.1

My first doubt is about the number of processes that I see after system startup:

```

init-+-NetworkManager-+-dhclient
     |                `-2*[{NetworkManager}]
     |-accounts-daemon---{accounts-daemo}
     |-acpid
     |-applet.py
     |-atd
     |-avahi-daemon---avahi-daemon
     |-colord---2*[{colord}]
     |-console-kit-dae---64*[{console-kit-da}]
     |-cron
     |-cupsd
     |-2*[dbus-daemon]
     |-dbus-launch
     |-dconf-service---2*[{dconf-*********]
     |-freshclam
     |-gconfd-2
     |-6*[getty]
     |-gnome-keyring-d---4*[{gnome-keyring-}]
     |-gnome-keyring-d
     |-gvfs-afc-volume---{gvfs-afc-volum}
     |-gvfs-fuse-daemo---3*[{gvfs-fuse-daem}]
     |-gvfs-gdu-volume
     |-gvfs-gphoto2-vo
     |-gvfsd
     |-gvfsd-burn
     |-gvfsd-dnssd
     |-gvfsd-metadata
     |-gvfsd-network---2*[{gvfsd-network}]
     |-gvfsd-smb-brows---2*[{gvfsd-smb-brow}]
     |-gvfsd-trash
     |-irqbalance
     |-lightdm-+-Xorg
     |         |-sh-+-ssh-agent
     |         |    |-xfce4-session-+-Thunar
     |         |    |               |-xfce4-panel-+-panel-6-systray
     |         |    |               |             |-xfce4-mixer-plu---4*[{xfce4-mixer-pl}]
     |         |    |               |             |-xfce4-oragecloc
     |         |    |               |             |-xfce4-places-pl
     |         |    |               |             `-{xfce4-panel}
     |         |    |               |-xfdesktop
     |         |    |               |-xfwm4
     |         |    |               `-{xfce4-session}
     |         |    `-xscreensaver
     |         `-2*[{lightdm}]
     |-modem-manager
     |-nautilus---2*[{nautilus}]
     |-nm-applet---{nm-applet}
     |-polkit-gnome-au---{polkit-gnome-a}
     |-polkitd---{polkitd}
     |-pommed---{pommed}
     |-pulseaudio-+-gconf-helper
     |            `-2*[{pulseaudio}]
     |-rsyslogd---3*[{rsyslogd}]
     |-rtkit-daemon---2*[{rtkit-daemon}]
     |-tumblerd---2*[{tumblerd}]
     |-udevd---2*[udevd]
     |-udisks-daemon-+-udisks-daemon
     |               `-2*[{udisks-daemon}]
     |-update-notifier---2*[{update-notifie}]
     |-upowerd---2*[{upowerd}]
     |-upstart-socket-
     |-upstart-udev-br
     |-winbindd---winbindd
     |-wpa_supplicant
     |-xfce4-notifyd
     |-xfce4-power-man---{xfce4-power-ma}
     |-xfce4-settings-
     |-xfce4-terminal-+-bash---pstree
     |                |-xfce4-terminal
     |                `-{xfce4-terminal}
     |-xfce4-volumed---5*[{xfce4-volumed}]
     |-xfconfd
     `-xfsettingsd

```

for example
I know I'll never use the bluetooth service to do music, so I disabled it permanently and the daemon is no more in this list.
Would you suggest me other things to do?

---

