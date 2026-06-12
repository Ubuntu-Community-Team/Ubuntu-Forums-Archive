---
title: "Cannot receive update packages, automatix problems etc."
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by CAX on 2007-01-07
many problems here (edgy user): 

1. I cannot get the update packages. It says that some other applicaton is using the package database even if I just logged in to the system. Any help on this one? How do I check that nothing started automatically?

2. when trying to install nvida with automatix it starts installing sun java 1.5 I think and then just stall on a window where I can read the license agreement with an ok written at the bottom of the text but the problem is that it is text and not and active button. Not sure about this one. And in general nothing installs when using automatix. normally it tells me (shortly seen in the terminal like window that shows up) that I should try to solve some problems by running dpkg --configure -a of sometimes -g etc... seems like there is an underlying common problem here.

Thanks in advance!

](*,)

---

### Post by taurus on 2007-01-07
1.  Paste the output of this command here.  

Applications -> Accessories -> Terminal
```
ps -A
```

2.  Use the down arrow to scroll down and at the end, hit the Tag key to highlight the OK.  Then, hit the return to agree to the license.  And if you want to install nVidia driver, here's a guide for you.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by CAX on 2007-01-07
ps -A gave:


  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  147 ?        00:00:00 pdflush
  148 ?        00:00:00 pdflush
  149 ?        00:00:00 kswapd0
  150 ?        00:00:00 aio/0
 1715 ?        00:00:00 khubd
 1734 ?        00:00:00 khpsbpkt
 1756 ?        00:00:00 knodemgrd_0
 1804 ?        00:00:00 kjournald
 1879 ?        00:00:00 logd
 2025 ?        00:00:00 udevd
 2756 ?        00:00:00 shpchpd
 2798 ?        00:00:00 kpsmoused
 2933 ?        00:00:00 pccardd
 2963 ?        00:00:00 scsi_eh_0
 2964 ?        00:00:00 usb-storage
 3620 tty1     00:00:00 getty
 3621 tty2     00:00:00 getty
 3622 tty3     00:00:00 getty
 3626 tty4     00:00:00 getty
 3627 tty5     00:00:00 getty
 3628 tty6     00:00:00 getty
 3853 ?        00:00:00 acpid
 3942 ?        00:00:00 syslogd
 3968 ?        00:00:00 dd
 3970 ?        00:00:00 klogd
 3983 ?        00:00:00 kdm
 3999 tty7     00:01:06 Xorg
 4005 ?        00:00:00 kdm
 4016 ?        00:00:00 cupsd
 4035 ?        00:00:00 hpiod
 4038 ?        00:00:00 python
 4083 ?        00:00:00 apt-index-watch
 4099 ?        00:00:00 dbus-daemon
 4114 ?        00:00:03 hald
 4115 ?        00:00:00 hald-runner
 4121 ?        00:00:00 hald-addon-acpi
 4129 ?        00:00:00 hald-addon-keyb
 4147 ?        00:00:00 hald-addon-stor
 4195 ?        00:00:00 ondemand
 4237 ?        00:00:00 hcid
 4244 ?        00:00:00 sdpd
 4255 ?        00:00:00 krfcommd
 4288 ?        00:00:00 atd
 4302 ?        00:00:00 cron
 4382 ?        00:00:00 dhclient3
 4390 ?        00:00:00 x-session-manag
 4426 ?        00:00:00 ssh-agent
 4429 ?        00:00:00 dbus-launch
 4430 ?        00:00:00 dbus-daemon
 4460 ?        00:00:00 start_kdeinit
 4461 ?        00:00:00 kdeinit
 4464 ?        00:00:00 dcopserver
 4467 ?        00:00:00 klauncher
 4469 ?        00:00:01 kded
 4475 ?        00:00:00 kwrapper
 4477 ?        00:00:00 ksmserver
 4478 ?        00:00:03 kwin
 4480 ?        00:00:02 kdesktop
 4484 ?        00:00:00 kio_uiserver
 4503 ?        00:00:05 artsd
 4506 ?        00:00:00 kaccess
 4511 ?        00:00:00 kmix
 4512 ?        00:00:00 katapult
 4521 ?        00:00:00 guidance-power-
 4522 ?        00:01:17 firefox-bin
 4525 ?        00:00:00 kio_file
 4538 ?        00:00:00 aspell
 4554 ?        00:00:00 knotify
 4557 ?        00:00:00 passkey-agent
 4561 ?        00:00:00 kbluetoothd
 4562 ?        00:00:12 adept_notifier
 4604 ?        00:00:00 gconfd-2
 4605 ?        00:00:06 guidance-power-
 4625 ?        00:00:00 kdesud
 4833 ?        00:00:00 vol_id
 4963 ?        00:00:02 aptitude
 5181 ?        00:00:00 dpkg
 5191 ?        00:00:00 frontend
 5197 ?        00:00:00 preinst
 5199 ?        00:03:13 whiptail
 5313 ?        00:00:00 konsole
 5314 pts/2    00:00:00 bash
 5334 ?        00:00:01 kicker
 5335 ?        00:00:00 kio_system
 5336 ?        00:00:00 kio_trash
 5345 pts/2    00:00:00 ps

