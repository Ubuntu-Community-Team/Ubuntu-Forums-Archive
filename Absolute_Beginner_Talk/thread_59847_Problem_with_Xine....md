---
title: "Problem with Xine..."
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2005-08-25
Hi,
I watched a few DVDs in Xine. It is working. 
But I just put in this DVD to watch, and I got an error:

 The source can"t be read.  Maybe you don"t have enough rights for this, or source doesn"t contain data (e.g: not disk in drive). (Error reading NAV packet.)

Even though other DVDs work, this one gives this error.

Can someone help???

---

### Post by Kapre on 2005-08-25
[QUOTE=ROUBOS]Hi,
I watched a few DVDs in Xine. It is working. 
But I just put in this DVD to watch, and I got an error:

 The source can"t be read.  Maybe you don"t have enough rights for this, or source doesn"t contain data (e.g: not disk in drive). (Error reading NAV packet.)

Even though other DVDs work, this one gives this error.

Can someone help???[/QUOTE]

Roubos - is this DVD a backup or original? I'm also having this kind of error on my backup discs (not all of them though). I think the problem stems on how it was burnt and not problem with Xine. 

BTW, i'm using GXine.

K

---

### Post by ROUBOS on 2005-08-25
It's an original. I rented it. It's the original copy. Not a backup.
All other DVDs I've tried to watch worked fine

---

### Post by aysiu on 2005-08-25
Can we assume that you've already installed libdvdcss2?

---

### Post by ROUBOS on 2005-08-25
I can't install that for some reason

$ sudo apt-get install libdvdcss2 

gives me:

Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by aysiu on 2005-08-25
Did you do this

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

before doing this

[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

?

---

### Post by ROUBOS on 2005-08-25
yes,

here it is:


deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#####################

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by KingBahamut on 2005-08-25
Shouldnt there be matching deb entries for the deb-src entries that dont have one?

---

### Post by ROUBOS on 2005-08-25
OK

I copied back my source list backup .. so now it's looking like this

what changes should I make??

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted

deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by Lord Illidan on 2005-08-25
I think he means that you have to put in this repo too..

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

and a word of advice..

if apt-get gives u problems, they are easier to solve in Synaptic, especially if you have to force versions and stuff.

---

### Post by ROUBOS on 2005-08-25
I cant find libdvdcss2 in the Synaptic Package manager

---

### Post by Lord Illidan on 2005-08-25
Try including this too..

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary main restricted

---

### Post by ROUBOS on 2005-08-25
no luck :?

---

### Post by Lord Illidan on 2005-08-25
Then try backing up the sources.list and replace everything with the repos in the ubuntu guide..

---

### Post by ROUBOS on 2005-08-25
tried that... same :(

Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

