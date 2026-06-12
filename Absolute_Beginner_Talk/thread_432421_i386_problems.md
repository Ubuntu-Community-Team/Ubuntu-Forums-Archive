---
title: "i386 problems"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by richmellis on 2007-05-04
Hello,  I am brand new to Linux Ubuntu and in the process of downloading through the Add/Remove Applications, but under the descriptions for many of the programs, I get the following message: "[application] cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type." Can someone point me to where I need to go to correct this or to at least get some info?  Thanks!

---

### Post by teddybairs1 on 2007-05-04
What are your system specs? What apps are you trying to install? The Add/Remove program should be tied to the i386 repositories for your distro.

---

### Post by richmellis on 2007-05-04
Thanks for the reply.  I am using a Dell Inpiron 600s0 laptop with Intel Pentium M 2.0 gb Graphics .card is ATI Radeon Mobility x300 128mb.  The original file system under windows xp was ntfs.  I was trying to get the codecs for the Totem movie player and the Rhythmbox player.  Thanks!

---

### Post by Acglaphotis on 2007-05-04
[I posted here my fix]("http://ubuntuforums.org/showthread.php?t=433355").

-Acgla

---

### Post by richmellis on 2007-05-06
I am new to using the Terminal.  I don't understand the use of comment and uncomment.  When I enter the sudo gedit /etc/apt/sources.list command in terminal, I get the following(it is long: what do I do next to "comment"?  thanks for helping!
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-updates main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-security main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-security main restricted
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-security universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-security universe
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-security multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) feisty-security multiverse

---

### Post by teddybairs1 on 2007-05-07
"comment" and "uncomment" refer to the # in front of each of the lines. It also referred to as "remark". It's talking about when you want to actually add text into the body of program code for FYI without it trying to run it as program code.

Each of the lines with a # in front of it has been "commented", meaning that these are developers' comments or FYIs, and the maching will ignore these and go to the next line without a # in order to try and execute it as code. In order to tell it to ignore a line you stick a # in front of it, and in order to tell it to execute a line you remove the #.

---

