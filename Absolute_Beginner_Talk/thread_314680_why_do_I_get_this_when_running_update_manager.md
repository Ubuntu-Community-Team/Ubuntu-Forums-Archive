---
title: "why do I get this when running update manager?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by tribeone on 2006-12-07
Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.

How do I fix this???

---

### Post by taurus on 2006-12-07
Do you have synaptic or aptitude running at all?

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by tribeone on 2006-12-07
I dont know.I  installed easyuuntu and then tried to install automatix but it failed to install. I don't know what is going on. That ps -A returns this

```
[CODE]
:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  113 ?        00:00:00 pdflush
  114 ?        00:00:00 pdflush
  116 ?        00:00:00 aio/0
  115 ?        00:00:00 kswapd0
  703 ?        00:00:00 kseriod
 1798 ?        00:00:00 khubd
 1892 ?        00:00:00 kjournald
 2118 ?        00:00:00 udevd
 2874 ?        00:00:00 shpchpd_event
 2949 ?        00:00:00 kgameportd
 3462 ?        00:00:00 dhclient3
 3787 ?        00:00:00 acpid
 3877 ?        00:00:00 syslogd
 3903 ?        00:00:00 dd
 3905 ?        00:00:00 klogd
 4228 ?        00:00:00 gdm
 4245 ?        00:00:00 gdm
 4262 tty7     01:07:07 Xorg
 4269 ?        00:00:00 hpiod
 4275 ?        00:00:00 python
 4322 ?        00:00:00 cupsd
 4347 ?        00:00:00 dbus-daemon
 4362 ?        00:00:01 hald
 4363 ?        00:00:00 hald-runner
 4368 ?        00:00:00 hald-addon-acpi
 4424 ?        00:00:00 hald-addon-keyb
 4435 ?        00:00:00 hald-addon-stor
 4436 ?        00:00:00 hald-addon-stor
 4539 ?        00:00:00 hcid
 4543 ?        00:00:00 sdpd
 4558 ?        00:00:00 krfcommd
 4571 ?        00:00:00 mdadm
 4605 ?        00:00:00 atd
 4618 ?        00:00:00 cron
 4690 tty1     00:00:00 getty
 4691 tty2     00:00:00 getty
 4692 tty3     00:00:00 getty
 4693 tty4     00:00:00 getty
 4694 tty5     00:00:00 getty
 4695 tty6     00:00:00 getty
 4845 ?        00:00:00 dhclient3
19635 ?        00:00:00 gconfd-2
19651 ?        00:00:00 x-session-manag
19693 ?        00:00:00 ssh-agent
19696 ?        00:00:00 dbus-daemon
19697 ?        00:00:00 dbus-launch
19700 ?        00:00:00 gnome-keyring-d
19702 ?        00:00:00 bonobo-activati
19704 ?        00:00:00 esd
19706 ?        00:00:00 gnome-settings-
19711 ?        00:00:03 metacity
19717 ?        00:00:02 gnome-panel
19719 ?        00:00:01 nautilus
19726 ?        00:00:00 update-notifier
19730 ?        00:00:00 gnome-cups-icon
19733 ?        00:00:00 gnome-volume-ma
19737 ?        00:00:00 gnome-vfs-daemo
19752 ?        00:00:00 gnome-power-man
19754 ?        00:00:00 trashapplet
19760 ?        00:00:00 mapping-daemon
19766 ?        00:00:00 mixer_applet2
19768 ?        00:00:00 clock-applet
19785 ?        00:00:00 gnome-screensav
19926 ?        00:00:34 firefox-bin
19969 ?        00:00:00 notification-da
20349 ?        00:00:00 gnome-terminal
20350 ?        00:00:00 gnome-pty-helpe
20351 pts/0    00:00:00 bash
20439 pts/1    00:00:00 bash
20569 pts/1    00:00:00 ps


```[/CODE]

---

### Post by taurus on 2006-12-07
I am not sure if you want to install both easyubuntu and automatix2 on the same machine since they are both doing pretty similar task.  Can you paste the output of that command to see if you have something line synaptic or aptitude running in the background before you use automatix2?

```
ps -A
```

