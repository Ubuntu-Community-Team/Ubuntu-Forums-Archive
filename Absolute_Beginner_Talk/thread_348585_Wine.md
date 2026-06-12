---
title: "Wine"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by shawn fernandes on 2007-01-29
I typed this in my terminal:
 apt-get update
I got this as reply:
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
I also typed this :
apt-get install wine
Reply was:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

What does this mean? How do I solve it?

Thank you.

---

### Post by meng on 2007-01-29
sudo apt-get install wine
enter your user password when prompted

---

### Post by shawn fernandes on 2007-01-29
E: Type 'wget' is not known on line 58 in source list /etc/apt/sources.list
E: Unable to lock the list directory

What does this mean?

---

### Post by Denn1s on 2007-01-29
have you edited your sources.list? if you don't know wath this is you probably havnt,
try: ```
sudo nano /etc/apt/sources.list
``` and post the output and we will tell you how to fix this

---

### Post by shawn fernandes on 2007-01-29
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
                               [ Read 56 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

Now what to do?

---

### Post by machoo02 on 2007-01-29
There's a problem in your sources.list file on line #58, which is below what you pasted in your last post.  Try this instead:
```
gksudo gedit /etc/apt/sources.list
``` and post the contents of the entire file here.

---

### Post by shawn fernandes on 2007-01-30
shawn@shawn-laptop:~$ gksudo gedit /etc/apt/sources.list

(gksudo:7594): Gdk-WARNING **: locale not supported by Xlib

(gksudo:7594): Gdk-WARNING **: cannot set locale modifiers
(gedit:7595): Gdk-WARNING **: locale not supported by Xlib

(gedit:7595): Gdk-WARNING **: cannot set locale modifiers

(gedit:7595): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave


deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
# Repository for wine
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free


What do I have to do?

---

### Post by ultima on 2007-01-30
Are you sure that is the whole file I only count 53 lines

---

### Post by machoo02 on 2007-01-30
The last thing that you have listed in your file (according to your post) is:> # Repository for wine
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
The 'deb' line that you have here is in your list twice...the packaging program does not like to have duplicate lines like that.  In addition, that is not the official repository for Wine.  Open up your sources.list file as I described before, and paste over the lines that I have quoted above with```
## Latest WINE packages from WineHQ
deb http://wine.budgetdedicated.com/apt dapper main
```

Save and close the file, then 

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wine
```Hopefully that will do the trick.

---

### Post by jkeyes0 on 2007-01-30
Stupid question, but you don't have Synaptic package manager or another apt-get session up, do you?

---

