---
title: "Error with apt-get update or Update Manager"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by amr0th on 2006-09-25
Hi

I'm pretty new to Ubuntu, so please forgive my ignorance.
I've been unable to update my Ubuntu Dapper Drake for the last few days/weeks (I don't know how long, i only  noticed the lack of update warnings/icons recently).
I keep getting the same error message when trying to update manually, whether its in terminal with apt-get update or with the Update Manager itself.
The error message is keep getting is: 
[B]E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily un available)
E: Unable to lock the list directory[/B]

At first I thought it might be a problem with my sources.list file, but i've edited several times, changed it to sources.list's that i've found here on the forum, with no effect.
Here's my sources.list (just in case):

[INDENT]####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
[/INDENT]

At the time of the manual updating i've also checked that no other tool might be interfering with the updates such as Synaptic. The only active update tool is either apt-get or Update Manager.
I've also tried restarting Gnome. No effect.


Do i remove the file in /var/lib/apt/lists/lock ?
Is there any way i can see which user/program/ is currently locking the file?
Does anyone have any ideas?

---

### Post by bulldog on 2006-09-25
Type in your terminal 

sudo aptitude update

And tell me what happens

Where is your sources.list located??
It should be in /etc/apt/sources.list

---

### Post by amr0th on 2006-09-25
Sources list is in etc/apt/sources.list 


Result of sudo aptitude update:

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

---

### Post by Dinerty on 2006-09-25
Make sure you don't have any other software updates running, check this by

```
ps -A
```

Have you tried rebooting?.

Start fresh and close any programs down like Synaptic, adept and so forth ...). Here is a link with someone who had the same problem, perhaps it may help

