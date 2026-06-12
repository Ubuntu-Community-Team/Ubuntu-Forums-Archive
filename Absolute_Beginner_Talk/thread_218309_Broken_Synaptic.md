---
title: "Broken Synaptic"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Sq322 on 2006-07-18
trying to run synaptic in GUI i get an error that it is in use
trying to run from a command line i get this
> <username>@<username>-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


Here is my sources.list file
> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free


Any help would be greatly appreciated. Thx

---

### Post by T700 on 2006-07-18
Sounds like you might have another package manager open.  Maybe a terminal session?  Adept?

If not, you can delete the lock file and that will fix it.

Paul

---

### Post by taurus on 2006-07-18
See if you have apt-get or something similar to that running in the background!  Type this from a terminal and look at the list...

```

ps -A

```
Then, kill it with the kill command

```

sudo kill -9 <process number from the first column>

```

---

### Post by Arisna on 2006-07-18
Try `**sudo** apt-get update' at a command line.  You'll have to type your password in to get admin privileges.  That will either work or give a fancier error message.

---

### Post by Sq322 on 2006-07-18
> ~$ ps -a
  PID TTY          TIME CMD
17954 pts/1    00:00:00 wrapper-gtk24.s
17968 pts/1    00:00:03 vmware
17969 pts/1    00:00:00 wrapper-gtk24.s
18111 pts/2    00:00:00 ps

That is what i get from invoking the ps command

Which lock files would i delete , and how?

Thx for the lightining fast replies

---

### Post by Sq322 on 2006-07-18
> **Arisna said:**
> Try `**sudo** apt-get update' at a command line.  You'll have to type your password in to get admin privileges.  That will either work or give a fancier error message.

