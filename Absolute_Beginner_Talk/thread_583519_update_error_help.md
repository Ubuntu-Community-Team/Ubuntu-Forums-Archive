---
title: "update error help"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by campbuds on 2007-10-20
Here is the errors it is telling me about... (it also saidto fix packages first)

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

When I put in "sudo aptitude update" I get this,,,

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or 

here is the results of ps -A...

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  115 ?        00:00:00 pdflush
  116 ?        00:00:00 pdflush
  118 ?        00:00:00 aio/0
  117 ?        00:00:00 kswapd0
  705 ?        00:00:00 kseriod
 1802 ?        00:00:00 khubd
 1874 ?        00:00:00 kjournald
 2100 ?        00:00:00 udevd
 2854 ?        00:00:00 shpchpd_event
 2905 ?        00:00:00 w1_control
 2909 ?        00:00:00 w1_bus_master1
 2927 ?        00:00:00 kgameportd
 3309 ?        00:00:00 dhclient3
 3768 ?        00:00:00 acpid
 3861 ?        00:00:00 syslogd
 3887 ?        00:00:00 dd
 3889 ?        00:00:00 klogd
 4208 ?        00:00:00 gdm
 4216 ?        00:00:00 gdm
 4242 tty7     00:03:08 Xorg
 4251 ?        00:00:00 hpiod
 4275 ?        00:00:00 python
 4322 ?        00:00:00 cupsd
 4347 ?        00:00:00 dbus-daemon
 4362 ?        00:00:01 hald
 4363 ?        00:00:00 hald-runner
 4368 ?        00:00:00 hald-addon-acpi
 4424 ?        00:00:00 hald-addon-keyb
 4435 ?        00:00:02 hald-addon-stor
 4436 ?        00:00:00 hald-addon-stor
 4513 ?        00:00:00 hcid
 4517 ?        00:00:00 sdpd
 4532 ?        00:00:00 krfcommd
 4545 ?        00:00:00 mdadm
 4579 ?        00:00:00 atd
 4592 ?        00:00:00 cron
 4664 tty1     00:00:00 getty
 4665 tty2     00:00:00 getty
 4666 tty3     00:00:00 getty
 4667 tty4     00:00:00 getty
 4668 tty5     00:00:00 getty
 4669 tty6     00:00:00 getty
 4688 ?        00:00:01 x-session-manag
 4730 ?        00:00:00 ssh-agent
 4733 ?        00:00:00 dbus-launch
 4734 ?        00:00:00 dbus-daemon
 4736 ?        00:00:00 gconfd-2
 4739 ?        00:00:00 gnome-keyring-d
 4741 ?        00:00:00 bonobo-activati
 4743 ?        00:00:02 gnome-settings-
 4747 ?        00:00:00 esd
 4751 ?        00:00:00 esd
 4757 ?        00:00:16 metacity
 4762 ?        00:00:13 gnome-panel
 4764 ?        00:00:17 nautilus
 4769 ?        00:00:00 gnome-volume-ma
 4775 ?        00:00:01 update-notifier
 4779 ?        00:00:00 gnome-vfs-daemo
 4784 ?        00:00:00 gnome-cups-icon
 4792 ?        00:00:01 trashapplet
 4794 ?        00:00:00 gnome-power-man
 4804 ?        00:00:00 mapping-daemon
 4806 ?        00:00:00 clock-applet
 4808 ?        00:00:00 mixer_applet2
 4822 ?        00:00:02 gnome-screensav
 5387 ?        00:00:01 at-spi-registry
 7171 ?        00:00:44 firefox-bin
 7521 ?        00:00:01 gnome-terminal
 7522 ?        00:00:00 gnome-pty-helpe
 7523 pts/0    00:00:00 bash
 7584 pts/0    00:00:00 ps


I was looking for apt and apt-get like I read in another post to kill them but couldn't find em. What do I do?

---

### Post by campbuds on 2007-10-21
still need help with this

---

### Post by mikeyphi on 2007-10-21
What are you try to update?

open a terminal and run 'sudo dpkg --configure -a'

might help-can't hurt!

---

### Post by campbuds on 2007-10-24
here is the result from that. I need to get this fixed.

dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

---

