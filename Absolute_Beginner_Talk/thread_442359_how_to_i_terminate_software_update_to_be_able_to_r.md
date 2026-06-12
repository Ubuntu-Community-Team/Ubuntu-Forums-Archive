---
title: "how to i terminate software update to be able to run it again?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-13
i had to shut down and restart the computer thinking that software update will be terminated since it really took a long time to install 33Mb of update (the files were downloaded, it just needed to be installed completely). i think it hung since the black box that blinks in the terminal doesn't blink anymore. now that i've started the computer and ran software manager to choose what to update (i choose only a few, about 30Mb per download, so as not to hag the pc), it tells me that only one software management tool is allowed to run at the same time e.g. aptitude or synaptic first.

so my question is, how do i terminate it so i can run it again? i tried finding aptitude and synaptic in system monitor but it's not there, any suggestions? like is there another task manager? any help will be appreciated.

---

### Post by taurus on 2007-05-13
Maybe you should look for adept.

```
ps -A
```

---

### Post by j_evenstar on 2007-05-13
here it is:
```
jillian@jillian-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  107 ?        00:00:00 pdflush
  108 ?        00:00:00 pdflush
  110 ?        00:00:00 aio/0
  109 ?        00:00:00 kswapd0
  697 ?        00:00:00 kseriod
 1821 ?        00:00:00 khubd
 1922 ?        00:00:00 kjournald
 2148 ?        00:00:00 udevd
 2949 ?        00:00:00 shpchpd_event
 2995 ?        00:00:00 kgameportd
 3470 ?        00:00:00 dhclient3
 3881 ?        00:00:00 acpid
 3971 ?        00:00:00 syslogd
 3997 ?        00:00:00 dd
 3999 ?        00:00:00 klogd
 4318 ?        00:00:00 gdm
 4328 ?        00:00:00 gdm
 4335 tty7     00:00:46 Xorg
 4357 ?        00:00:00 hpiod
 4361 ?        00:00:00 python
 4408 ?        00:00:00 cupsd
 4433 ?        00:00:00 dbus-daemon
 4448 ?        00:00:01 hald
 4449 ?        00:00:00 hald-runner
 4454 ?        00:00:00 hald-addon-acpi
 4510 ?        00:00:00 hald-addon-keyb
 4521 ?        00:00:00 hald-addon-stor
 4522 ?        00:00:00 hald-addon-stor
 4524 ?        00:00:00 hald-addon-stor
 4525 ?        00:00:00 hald-addon-stor
 4603 ?        00:00:00 hcid
 4608 ?        00:00:00 sdpd
 4617 ?        00:00:00 krfcommd
 4631 ?        00:00:00 mdadm
 4665 ?        00:00:00 atd
 4678 ?        00:00:00 cron
 4754 tty1     00:00:00 getty
 4755 tty2     00:00:00 getty
 4756 tty3     00:00:00 getty
 4757 tty4     00:00:00 getty
 4758 tty5     00:00:00 getty
 4759 tty6     00:00:00 getty
 4770 ?        00:00:00 x-session-manag
 4812 ?        00:00:00 ssh-agent
 4815 ?        00:00:00 dbus-launch
 4816 ?        00:00:00 dbus-daemon
 4818 ?        00:00:00 gconfd-2
 4821 ?        00:00:00 gnome-keyring-d
 4823 ?        00:00:00 bonobo-activati
 4825 ?        00:00:01 gnome-settings-
 4827 ?        00:00:00 esd
 4834 ?        00:00:03 metacity
 4840 ?        00:00:03 gnome-panel
 4842 ?        00:00:01 nautilus
 4845 ?        00:00:00 gnome-volume-ma
 4853 ?        00:00:00 update-notifier
 4858 ?        00:00:00 gnome-vfs-daemo
 4863 ?        00:00:00 gnome-cups-icon
 4870 ?        00:00:00 trashapplet
 4871 ?        00:00:00 gnome-power-man
 4882 ?        00:00:00 mapping-daemon
 4887 ?        00:00:00 clock-applet
 4889 ?        00:00:00 mixer_applet2
 4895 ?        00:00:00 notification-da
 4905 ?        00:00:00 gnome-screensav
 5062 ?        00:00:00 firefox
 5073 ?        00:00:00 run-mozilla.sh
 5078 ?        00:00:47 firefox-bin
 5331 ?        00:00:00 at-spi-registry
 5558 ?        00:00:00 gnome-terminal
 5559 ?        00:00:00 gnome-pty-helpe
 5560 pts/0    00:00:00 bash
 5578 pts/0    00:00:00 ps
jillian@jillian-desktop:~$
```
uhm does this have update manager/software updates running? if so, how do i terminate it. thanks. and when i terminate it will it work again and i can run it again? sorry for being anxious.:confused:
thanks..

---

### Post by j_evenstar on 2007-05-13
help please..

---

### Post by j_evenstar on 2007-05-13
help help help

---