> W: GPG error: [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems

That is what the apt-get command got me

---

### Post by Arisna on 2006-07-18
That command is case sensitive--`ps -A' not `ps -a'.  Give that a shot. :)

---

### Post by Sq322 on 2006-07-18
> **Arisna said:**
> That command is case sensitive--`ps -A' not `ps -a'.  Give that a shot. :)

DOH!!
>   PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:01 kblockd/0
    9 ?        00:00:00 kacpid
   10 ?        00:00:00 kacpid-work-0
  142 ?        00:00:00 aio/0
  141 ?        00:00:04 kswapd0
  729 ?        00:00:00 kseriod
 1827 ?        00:00:00 khubd
 1844 ?        00:00:00 khpsbpkt
 1868 ?        00:00:00 knodemgrd_0
 1949 ?        00:00:00 kjournald
 2180 ?        00:00:00 udevd
 2958 ?        00:00:00 shpchpd_event
 3179 ?        00:00:00 pccardd
 3182 ?        00:00:00 ipw2200/0
 3582 ?        00:00:00 kjournald
 3751 ?        00:00:00 portmap
 4032 ?        00:00:00 acpid
 4147 ?        00:00:00 dd
 4149 ?        00:00:00 klogd
 4472 ?        00:00:00 gdm
 4488 ?        00:00:00 gdm
 4498 tty7     00:04:50 Xorg
 4515 ?        00:00:00 hpiod
 4615 ?        00:00:00 dbus-daemon
 4630 ?        00:00:12 hald
 4631 ?        00:00:00 hald-runner
 4636 ?        00:00:00 hald-addon-acpi
 4691 ?        00:00:00 hald-addon-keyb
 4711 ?        00:00:14 hald-addon-stor
 4712 ?        00:00:00 hald-addon-stor
 4731 ?        00:00:00 dhcdbd
 4748 ?        00:00:00 NetworkManager
 4762 ?        00:00:00 NetworkManagerD
 4829 ?        00:00:00 nmbd
 4831 ?        00:00:00 smbd
 4846 ?        00:00:00 dhclient
 4854 ?        00:00:00 smbd
 4855 ?        00:00:00 sshd
 4902 ?        00:00:00 xinetd
 4912 ?        00:00:00 rpc.statd
 4939 ?        00:00:00 hcid
 4944 ?        00:00:00 sdpd
 4954 ?        00:00:00 krfcommd
 4967 ?        00:00:00 mdadm
 5013 ?        00:00:00 atd
 5026 ?        00:00:00 cron
 5083 ?        00:00:00 vmnet-bridge
 5102 ?        00:00:00 vmnet-netifup
 5108 ?        00:00:00 vmnet-netifup
 5125 ?        00:00:59 vmnet-natd
 5138 ?        00:00:00 vmnet-dhcpd
 5139 ?        00:00:00 vmnet-dhcpd
 5204 tty1     00:00:00 getty
 5205 tty2     00:00:00 getty
 5206 tty3     00:00:00 getty
 5207 tty4     00:00:00 getty
 5208 tty5     00:00:00 getty
 5209 tty6     00:00:00 getty
 5590 ?        00:00:09 vmware-serverd
 8535 ?        00:00:00 apt-get
 8595 ?        00:00:00 dpkg
 8605 ?        00:00:00 frontend
 8614 ?        00:00:00 mono-apache-ser <defunct>
 8755 ?        00:00:00 apache2
 8756 ?        00:00:00 apache2
 8757 ?        00:00:00 apache2
 8759 ?        00:00:00 apache2
11232 ?        00:00:30 cupsd
11660 ?        00:00:00 syslogd
13181 ?        00:00:00 pdflush
15636 ?        00:00:00 pdflush
16555 ?        00:00:11 gconfd-2
16572 ?        00:00:00 x-session-manag
16614 ?        00:00:00 ssh-agent
16617 ?        00:00:00 dbus-launch
16618 ?        00:00:00 dbus-daemon
16621 ?        00:00:00 gnome-keyring-d
16623 ?        00:00:00 bonobo-activati
16625 ?        00:00:01 gnome-settings-
16630 ?        00:00:00 esd
16635 ?        00:00:08 metacity
16640 ?        00:00:05 gnome-panel
16642 ?        00:00:01 nautilus
16645 ?        00:00:00 gnome-volume-ma
16652 ?        00:00:00 update-notifier
16656 ?        00:00:00 nm-applet
16661 ?        00:00:00 gnome-cups-icon
16668 ?        00:00:00 gnome-vfs-daemo
16674 ?        00:00:00 trashapplet
16687 ?        00:00:00 gnome-power-man
16691 ?        00:00:00 mapping-daemon
16696 ?        00:00:00 gweather-applet
16698 ?        00:00:00 mono
16700 ?        00:00:00 gpilot-applet
16702 ?        00:00:00 gnome-netstatus
16704 ?        00:00:00 mixer_applet2
16706 ?        00:00:00 clock-applet
16712 ?        00:00:00 gam_server
16714 ?        00:00:00 gpilotd
16732 ?        00:00:00 gnome-screensav
16815 ?        00:00:52 firefox-bin
16822 ?        00:00:01 gaim
16831 ?        00:00:18 evolution
16841 ?        00:00:00 evolution-data-
16844 ?        00:00:20 evolution-excha
16852 ?        00:00:00 evolution-alarm
17922 ?        00:00:00 at-spi-registry
17932 ?        00:00:01 gnome-terminal
17933 ?        00:00:00 gnome-pty-helpe
17934 pts/1    00:00:00 bash
17954 pts/1    00:00:00 wrapper-gtk24.s
17968 pts/1    00:00:03 vmware
17969 pts/1    00:00:00 wrapper-gtk24.s
17985 ?        00:01:13 vmware-vmx
18007 ?        00:00:01 vmware-rtc
18092 pts/2    00:00:00 bash
18236 pts/2    00:00:00 ps

I am guessing to kill line 8535 and 8595 for starters...correct?

---

### Post by PriceChild on 2006-07-18
> **Sq322 said:**
> That is what the apt-get command got me

Those errors don't matter... they're just telling you that you may want to install new keys to ensure downloaded software it official.

You should now be able to safely install software by:

sudo apt-get install <<name>>

---

### Post by Sq322 on 2006-07-18
killing those two running processes got me back up and running
Thx a ton folks

---

### Post by taurus on 2006-07-18
```

sudo kill -9 8535

```
should do it...

---

### Post by PingunZ on 2006-07-18
> <username>@<username>-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

You dont have the permission to do apt-get update
so try fake administrator
```
sudo apt-get update
```

or just go to system -> administration -> synaptic

Grtz PingunZ

---

