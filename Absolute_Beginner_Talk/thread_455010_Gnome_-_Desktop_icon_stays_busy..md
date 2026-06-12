---
title: "Gnome - Desktop icon stays busy."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Dcox on 2007-05-26
Hi guys,

when I'm on my desktop and have nothing selected, the icon stays 'busy' like in windows the hourglass. It keeps on going and does not stop... I have no clue what's going on. So i do not have a "pointer" but a circle which states something is going on...

Here the PS aux : 

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.2  0.1   2912  1848 ?        Ss   10:04   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    10:04   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   10:04   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    10:04   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   10:04   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   10:04   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   10:04   0:00 [kthread]
root        30  0.0  0.0      0     0 ?        S<   10:04   0:00 [kblockd/0]
root        31  0.0  0.0      0     0 ?        S<   10:04   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   10:04   0:00 [kacpi_notify]
root       146  0.0  0.0      0     0 ?        S<   10:04   0:00 [kseriod]
root       171  0.0  0.0      0     0 ?        S    10:04   0:00 [pdflush]
root       172  0.0  0.0      0     0 ?        S    10:04   0:00 [pdflush]
root       173  0.0  0.0      0     0 ?        S<   10:04   0:00 [kswapd0]
root       174  0.0  0.0      0     0 ?        S<   10:04   0:00 [aio/0]
root      1979  0.0  0.0      0     0 ?        S<   10:04   0:00 [ksuspend_usbd]
root      1980  0.0  0.0      0     0 ?        S<   10:04   0:00 [khubd]
root      2011  0.0  0.0      0     0 ?        S<   10:04   0:00 [ata/0]
root      2012  0.0  0.0      0     0 ?        S<   10:04   0:00 [ata_aux]
root      2015  0.0  0.0      0     0 ?        S<   10:04   0:00 [khpsbpkt]
root      2121  0.0  0.0      0     0 ?        S<   10:04   0:00 [knodemgrd_0]
root      2309  0.0  0.0      0     0 ?        S<   10:04   0:00 [scsi_eh_0]
root      2310  0.0  0.0      0     0 ?        S<   10:04   0:00 [usb-storage]
root      2384  0.0  0.0      0     0 ?        S<   10:04   0:00 [kjournald]
root      2584  0.0  0.1   2888  1236 ?        S<s  10:05   0:00 /sbin/udevd --daemon
root      4001  0.0  0.0      0     0 ?        S<   10:05   0:00 [kjournald]
root      4297  0.0  0.0   1652   508 tty4     Ss+  10:05   0:00 /sbin/getty 38400 tty4
root      4298  0.0  0.0   1648   508 tty5     Ss+  10:05   0:00 /sbin/getty 38400 tty5
root      4301  0.0  0.0   1652   508 tty2     Ss+  10:05   0:00 /sbin/getty 38400 tty2
root      4303  0.0  0.0   1648   504 tty3     Ss+  10:05   0:00 /sbin/getty 38400 tty3
root      4304  0.0  0.0   1652   512 tty1     Ss+  10:05   0:00 /sbin/getty 38400 tty1
root      4305  0.0  0.0   1648   508 tty6     Ss+  10:05   0:00 /sbin/getty 38400 tty6
root      4543  0.0  0.1   2256  1164 ?        Ss   10:05   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4645  0.0  0.0   1704   652 ?        Ss   10:05   0:00 /sbin/syslogd
root      4702  0.0  0.0   1788   520 ?        Ss   10:05   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4704  0.0  0.1   2428  1372 ?        Ss   10:05   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4725  0.0  0.1   2852  1064 ?        Ss   10:05   0:00 /usr/bin/dbus-daemon --system
107       4741  0.6  0.8  10568  8892 ?        Ss   10:05   0:02 /usr/sbin/hald
root      4742  0.0  0.1   2872  1036 ?        S    10:05   0:00 hald-runner
107       4748  0.0  0.0   2092   880 ?        S    10:05   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4756  0.0  0.0   2092   896 ?        S    10:05   0:00 hald-addon-keyboard: listening on /dev/input/event1
107       4765  0.0  0.0   2096   896 ?        S    10:05   0:00 hald-addon-keyboard: listening on /dev/input/event4
107       4768  0.0  0.0   2092   892 ?        S    10:05   0:00 hald-addon-keyboard: listening on /dev/input/event5
107       4781  0.0  0.0   2092   904 ?        S    10:05   0:00 hald-addon-storage: polling /dev/hdb
107       4783  0.0  0.0   2092   904 ?        S    10:05   0:00 hald-addon-storage: polling /dev/sda
107       4785  0.0  0.0   2092   904 ?        S    10:05   0:00 hald-addon-storage: polling /dev/sdb
107       4787  0.0  0.0   2092   904 ?        S    10:05   0:00 hald-addon-storage: polling /dev/sdc
107       4789  0.0  0.0   2096   904 ?        S    10:05   0:00 hald-addon-storage: polling /dev/sdd
root      4802  0.0  0.0   1936   840 ?        Ss   10:05   0:00 /usr/sbin/dhcdbd --system
root      4817  0.0  0.1  12320  1932 ?        Ssl  10:05   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
avahi     4835  0.0  0.1   2664  1364 ?        Ss   10:05   0:00 avahi-daemon: registering [Ubuntu.local]
avahi     4836  0.0  0.0   2664   460 ?        Ss   10:05   0:00 avahi-daemon: chroot helper
root      4849  0.0  0.1   3052  1260 ?        Ss   10:05   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4865  0.0  0.0   2868   804 ?        Ss   10:05   0:00 /usr/bin/system-tools-backends
root      4866  0.0  0.1   2716  1216 ?        S    10:05   0:00 dbus-daemon --session --print-address --nofork
root      4898  0.0  0.1  12216  1408 ?        Ss   10:05   0:00 /usr/sbin/gdm
root      4901  0.0  0.2  12576  2396 ?        S    10:05   0:00 /usr/sbin/gdm
root      4904 11.1  4.1  54744 42544 tty7     Ss+  10:05   0:45 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
cupsys    4973  0.0  0.1   4684  1968 ?        Ss   10:05   0:00 /usr/sbin/cupsd
dhcp      4974  0.0  0.1   2452  1208 ?        S    10:05   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
root      5003  0.0  0.0   6412   832 ?        Ss   10:05   0:00 /usr/sbin/hpiod
hplip     5006  0.0  0.4   9984  4896 ?        S    10:05   0:00 python /usr/sbin/hpssd
daemon    5178  0.0  0.0   1904   416 ?        Ss   10:05   0:00 /usr/sbin/atd
root      5192  0.0  0.0   2280   892 ?        Ss   10:05   0:00 /usr/sbin/cron
dieter    5336  0.0  1.0  30224 11232 ?        Ssl  10:05   0:00 /usr/bin/gnome-session
dieter    5377  0.0  0.0   4248   524 ?        Ss   10:05   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dieter    5380  0.0  0.0   2660   632 ?        S    10:05   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dieter    5381  0.0  0.0   2848  1012 ?        Ss   10:05   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
dieter    5383  0.1  0.4   6732  4232 ?        S    10:05   0:00 /usr/lib/libgconf2-4/gconfd-2 6
dieter    5386  0.0  0.0   2748   992 ?        S    10:05   0:00 /usr/bin/gnome-keyring-daemon
dieter    5388  0.0  0.9  29504 10000 ?        Sl   10:05   0:00 /usr/lib/control-center/gnome-settings-daemon
dieter    5395  0.0  0.0   1712   480 ?        Ss   10:05   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dieter    5396  0.0  0.3   4960  3324 ?        S    10:05   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dieter    5401  0.0  0.3  39632  3108 ?        Ssl  10:05   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=21
dieter    5406  0.3  0.5  15652  5368 ?        S    10:05   0:01 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17
dieter    5407  0.0  0.0   1712   492 ?        S    10:05   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0 gconf
dieter    5410  0.2  1.8  60220 19280 ?        S    10:05   0:00 gnome-panel --sm-client-id default1
dieter    5413  0.1  1.7  75656 17828 ?        R    10:05   0:00 nautilus --no-default-window --sm-client-id default2
dieter    5416  0.1  0.9  17348  9352 ?        S    10:05   0:00 gtk-window-decorator
dieter    5421  0.2  0.7  18052  7944 ?        S    10:05   0:00 /usr/bin/compiz.real --no-fbo --ignore-desktop-hints --sm-client-id default0 gconf gconf
dieter    5422  0.0  0.4  18812  4760 ?        Ss   10:05   0:00 gnome-volume-manager --sm-client-id default4
dieter    5424  0.0  0.3   8456  3360 ?        S    10:05   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
dieter    5428  0.2  2.0  75556 20880 ?        Sl   10:05   0:01 gaim
dieter    5432  0.0  1.1  48508 11932 ?        S    10:05   0:00 update-notifier
dieter    5435  0.0  0.8  78912  8928 ?        S    10:05   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=23
dieter    5447  0.0  0.9  67896  9972 ?        Sl   10:05   0:00 /usr/lib/evolution/2.10/evolution-alarm-notify
dieter    5450  0.0  0.0   2456   884 ?        S    10:05   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
dieter    5455  0.0  0.7  19072  7724 ?        S    10:05   0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=24
dieter    5456  0.0  1.2  48160 12544 ?        S    10:05   0:00 nm-applet --sm-disable
dieter    5458  0.0  0.5  45968  5748 ?        Ss   10:05   0:00 gnome-power-manager
dieter    5459  0.0  0.7  39932  8132 ?        S    10:05   0:00 gnome-cups-icon --sm-client-id default3
dieter    5469  0.0  0.6  65596  6476 ?        Sl   10:05   0:00 /usr/lib/evolution/evolution-data-server-1.10 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=31
dieter    5471  0.0  1.1  49664 12384 ?        S    10:05   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=37
dieter    5479  0.0  0.9  36408  9380 ?        Sl   10:05   0:00 /usr/lib/evolution/2.10/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=32
dieter    5545  0.1  0.2  15896  2244 ?        Ss   10:05   0:00 gnome-screensaver
dieter    5675  5.8  4.6 175864 48008 ?        Sl   10:09   0:08 /usr/lib/firefox/firefox-bin file:///tmp/gaimST7z5S -a firefox
dieter    5745  2.0  1.6  72216 16580 ?        Sl   10:11   0:00 gnome-terminal
dieter    5750  0.0  0.0   2460   728 ?        S    10:11   0:00 gnome-pty-helper
dieter    5751  0.6  0.3   5896  3416 pts/0    Ss   10:11   0:00 bash
dieter    5780  0.0  0.0   2564   996 pts/0    R+   10:12   0:00 ps aux
```

Coud anyone please help me out ? It's really bugging me.

---

### Post by Dcox on 2007-05-27
When I add a new user, the user does not have the issue. So must be user-related.
Also tried removing .gnome, .gnome2, .gconf and .gconfd and relogon. Did not solve this.

Screensaver also doen't start anymore.

Can I delete my user and start over without losing my /home/user dir ?

---