[http://www.ubuntuforums.org/showthread.php?t=245109&highlight=11+Resource+temporarily+unavailable](http://www.ubuntuforums.org/showthread.php?t=245109&highlight=11+Resource+temporarily+unavailable)

---

### Post by amr0th on 2006-09-26
Here's the result of my ps -A:

  PID TTY          TIME CMD
    1 ?        00:00:05 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:05 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  117 ?        00:00:00 pdflush
  118 ?        00:00:00 pdflush
  120 ?        00:00:00 aio/0
  119 ?        00:00:02 kswapd0
  707 ?        00:00:00 kseriod
 1838 ?        00:00:00 khubd
 1954 ?        00:00:02 kjournald
 2182 ?        00:00:00 udevd
 2977 ?        00:00:00 shpchpd_event
 3102 ?        00:00:00 kgameportd
 3996 ?        00:00:00 dd
 3998 ?        00:00:00 klogd
 4017 ?        00:00:01 dbus-daemon
 4032 ?        00:00:02 hald
 4033 ?        00:00:00 hald-runner
 4038 ?        00:00:00 hald-addon-acpi
 4088 ?        00:00:09 hald-addon-keyb
 4099 ?        00:01:08 hald-addon-stor
 4100 ?        00:00:49 hald-addon-stor
 4102 ?        00:04:53 hald-addon-stor
 4103 ?        00:05:03 hald-addon-stor
 4353 ?        00:00:00 gdm
 4417 ?        00:00:00 hpiod
 4420 ?        00:00:02 python
 4490 ?        00:00:00 mysqld_safe
 4536 ?        00:03:00 mysqld
 4537 ?        00:00:00 logger
 4653 ?        00:00:00 master
 4669 ?        00:00:00 qmgr
 4683 ?        00:00:05 nmbd
 4685 ?        00:00:00 smbd
 4703 ?        00:00:10 sshd
 4750 ?        00:00:00 smbd
 4767 ?        00:00:01 ntpd
 4783 ?        00:00:00 hcid
 4787 ?        00:00:00 sdpd
 4799 ?        00:00:00 krfcommd
 4813 ?        00:00:00 mdadm
 4855 ?        00:00:00 atd
 4868 ?        00:00:00 cron
 4966 tty1     00:00:00 getty
 4967 tty2     00:00:00 getty
 4968 tty3     00:00:00 getty
 4969 tty4     00:00:00 getty
 4970 tty5     00:00:00 getty
 4971 tty6     00:00:00 getty
 5041 ?        00:00:04 gconfd-2
 5044 ?        00:00:00 gnome-keyring-d
 5046 ?        00:00:00 bonobo-activati
 5074 ?        21-09:52:32 gnome-cups-icon
 9098 ?        00:00:00 mount.smbfs
 9103 ?        00:00:03 smbiod
 2555 ?        00:00:00 acpid
 2618 ?        00:00:01 apache2
 2625 ?        00:00:00 apache2
 2626 ?        00:00:00 apache2
 2627 ?        00:00:00 apache2
 2628 ?        00:00:00 apache2
 2629 ?        00:00:00 apache2
19250 ?        00:00:00 proftpd
 9178 ?        00:03:03 cupsd
17368 ?        00:00:02 screen
17369 pts/3    00:00:00 bash
17378 pts/3    00:00:12 irssi
17897 ?        00:00:00 anacron
17900 ?        00:00:00 run-parts
17904 ?        00:00:00 apt
17917 ?        00:00:01 apt-get
17920 ?        00:00:00 http
17921 ?        00:00:00 ftp
17922 ?        00:00:00 ftp
17923 ?        00:00:00 http
17924 ?        00:00:00 http
17925 ?        00:00:00 http
17927 ?        00:00:00 gpgv
17932 ?        00:00:00 bzip2
17935 ?        00:00:00 bzip2 <defunct>
26487 ?        00:00:00 gdm
26490 tty7     00:55:12 Xorg
26506 ?        00:00:03 x-session-manag
26552 ?        00:00:00 ssh-agent
26555 ?        00:00:00 dbus-launch
26556 ?        00:00:00 dbus-daemon
26559 ?        00:00:00 gnome-keyring-d
26561 ?        00:00:30 gnome-settings-
26563 ?        00:00:00 esd
26574 ?        00:02:26 metacity
26578 ?        00:01:04 nautilus
26580 ?        00:02:16 gnome-panel
26581 ?        00:00:04 gnome-volume-ma
26586 ?        00:00:06 update-notifier
26594 ?        00:00:01 gnome-vfs-daemo
26590 ?        00:01:38 gnome-terminal
26606 ?        00:00:04 trashapplet
26616 ?        00:00:06 gnome-power-man
26628 ?        00:00:00 gnome-pty-helpe
26638 ?        00:00:00 mapping-daemon
26659 ?        00:00:05 mixer_applet2
26661 ?        00:00:05 clock-applet
30716 ?        01:38:31 firefox-bin
 2733 ?        00:00:00 evolution-data-
 2739 ?        00:00:02 evolution-alarm
 3454 ?        00:00:11 at-spi-registry
13539 ?        00:00:00 syslogd
20770 ?        00:00:02 screen
20771 pts/2    00:00:00 bash
20782 pts/2    00:00:27 irssi
26089 ?        00:00:00 evolution-excha
  826 ?        00:01:09 evolution
  964 pts/1    00:00:00 bash
 1111 pts/0    00:00:00 bash
 1782 ?        00:00:00 pickup
 1784 ?        00:00:05 gaim
 1841 ?        00:00:00 esd
 1849 pts/1    00:00:00 ps


I noticed apt and apt-get in the ps list, do i kill both processes?

---

### Post by amr0th on 2006-09-26
I killed the existing apt-get process.
Now I'm able to get apt-get update & Update Manager working again. 

Thank for the help :-D

---

### Post by randell6564 on 2007-10-13
> **amr0th said:**
> I killed the existing apt-get process.
Now I'm able to get apt-get update & Update Manager working again. 

Thank for the help :-D
[COLOR="Red"]Hello!
How do I "kill" these processes?  I'm having the same problem.
Thanks![/COLOR]

---

### Post by llamakc on 2007-10-13
There are multiple ways to do this, but the quick and dirty is:

killall name-of-process [sudo killall apt-get]

or 

kill -9 PID

where PID is the process ID

---

### Post by randell6564 on 2007-10-13
> **llamakc said:**
> There are multiple ways to do this, but the quick and dirty is:

killall name-of-process [sudo killall apt-get]

or 

kill -9 PID

where PID is the process ID
[COLOR="Red"]Thank you my friend[/COLOR]

---

