---
title: "wanna add ubuntustudio package"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-06-19
wanna add ubuntu studio package in my exeisting ubuntu feisty distro and i got this message in the synaptic window.....what should i do ??? TIA !

---

### Post by Seisen on 2007-06-19
Post your source list, you might not have the universe repos.

---

### Post by p_quarles on 2007-06-19
I imagine you're getting that message because synaptic can't find the supercollider package on any of the repositories you have enabled. Do some searching for the correct repo, add it, and then try again. That's all I can think of.

---

### Post by gprok on 2007-06-19
sry im a little new at linux...what is my source list ????


what should i type for my search on repo ???

i know that as something to do with supuercollider cause the process stopped when trying to get supercollider  TIA

Gprok

---

### Post by Seisen on 2007-06-19
Put this in the terminal

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by gprok on 2007-06-19
there is the source i found it wwow...

gprok

---

### Post by Seisen on 2007-06-19
Post a screenshot of what it says under the Ubuntu Software tab.

---

### Post by p_quarles on 2007-06-19
Cool. Now, highlight the "Ubuntu software" tab and give us another screenshot.

EDIT: Curses. Seisen beat me to it. :-)

---

### Post by gprok on 2007-06-19
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

---

### Post by gprok on 2007-06-19
there

---

### Post by p_quarles on 2007-06-19
Well, it should work. Try opening up synaptic, and running a "search" for supercollider. It came right up for me, and you have the correct repo for it.

---

### Post by gprok on 2007-06-19
when i try to select it to install it i got this ::::

i got a AMD64 3000+ processor maybe thst why ???

thanks soooo much for your help quarles

---

### Post by p_quarles on 2007-06-19
> **gprok said:**
> when i try to select it to install it i got this ::::

i got a AMD64 3000+ processor maybe thst why ???

thanks soooo much for your help quarles
You got me there. I recall hearing something, though, about a particular version of the Linux kernel that's required for Studio. I guess if I were you, I'd try to run the Ubuntustudio live DVD, and see if it works on your system.

---

### Post by gprok on 2007-06-19
there is no live dvd..i have to install it....i dont want to do that cause i like my feisty stable distrop at the moment and all i need is a few appz like ardour and jack tool...i dont need all that package really.....just a few apps to get me start with music making.......thanks soo much man....if you have another suggestion dont hesitate...im stuck hehehehehe

Gprok

---

### Post by p_quarles on 2007-06-19
I've got one last idea (you may have already tried this, though): On the Ubuntu studio support pages they have a script for upgrading "vanilla" Ubuntu. You can get it here:
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty)

Dunno if it'll work, but good luck.

---

### Post by gprok on 2007-06-19
ok Quarles i'll give it a shot.......ardour is allready install but cant run it cause i need jack first and i dunno at the moment how to run the server jack....im working on it

Gpeok

thanks m8

---

