---
title: "Can't find &quot;lamp-server&quot; package"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Sammi on 2007-06-29
Hi,

I just installed Ubuntu 7.04 Desktop. I've updated the installation and added all the universe and multiverse repositories, but I can't install the lamp-server meta package, because I can't find it.

```
$ sudo aptitude install lamp-server
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "lamp-server"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

This is my sources.list
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://fo.archive.ubuntu.com/ubuntu/](http://fo.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

Am I doing something wrong?

---

### Post by Skrynesaver on 2007-06-29
I know not of this lamp-server package of which you speak.
**L**inux =>Check
**A**pache webserver =>install it 
**M**ySQL => Install it
**P**erl, **P**ython or **P**hp => install and install the mods for apache

Tada, a LAMP stack

---

### Post by Sammi on 2007-06-29
Then ubuntuguide.org is incorrect.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ubuntu_Feisty_LAMP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ubuntu_Feisty_LAMP_Server)

---

### Post by Sammi on 2007-06-29
How did this get in to Ubuntuguide.org in the first place? Was there ever a lamp-server meta package for older versions of Ubuntu?

---

### Post by Johnathon on 2007-06-29
**Massive edit:** have you tried using ```
 aptitude install lamp server
``` with the space, instead of with a dash?

There is a "task" to install the Lamp (apache, mysql, perl & php.. python already installed) stack available through aptitude, but you have to use the words with a space.

**Even bigger edit:**
If that doesnt work, type the command "sudo aptitude" into a terminal, and it will load the text-based interface for aptitude. Go down to tasks, hit enter. Scroll down the tasks till you get to "lamp server", and then hit "+". Once you're sure you're ready, hit "g". It will ask you to confirm you want to install, hit "g" again, and it will begin installing.

---

### Post by NumberOne on 2007-06-29
The lamp server option is on the server iso.  I installed the server with the lamp option, then installed the desktop.

---