---

### Post by taurus on 2007-01-07
Do you by any chance have aptitude running right now?  Close everything down and send me the output of that command again.

```
ps -A
```

---

### Post by ajmorris on 2007-01-07
apptitude is running, Correct me if i'm wrong but i think that conflicts with it. Also do you have synaptic or another package manager open or do you have your "/etc/apt/source.list" file open?

---

### Post by ajmorris on 2007-01-07
> **taurus said:**
> Do you by any chance have aptitude running right now? Close everything down and send me the output of that command again.

Code:

ps -A



Sorry, we have basically the same post. We posted at the same time. lol. :)

---

### Post by CAX on 2007-01-07
yeah the aptitude notifier was running. Now after I closed it:

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  147 ?        00:00:00 pdflush
  148 ?        00:00:00 pdflush
  149 ?        00:00:00 kswapd0
  150 ?        00:00:00 aio/0
 1715 ?        00:00:00 khubd
 1734 ?        00:00:00 khpsbpkt
 1756 ?        00:00:00 knodemgrd_0
 1804 ?        00:00:00 kjournald
 1879 ?        00:00:00 logd
 2025 ?        00:00:00 udevd
 2756 ?        00:00:00 shpchpd
 2798 ?        00:00:00 kpsmoused
 2933 ?        00:00:00 pccardd
 2963 ?        00:00:00 scsi_eh_0
 2964 ?        00:00:00 usb-storage
 3620 tty1     00:00:00 getty
 3621 tty2     00:00:00 getty
 3622 tty3     00:00:00 getty
 3626 tty4     00:00:00 getty
 3627 tty5     00:00:00 getty
 3628 tty6     00:00:00 getty
 3853 ?        00:00:00 acpid
 3942 ?        00:00:00 syslogd
 3968 ?        00:00:00 dd
 3970 ?        00:00:00 klogd
 3983 ?        00:00:00 kdm
 3999 tty7     00:01:16 Xorg
 4005 ?        00:00:00 kdm
 4016 ?        00:00:00 cupsd
 4035 ?        00:00:00 hpiod
 4038 ?        00:00:00 python
 4083 ?        00:00:00 apt-index-watch
 4099 ?        00:00:00 dbus-daemon
 4114 ?        00:00:03 hald
 4115 ?        00:00:00 hald-runner
 4121 ?        00:00:00 hald-addon-acpi
 4129 ?        00:00:00 hald-addon-keyb
 4147 ?        00:00:00 hald-addon-stor
 4195 ?        00:00:00 ondemand
 4237 ?        00:00:00 hcid
 4244 ?        00:00:00 sdpd
 4255 ?        00:00:00 krfcommd
 4288 ?        00:00:00 atd
 4302 ?        00:00:00 cron
 4382 ?        00:00:00 dhclient3
 4390 ?        00:00:00 x-session-manag
 4426 ?        00:00:00 ssh-agent
 4429 ?        00:00:00 dbus-launch
 4430 ?        00:00:00 dbus-daemon
 4460 ?        00:00:00 start_kdeinit
 4461 ?        00:00:00 kdeinit
 4464 ?        00:00:00 dcopserver
 4467 ?        00:00:00 klauncher
 4469 ?        00:00:01 kded
 4475 ?        00:00:00 kwrapper
 4477 ?        00:00:00 ksmserver
 4478 ?        00:00:03 kwin
 4480 ?        00:00:02 kdesktop
 4484 ?        00:00:00 kio_uiserver
 4503 ?        00:00:05 artsd
 4506 ?        00:00:00 kaccess
 4511 ?        00:00:00 kmix
 4512 ?        00:00:00 katapult
 4521 ?        00:00:00 guidance-power-
 4522 ?        00:01:25 firefox-bin
 4525 ?        00:00:00 kio_file
 4538 ?        00:00:00 aspell
 4554 ?        00:00:00 knotify
 4557 ?        00:00:00 passkey-agent
 4561 ?        00:00:00 kbluetoothd
 4604 ?        00:00:00 gconfd-2
 4605 ?        00:00:06 guidance-power-
 4625 ?        00:00:00 kdesud
 4833 ?        00:00:00 vol_id
 4963 ?        00:00:02 aptitude
 5181 ?        00:00:00 dpkg
 5191 ?        00:00:00 frontend
 5197 ?        00:00:00 preinst
 5199 ?        00:09:19 whiptail
 5313 ?        00:00:01 konsole
 5314 pts/2    00:00:00 bash
 5334 ?        00:00:01 kicker
 5397 ?        00:00:00 artsd
 5399 pts/2    00:00:00 ps