p.s.  Just so you know.  You cannot run automatix2 if you have synaptic open or run aptitude from a terminal.  You can only run one thing at a time...

p.s.s.  Need to see the rest of that output though!

---

### Post by tribeone on 2006-12-07
Here you go. I have no idea what all this means.

```
~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  113 ?        00:00:00 pdflush
  114 ?        00:00:00 pdflush
  116 ?        00:00:00 aio/0
  115 ?        00:00:00 kswapd0
  703 ?        00:00:00 kseriod
 1798 ?        00:00:00 khubd
 1892 ?        00:00:00 kjournald
 2118 ?        00:00:00 udevd
 2874 ?        00:00:00 shpchpd_event
 2949 ?        00:00:00 kgameportd
 3462 ?        00:00:00 dhclient3
 3787 ?        00:00:00 acpid
 3877 ?        00:00:00 syslogd
 3903 ?        00:00:00 dd
 3905 ?        00:00:00 klogd
 4228 ?        00:00:00 gdm
 4245 ?        00:00:00 gdm
 4262 tty7     01:07:07 Xorg
 4269 ?        00:00:00 hpiod
 4275 ?        00:00:00 python
 4322 ?        00:00:00 cupsd
 4347 ?        00:00:00 dbus-daemon
 4362 ?        00:00:01 hald
 4363 ?        00:00:00 hald-runner
 4368 ?        00:00:00 hald-addon-acpi
 4424 ?        00:00:00 hald-addon-keyb
 4435 ?        00:00:00 hald-addon-stor
 4436 ?        00:00:00 hald-addon-stor
 4539 ?        00:00:00 hcid
 4543 ?        00:00:00 sdpd
 4558 ?        00:00:00 krfcommd
 4571 ?        00:00:00 mdadm
 4605 ?        00:00:00 atd
 4618 ?        00:00:00 cron
 4690 tty1     00:00:00 getty
 4691 tty2     00:00:00 getty
 4692 tty3     00:00:00 getty
 4693 tty4     00:00:00 getty
 4694 tty5     00:00:00 getty
 4695 tty6     00:00:00 getty
 4845 ?        00:00:00 dhclient3
19635 ?        00:00:00 gconfd-2
19651 ?        00:00:00 x-session-manag
19693 ?        00:00:00 ssh-agent
19696 ?        00:00:00 dbus-daemon
19697 ?        00:00:00 dbus-launch
19700 ?        00:00:00 gnome-keyring-d
19702 ?        00:00:00 bonobo-activati
19704 ?        00:00:00 esd
19706 ?        00:00:00 gnome-settings-
19711 ?        00:00:03 metacity
19717 ?        00:00:02 gnome-panel
19719 ?        00:00:01 nautilus
19726 ?        00:00:00 update-notifier
19730 ?        00:00:00 gnome-cups-icon
19733 ?        00:00:00 gnome-volume-ma
19737 ?        00:00:00 gnome-vfs-daemo
19752 ?        00:00:00 gnome-power-man
19754 ?        00:00:00 trashapplet
19760 ?        00:00:00 mapping-daemon
19766 ?        00:00:00 mixer_applet2
19768 ?        00:00:00 clock-applet
19785 ?        00:00:00 gnome-screensav
19926 ?        00:00:34 firefox-bin
19969 ?        00:00:00 notification-da
20349 ?        00:00:00 gnome-terminal
20350 ?        00:00:00 gnome-pty-helpe
20351 pts/0    00:00:00 bash
20439 pts/1    00:00:00 bash
20569 pts/1    00:00:00 p
```s

---

### Post by taurus on 2006-12-07
Now tell me exactly what you want to do!  Do you want to check to see if there are updates?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by tribeone on 2006-12-07
This is what I get when I run those two commands:

```
~$ sudo aptitude update
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get:4 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Get:5 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:6 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:7 http://us.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Sources
Hit http://us.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 7B in 4s (1B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache

~$ sudo aptitude upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

---

### Post by taurus on 2006-12-07
From a terminal, run

```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by tribeone on 2006-12-08
Ok, this is what I get:

```
:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 7B in 0s (8B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

:~$ sudo aptitude upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

