---
title: "Total Newbie slaughtered by DEPENDENCY errors"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2006-04-21
I've been attempting several different ways of installing opera. But every time I try I run into dependency errors. This happens when I run the Update Manager as well.

The errors involve:
malix
mutt
lbs-core
lbs-graphics
lbs-cxx
lbs

here are the exact messages from the terminal when I try: sudo apt-get -f install
> invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can anyone help?
](*,)

---

### Post by jorn on 2006-04-21
Do you install from synaptic?

---

### Post by mjm115 on 2006-04-21
[QUOTE=mlhudson]I've been attempting several different ways of installing opera. But every time I try I run into dependency errors. This happens when I run the Update Manager as well.

The errors involve:
malix
mutt
lbs-core
lbs-graphics
lbs-cxx
lbs

here are the exact messages from the terminal when I try: sudo apt-get -f install


Can anyone help?
](*,)[/QUOTE]

Add the following line to your source.list:

> deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

Then do

> 
sudo apt-get update
sudo apt-get install opera


---

### Post by mlhudson on 2006-04-21
Are you asking about whether I tried to install Opera synaptic? if so, the answer's no. I tried to use the wiki that told how to use adding an opera link to your sources.list and then sudo apt-get update and sudo apt-get install opera.

Would using synaptic fix my dependency errors?

---

### Post by gingermark on 2006-04-21
Synaptic is a frontend for apt-get - they're pretty much the same thing.

Those errors seem very odd. Have you installed anything else that might've caused them? You might want to post your sources.list file (located in /etc/apt) - there might be a problem with that that is causing the errors.

Maybe.... :)

---

### Post by mlhudson on 2006-04-21
Here's my sources.list:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

---

### Post by mlhudson on 2006-04-21
looking at that list for the first time outside of GEdit, I see that I'm using http:gb....
I'm in the US. Does that matter?

---

### Post by timsch75 on 2006-04-21
No.  Physical location may only result in slower transmission.  Use Synaptic, for sure.  Search the forum on how to enable multiverse/universal repositories.  There should not be a problem installing opera.  Plugins for opera will be a bit more work.  I'm using opera with Ubuntu and have no recollection of any installation issues using Synaptic

---