also tried killall get-apt and no processes was terminated

---

### Post by taurus on 2007-01-07
> **ajmorris said:**
> apptitude is running, Correct me if i'm wrong but i think that conflicts with it. Also do you have synaptic or another package manager open or do you have your "/etc/apt/source.list" file open?

```
4562 ? 00:00:12 adept_notifier
4963 ? 00:00:02 aptitude
```

---

### Post by taurus on 2007-01-07
Here's the process you need to terminate.

```
4963 ? 00:00:02 aptitude
```
So from a terminal, run

```
sudo kill -9 4963
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Frak on 2007-01-07
You cant run more than one apt proccess at a time, **taurus**, tell me if I'm wrong with this code:

```
kill 4562
```

I have to learn how to use this code too, as this happens to me all the time, so might as well start practising.

---

### Post by CAX on 2007-01-07
well *I tried this and:

cax@cax-laptop:~$ sudo kill -9 4963
cax@cax-laptop:~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Get:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Translation-en_US
Get:4 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:5 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 10B in 1s (7B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

---

### Post by taurus on 2007-01-07
Paste that output again!

```
ps -A
```

---

### Post by CAX on 2007-01-07
here you go:

cax@cax-laptop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  147 ?        00:00:00 pdflush
  148 ?        00:00:00 pdflush
  149 ?        00:00:00 kswapd0
  150 ?        00:00:00 aio/0
 1715 ?        00:00:00 khubd
 1734 ?        00:00:00 khpsbpkt
 1756 ?        00:00:00 knodemgrd_0
 1804 ?        00:00:00 kjournald
 1879 ?        00:00:00 logd
 2025 ?        00:00:00 udevd
 2756 ?        00:00:00 shpchpd
 2798 ?        00:00:00 kpsmoused
 2933 ?        00:00:00 pccardd
 2963 ?        00:00:00 scsi_eh_0
 2964 ?        00:00:00 usb-storage
 3620 tty1     00:00:00 getty
 3621 tty2     00:00:00 getty
 3622 tty3     00:00:00 getty
 3626 tty4     00:00:00 getty
 3627 tty5     00:00:00 getty
 3628 tty6     00:00:00 getty
 3853 ?        00:00:00 acpid
 3942 ?        00:00:00 syslogd
 3968 ?        00:00:00 dd
 3970 ?        00:00:00 klogd
 3983 ?        00:00:00 kdm
 3999 tty7     00:01:38 Xorg
 4005 ?        00:00:00 kdm
 4016 ?        00:00:00 cupsd
 4035 ?        00:00:00 hpiod
 4038 ?        00:00:00 python
 4083 ?        00:00:00 apt-index-watch
 4099 ?        00:00:00 dbus-daemon
 4114 ?        00:00:03 hald
 4115 ?        00:00:00 hald-runner
 4121 ?        00:00:00 hald-addon-acpi
 4129 ?        00:00:00 hald-addon-keyb
 4147 ?        00:00:00 hald-addon-stor
 4195 ?        00:00:00 ondemand
 4237 ?        00:00:00 hcid
 4244 ?        00:00:00 sdpd
 4255 ?        00:00:00 krfcommd
 4288 ?        00:00:00 atd
 4302 ?        00:00:00 cron
 4382 ?        00:00:00 dhclient3
 4390 ?        00:00:00 x-session-manag
 4426 ?        00:00:00 ssh-agent
 4429 ?        00:00:00 dbus-launch
 4430 ?        00:00:00 dbus-daemon
 4460 ?        00:00:00 start_kdeinit
 4461 ?        00:00:00 kdeinit
 4464 ?        00:00:00 dcopserver
 4467 ?        00:00:00 klauncher
 4469 ?        00:00:01 kded
 4475 ?        00:00:00 kwrapper
 4477 ?        00:00:00 ksmserver
 4478 ?        00:00:04 kwin
 4480 ?        00:00:02 kdesktop
 4484 ?        00:00:00 kio_uiserver
 4503 ?        00:00:05 artsd
 4506 ?        00:00:00 kaccess
 4511 ?        00:00:00 kmix
 4512 ?        00:00:00 katapult
 4521 ?        00:00:00 guidance-power-
 4522 ?        00:01:43 firefox-bin
 4525 ?        00:00:00 kio_file
 4538 ?        00:00:00 aspell
 4554 ?        00:00:00 knotify
 4557 ?        00:00:00 passkey-agent
 4561 ?        00:00:00 kbluetoothd
 4604 ?        00:00:00 gconfd-2
 4605 ?        00:00:06 guidance-power-
 4625 ?        00:00:00 kdesud
 4833 ?        00:00:00 vol_id
 5181 ?        00:00:00 dpkg
 5191 ?        00:00:00 frontend
 5197 ?        00:00:00 preinst
 5199 ?        00:18:20 whiptail
 5313 ?        00:00:01 konsole
 5314 pts/2    00:00:00 bash
 5334 ?        00:00:01 kicker
 5445 pts/2    00:00:00 ps

---

### Post by taurus on 2007-01-07
```
sudo kill -9 5181
sudo aptitude update
```

---

### Post by CAX on 2007-01-07
cax@cax-laptop:~$ sudo kill -9 5181
cax@cax-laptop:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Translation-en_US
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Sources
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 10B in 0s (12B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache
cax@cax-laptop:~$

---

### Post by CAX on 2007-01-07
cax@cax-laptop:~$  sudo dpkg --configure -a
cax@cax-laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:4 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Translation-en_US
Get:7 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:8 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy Release
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 10B in 1s (6B/s)
Reading package lists... Done
cax@cax-laptop:~$

---

### Post by taurus on 2007-01-07
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by CAX on 2007-01-07
> **taurus said:**
> ```
sudo dpkg --configure -a
sudo aptitude update
```


Yup, did that as you see from my post above. Also ran "sudo aptitude upgrade" after that. Think it worked as it took some time (although not that long). Too long to post the whole output here but at the end the following was listed:

Errors were encountered while processing:
 x11-common
 screen

---

### Post by taurus on 2007-01-07
What's the exactly error message for those two packages when you ran the "sudo aptitude upgrade"?

---

### Post by CAX on 2007-01-07
I'll have to get back to you on that one. I have restarted the computer and now automatix seems to be working. and being able to install all the things I want (being fresh system install it is quite a lot). Thanks for all the help so far! I think that Bill has nothing in comparance to this "customer" service :P

---

### Post by taurus on 2007-01-07
> **CAX said:**
> I'll have to get back to you on that one. I have restarted the computer and now automatix seems to be working. and being able to install all the things I want (being fresh system install it is quite a lot). 

Sometimes a reboot would cure the illness...  ;) 

> Thanks for all the help so far! I think that Bill has nothing in comparance to this "customer" service :P

You think so...  :mrgreen:

---

### Post by arnieboy on 2007-01-07
when the EULA for java comes up in xterm, all you need to do is hit Tab to highlight OK and then press enter.

---

