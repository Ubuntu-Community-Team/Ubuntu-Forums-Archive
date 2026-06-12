---
title: "Cant install anything (11 resource error)"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by tast01 on 2007-10-29
Im trying to install bluefish, after typing:* sudo apt-get install bluefish*  I get this error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gnome-bin weblint-perl weblint php4-cli php5-cli tidy
The following NEW packages will be installed:
  bluefish
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

no matter what i try to install i get that message :/

---

### Post by taurus on 2007-10-29
Do you by any chance have synaptic or adept open?

---

### Post by tast01 on 2007-10-29
no (well no gui window as far as i can see)

---

### Post by taurus on 2007-10-29
What's the output of this command?

```
ls -la /var/cache/apt/archives/lock
```

---

### Post by tast01 on 2007-10-29
```
-rw-r----- 1 root root 0 2007-10-29 20:22 /var/cache/apt/archives/lock
```

---

### Post by taurus on 2007-10-29
Do you still get the same error message when you run these two commands?

```
sudo apt-get update
sudo apt-get install bluefish
```

If you do, then post the output of this command.

```
ps -A
```

---

### Post by tast01 on 2007-10-29
I do get the same output

output of ps -A
```
 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kacpid
   34 ?        00:00:00 kacpi_notify
  129 ?        00:00:00 kseriod
  150 ?        00:00:05 kswapd0
  201 ?        00:00:00 aio/0
  202 ?        00:00:00 aio/1
 1991 ?        00:00:00 ksuspend_usbd
 1992 ?        00:00:00 khubd
 2101 ?        00:00:00 ata/0
 2102 ?        00:00:00 ata/1
 2103 ?        00:00:00 ata_aux
 2121 ?        00:00:00 khpsbpkt
 2189 ?        00:00:00 scsi_eh_0
 2190 ?        00:00:06 scsi_eh_1
 2248 ?        00:00:00 scsi_eh_2
 2249 ?        00:00:00 scsi_eh_3
 2271 ?        00:00:00 scsi_eh_4
 2272 ?        00:00:00 usb-storage
 2310 ?        00:00:00 knodemgrd_0
 2511 ?        00:00:10 kjournald
 2717 ?        00:00:00 udevd
 3003 ?        00:00:00 miniserv.pl
 3020 ?        00:00:00 miniserv.pl
 3103 ?        00:00:00 sh
 3104 ?        00:00:00 yes
 3105 ?        00:00:01 apt-get
 3129 ?        00:00:00 dpkg <defunct>
 3512 tty7     00:02:45 Xorg
 3537 ?        00:00:00 gnome-keyring-d
 3540 ?        00:00:00 x-session-manag
 3575 ?        00:00:00 ssh-agent
 3577 ?        00:00:00 gconfd-2
 3581 ?        00:00:00 dbus-daemon
 3583 ?        00:00:01 gnome-settings-
 3589 ?        00:00:00 compiz
 3591 ?        00:00:16 gnome-panel
 3593 ?        00:00:21 nautilus
 3598 ?        00:00:00 gnome-vfs-daemo
 3599 ?        00:00:00 gnome-volume-ma
 3601 ?        00:00:00 bonobo-activati
 3623 ?        00:00:13 gnome-screensav
 3696 ?        00:00:10 gtk-window-deco
 3697 ?        00:00:34 compiz.real
 3709 ?        00:00:00 trashapplet
 3721 ?        00:00:00 vino-session
 3722 ?        00:00:00 bluetooth-apple
 3725 ?        00:00:00 update-notifier
 3730 ?        00:00:00 evolution-alarm
 3732 ?        00:01:28 trackerd
 3736 ?        00:00:00 mapping-daemon
 3738 ?        00:00:00 nm-applet
 3739 ?        00:00:00 python
 3741 ?        00:00:00 gnome-power-man
 3757 ?        00:00:00 kgameportd
 3763 ?        00:00:00 evolution-excha
 3766 ?        00:00:00 kpsmoused
 3771 ?        00:00:00 evolution-data-
 3792 ?        00:00:00 fast-user-switc
 3794 ?        00:00:01 deskbar-applet
 3796 ?        00:00:00 mixer_applet2
 3809 ?        00:00:01 notification-da
 4412 tty4     00:00:00 getty
 4413 tty5     00:00:00 getty
 4415 tty2     00:00:00 getty
 4417 tty3     00:00:00 getty
 4419 tty1     00:00:00 getty
 4420 tty6     00:00:00 getty
 4606 ?        00:00:00 acpid
 4661 ?        00:00:00 kondemand/0
 4662 ?        00:00:00 kondemand/1
 4731 ?        00:00:00 syslogd
 4787 ?        00:00:00 dd
 4789 ?        00:00:00 klogd
 4810 ?        00:00:01 dbus-daemon
 4826 ?        00:00:00 NetworkManager
 4840 ?        00:00:00 NetworkManagerD
 4853 ?        00:00:00 system-tools-ba
 4854 ?        00:00:00 dbus-daemon
 4873 ?        00:00:01 hald
 4874 ?        00:00:00 hald-runner
 4934 ?        00:00:00 hald-addon-keyb
 4935 ?        00:00:00 hald-addon-keyb
 4936 ?        00:00:00 cupsd
 4937 ?        00:00:00 hald-addon-keyb
 4940 ?        00:00:00 hald-addon-acpi
 5048 ?        00:00:00 console-kit-dae
 5135 ?        00:00:00 avahi-daemon
 5136 ?        00:00:00 avahi-daemon
 5150 ?        00:00:00 dhcdbd
 5172 ?        00:00:00 hcid
 5184 ?        00:00:00 bluetoothd-serv
 5185 ?        00:00:00 bluetoothd-serv
 5193 ?        00:00:00 krfcommd
 5226 ?        00:00:00 gdm
 5229 ?        00:00:00 gdm
 5249 ?        00:00:16 hald-addon-stor
 5295 ?        00:00:00 atd
 5309 ?        00:00:00 cron
 5332 ?        00:00:00 dhclient
 5358 ?        00:00:00 apache2
11023 ?        00:00:02 gnome-terminal
11026 ?        00:00:00 gnome-pty-helpe
11027 pts/0    00:00:00 bash
11065 pts/0    00:00:00 ssh
11141 pts/3    00:00:00 bash
11257 pts/2    00:00:00 ssh
11297 ?        00:00:00 firefox
11309 ?        00:00:00 run-mozilla.sh
11313 ?        00:01:16 firefox-bin
11357 pts/4    00:00:00 ssh
11369 ?        00:00:03 pidgin
11432 pts/3    00:00:00 ps
11787 ?        00:00:02 mount.ntfs-3g
21291 ?        00:00:00 apache2
21292 ?        00:00:00 apache2
21293 ?        00:00:00 apache2
21294 ?        00:00:00 apache2
21295 ?        00:00:00 apache2
22197 ?        00:00:00 pdflush
22307 ?        00:00:01 pdflush

```

---

### Post by taurus on 2007-10-29
Have you tried installing bluefish with synaptic?

---

### Post by tast01 on 2007-10-29
yes, I get the same message in a pop up box

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
```

---

