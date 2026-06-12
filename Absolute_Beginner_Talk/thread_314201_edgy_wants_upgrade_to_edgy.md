---
title: "edgy wants upgrade to edgy"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-12-07
hello,

when processing today's automatic updates, i got a message that said, ```
Not all updates can be installed.  Run a distribution upgrade, to install as many updates as possible.  This can be caused by an uncompleted upgrage, unofficial software packages, or by running a development version.
```

i clicked on the 'distribution upgrade' button, then it said it was "Upgrading Ubuntu to version 6.10'.

I'm already running it; why does synaptic think i need to upgrade?

-steve

---

### Post by taurus on 2006-12-07
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by stevieb on 2006-12-07
update:
```
...Hit http://packages.freecontrib.org edgy-plf/non-free Sources
Fetched 9652B in 2s (3862B/s)
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems

```

upgrade:
```
...Building tag database... Done
The following packages have been kept back:
  xserver-xorg
The following packages will be upgraded:
  gimp gimp-data gimp-python gnome-games gnome-games-data gnome-system-tools gnupg kate kcontrol kdebase-bin
  kdebase-data kdebase-kio-plugins kdepasswd kdeprint kdesktop kdm kfind khelpcenter kicker klipper kmenuedit konqueror
  konqueror-nsplugins konsole ksmserver ksplash ksysguard ksysguardd kwin libgimp2.0 libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libkonq4 vino wlassistant x11-common
  xbase-clients xorg xserver-xorg-video-all xutils
43 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 47.4MB of archives. After unpacking 8192B will be used.

```

-steve

---

### Post by taurus on 2006-12-07
You may want to run "sudo aptitude update" again or put a # in front of "http://packages.freecontrib.org edgy-plf/non-free" in /etc/apt/sources.list to comment it out...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by stevieb on 2006-12-07
sources.list
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe


# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://www.getautomatix.com/apt edgy main

deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

deb http://eric.lavar.de/comp/linux/debian/ experimental/
deb-src http://eric.lavar.de/comp/linux/debian/ experimental/

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free

```

the most recent i've added are those that have 'lavar' in them (right before #AUTOMATIX REPOS END), for my nokia 770.  maybe that's the problem?
-steve

---

### Post by taurus on 2006-12-07
Actually, it complains about the second to last line so I would comment out the last two lines in your /etc/apt/sources.list...

```

#deb http://packages.freecontrib.org/plf edgy-plf free non-free
#deb-src http://packages.freecontrib.org/plf edgy-plf free non-free

```

---

### Post by stevieb on 2006-12-07
ok, commented out the indicated lines and did sudo aptitude upgrade.  rebooted, and mouse didn't work.  rebooted again, and now everything seems to be fine.  thanks for the help!

-steve

---

