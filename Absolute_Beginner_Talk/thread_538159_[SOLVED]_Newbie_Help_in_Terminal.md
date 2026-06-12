---
title: "[SOLVED] Newbie Help in Terminal"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by vanishedchic86 on 2007-08-29
I've recently learning how to things in the terminal. I have fixed my wireless and video settings. I stopped using my laptop for a couple weeks and when I got on I realized there were updates. I had just recently messed with some coding to fix setting for my video card and everything worked. When I attempted to do the updates it told me that: 

[B]'E:Type 'sudo' is not known on line 49 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
[/B]

I've found a couple threads with a similar problem but I haven't been able to fix it. None of it worked for me. I was hoping some one could help me other wise I'm going to have to reinstall ubuntu Feisty  Fawn 7.04 and start new, which means playing with the scripts to get everything working again.

Thanks in advanced

---

### Post by bogolisk on 2007-08-29
> **vanishedchic86 said:**
> I've recently learning how to things in the terminal. I have fixed my wireless and video settings. I stopped using my laptop for a couple weeks and when I got on I realized there were updates. I had just recently messed with some coding to fix setting for my video card and everything worked. When I attempted to do the updates it told me that: 

[B]E: Type 'sudo' is not known on line 49 in source list /etc/apt/sources.list
[/B]

I've found a couple threads with a similar problem but I haven't been able to fix it. None of it worked for me. I was hoping some one could help me other wise I'm going to have to reinstall ubuntu Feisty  Fawn 7.04 and start new, which means playing with the scripts to get everything working again.

Thanks in advanced

please post the contents of the /etc/apt/sources.list file
```

cat /etc/apt/sources.list

```
and post the output

---

### Post by diatribe on 2007-08-29
you need to remove the instance of sudo on line 49 in your /etc/apt/sources.list

---

### Post by vanishedchic86 on 2007-08-29
> **bogolisk said:**
> please post the contents of the /etc/apt/sources.list file
```

cat /etc/apt/sources.list

```
and post the output

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.caguego.net fiesty-cafuego bcm43xx
deb http://ntfs-3g.sitesweetsite.info/ubuntu/fiesty main main-all
deb http://flomertens.keo.in/ubuntu/ fiesty main main-all
deb http://mirror.ubuntulinux.nl fiesty-seveas all
deb http://packages.medibuntu.org/ edgy free non-free
sudo apt-key add - && sudo apt-get update
sudo apt-get install mozilla-mplayer w32codecs
deb http://packages.medibuntu.org/ edgy free non-free

```

---

### Post by bobplano on 2007-08-29
you need to get rid of these two lines near the bottom:

sudo apt-key add - && sudo apt-get update
sudo apt-get install mozilla-mplayer w32codecs

---

### Post by vanishedchic86 on 2007-08-29
> **bobplano said:**
> you need to get rid of these two lines near the bottom:

sudo apt-key add - && sudo apt-get update
sudo apt-get install mozilla-mplayer w32codecs

and how would I do that? I understand you delete them but what's the code to get in to change it?

---

### Post by rsambuca on 2007-08-29
```
gksudo gedit /etc/apt/sources.list
```

Just delete the lines, press save, and close

---

### Post by vanishedchic86 on 2007-08-29
that worked thanks

---

