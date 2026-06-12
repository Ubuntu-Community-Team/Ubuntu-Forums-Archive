---
title: "synaptic--Segmentation fault (core dumped)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by itsasailboat on 2007-06-13
hi everyone,
i'm a new feisty user.  my synaptic package manager stopped working from the menu.  when i type "sudo synaptic" i get the message "Segmentation fault (core dumped)".  i tried to reinstall it with "sudo apt-get install --reinstall synaptic" but that didn't work.  one strange detail is that when i just type "synaptic" in the terminal, synaptic opens but with no root privileges, so i can't install anything.  anybody else ever have this happen?  let me know if i am leaving out important info that would be useful..i probably am.  thanks!


PS here is my sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://archive.clemsonlinux.org/](http://archive.clemsonlinux.org/) feisty main restricted

---

### Post by zvacet on 2007-06-14
```
gksudo gedit /etc/apt/sources.list
``` 

and change

deb [http://archive.clemsonlinux.org/](http://archive.clemsonlinux.org/) feisty main restricted

in 

#deb [http://archive.clemsonlinux.org/](http://archive.clemsonlinux.org/) feisty main restricted


```
sudo aptitude update
```

---

### Post by itsasailboat on 2007-06-14
thanks for the suggestion.  yeah, that source doesn't work today.  i commented it out.  synaptic still seems broken with the same error message though:  Segmentation fault (core dumped)

---

### Post by zvacet on 2007-06-14
Did you install something?Look this maybe will be helpfull  to you

[http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation]("http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation")

---

### Post by itsasailboat on 2007-06-14
i took a look at the other thread and tried those steps.  it didn't work.  and i don't have automatix.  i also tried purging and reinstalling synaptic with "apt-get".  it seemed to work, but i get the same error as before.

i did install a lot of new packages recently, while trying to get libraries for some experimental software.  is there a way to figure out which packages are causing me trouble?

---

