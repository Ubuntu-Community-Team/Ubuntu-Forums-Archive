---
title: "Gutsy Install Help!!"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by borovy3488 on 2007-10-13
OK, so I am trying to upgrade from feisty to gutsy as we speak.  So far, I have gotten two errors. Both on how it couldn't install something.  The first one was the tzdata package, and the other one was the util-linux.  What will this do to my install?  It is still working and installing everything.  What do I need to do once it's done??

Thanks,
Wayne

---

### Post by Martje_001 on 2007-10-13
> **borovy3488 said:**
> OK, so I am trying to upgrade from feisty to gutsy as we speak.  So far, I have gotten two errors. Both on how it couldn't install something.  The first one was the tzdata package, and the other one was the util-linux.  What will this do to my install?  It is still working and installing everything.  What do I need to do once it's done??

Thanks,
Wayne
Just reboot and look what it does. If the X server fails for some reason (common after a upgrade) do:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by spiderbatdad on 2007-10-13
I burned an iso of Gusty and made a clean install. I also let the partitioner save Fiesty in it's own partion so I wouldn't loose it. When it's all done, you can access your folders in Fiesty labeled as a (certain size) volume under Places-->Computer-->18GB Volume... or whatever size it says the volume is.

---

### Post by llamakc on 2007-10-13
Before you reboot, open a terminal and run:

```

sudo apt-get -f install

```

Just in case any packages didn't get configured. I would also run:

```

sudo apt-get update && sudo apt-get dist-upgrade

```

I moved up to Gutsy a few days ago with `sudo update-manager -c -d` and remember there being a few glitches like you mentioned. I'm currently using it with no problems. Both of those packages are properly installed on my rig:

```

ken@llamakc 08:49:34:~$ dpkg -l | grep util-linux
ii  util-linux                                 2.13-8ubuntu1                         Miscellaneous system utilities
ii  util-linux-locales                         2.13-8ubuntu1                         Locales files for util-linux
ken@llamakc 08:49:45:~$ dpkg -l | grep tzdata
ii  tzdata                                     2007f-3ubuntu1                        time zone and daylight-saving time data

```

HTH.

---

### Post by skompier on 2007-10-13
Are you installing via update -d in a terminal window? If so, I tried the same method and had several errors. I don't remember which, but it's never something that you want to see.

I went ahead and finished the update and rebooted. I was able to get to the desktop on reboot, but had problems with setting resolution and some update manager was hosed. I found a solution on the forums to fix that but I gave up, reinstalled 7.04 and decided to wait until the release.

I had a wild hair and d/l the RC, wiped my Linux partition and did a fresh install of the RC from CD and had no problems.

---

### Post by borovy3488 on 2007-10-13
OK guys, I'm not really sure what happened.  It said that the upgrade did not finish.  So, I just restarted my computer because my avant windows navigator wasn't working anymore (it uninstalled it) and I couldn't navigate windows.  Also, my Beryl got uninstalled so I had not borders on the windows to move them, close them or whatever.  After the restart, my user looked exactly the same. Nothing worked.  Now, I have created a new user and everything seems to be working fine.  In fact, there are some cool new features.  Yes, it does look like gutsy was somewhat installed.  I even got the Welcome to Ubuntu 7.10 thing when I opened firefox.  My question is, what do I need to do to make sure everything works??  Here is a list of all the errors I received during the upgrade attempt::

tzdata error
subprocess post-installation script returned error exit status 10


util-linux error
dependency problems - leaving unconfigured

util-linux-locales
dependency problems - leaving unconfigured

locales
dependency problems - leaving unconfigured

language-pack-en-base
dependency problems - leaving unconfigured

language-pack-en
dependency problems - leaving unconfigured

language-pack-gnome-en-base
dependency problems - leaving unconfigured

language-pack-gnome-en
dependency problems - leaving unconfigured

sun-java6-jre
dependency problems - leaving unconfigured

sun-java6-bin
dependency problems - leaving unconfigured

sun-java6-plugin
dependency problems - leaving unconfigured

ubuntu-minimal
dependency problems - leaving unconfigured

update-manager failed to install or upgrade

tz-data failed to install or upgrade

Upgrade Failed

Any ideas on what happened??

---

### Post by borovy3488 on 2007-10-13
Yes, I did update via update -d in the terminal.

---

### Post by Pumalite on 2007-10-13
Save data and do a clean install in 5 days.

---

### Post by llamakc on 2007-10-13
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) shows the recommended upgrade paths.

If you can get a terminal open, run: 

```

sudo apt-get -f install

```

and see if it processes those packages.

---

### Post by borovy3488 on 2007-10-13
Here's what I got after I ran that command::
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 sun-java6-jre
 sun-java6-bin
 util-linux-locales
 ubuntu-minimal
 sun-java6-plugin
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by llamakc on 2007-10-13
So, do you have ONLY Gutsy lines in your /etc/apt/sources.list, or do you have leftover 3rd party lines from your Feisty install?

---

### Post by borovy3488 on 2007-10-13
It looks like everything is working fine as of now.  What do I need to do to erase the other user and move all of those files over to this user?  Is there any way this is possible??

---

### Post by borovy3488 on 2007-10-13
Just checked the sources.list, and yes there are still 3rd party lines from my feisty.  What is the deal with that?

---

### Post by llamakc on 2007-10-13
Are they commented out, or are they not?

---

### Post by borovy3488 on 2007-10-13
Here is an exact copy of my sources.list:::

# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

## Avant Window Navigator
# deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by Gholas on 2007-10-14
I was getting this exact same error.  After some digging around, I found a bug report which tells how to fix the problem with tzdata.

[https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/116193](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/116193)

You basically have to change your timezone to "Europe/Berlin" and then 

sudo dpkg --configure -a

It was then able to configure all the broken packages.

---

