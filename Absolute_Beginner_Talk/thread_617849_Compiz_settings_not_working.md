---
title: "Compiz settings not working"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-11-19
I had Compiz-fusion on Feisty and that worked fine.  I had the settings manager, cube, animations etc..
I then (a while back) upgraded to Gusty and I still have desktop effects like wobbly windows etc.. 
The problem is I cant seem to load the Compiz settings manager or change any of the preferences in advanced effects under appearance.
I used to be able to do all this in Feisty.
Would there be any reason that the updated would of uninstalled anything?
Is there any way  to check that i have all the features of Compiz.

I use an ATI card
Thanks in advance.

---

### Post by MegaJim on 2007-11-19
I think 7.04 used the gnome-compiz-config package, the configuration tool for compiz-fusion in 7.10 is the compizconfig-settings-manager package.  I am going to assume you know how to find and install this from the official Gutsy repositories, if you have any difficulty though please come back and say so.

---

### Post by pfwd.tech on 2007-11-19
Unfortunately i think i may need a hand.
I researched some old threads and added ... 
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
to the bottom of the sources.list

This is the bottom part of my sources.list This is where i added the eycandy in 7.04.  Should i remove these?
```
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Compiz fusion
deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse restricted #Added by software-properties
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
```
I then updated and upgraded my packages to make sure i have everything.

I'm not sure what i should do next.
I will check back in the morning. 
Thanks

---

### Post by MegaJim on 2007-11-19
Good night/morning :)

You can install compizconfig-settings-manager from the official Gutsy repositories by opening up synaptic package manager from System -> Administration -> Synaptic.

From there just search for compizconfig-settings-manager and mark it for installation.  Synaptic will handle the dependencies.

---

### Post by pfwd.tech on 2007-11-19
I thought i might have another go before i get some sleep.  i got the compiz setting manager by :```
sudo apt-get install compiz-setting
``` 
The manager opens but warns of a dbus plugin error "Dbus Failed to load" Plus i only seem to have basic settings (no animation effects).

I still can't access the compizConfig settings or the preferences on the advanced appearances option.
Anyway im getting there

---

### Post by MegaJim on 2007-11-19
I believe the compizconfig-settings-manager is launched through the System->Preferences menu, and is separate to the advanced appearances menu.  I don't recall its exact name but you should be able to work it out.

---

### Post by pfwd.tech on 2007-12-14
Sorry for re igniting this thread but I've only just got back around to playing with it.  
I now have two menu items in the preferences dropdown. One is called Compiz Settings Manger. This is has an icon of a red box.  Once clicked the managers is open but with a Dbus plugin error.
The other is called CompizConfig Settings Manager. This one will not load.
Also - as a side issue my AWN Manager for the doc doesn't want to open either.  I have never got this working.

This is my sources file:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
##################
# Compiz fusion 
#################
# For Feisty
# deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse restricted
# deb-src http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse restricted #Added by software-properties
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

```

Can you help as I don't know what I should do in order to get this to work.
Let me know if you need any more command dumps.
Thanks in advance.

---

### Post by spiderbatdad on 2007-12-14
your command should have been:```
sudo apt-get install compizconfig-settings-manger
```

---

### Post by pfwd.tech on 2007-12-14
Thanks for the reply. It didn't work however. This is the output
```

---@---:~$ sudo apt-get install compizconfig-settings-manger
[sudo] password for ----:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manger

```

---

### Post by qamelian on 2007-12-14
You've spelled manager wrong. You missed an *a*.

---

### Post by spiderbatdad on 2007-12-14
ack! my fault

---

