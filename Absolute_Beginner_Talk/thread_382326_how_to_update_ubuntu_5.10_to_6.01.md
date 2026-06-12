---
title: "how to update ubuntu 5.10 to 6.01?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-03-11
So I started poking around and I found this:
cloud@cloud:~$ cat /etc/apt/sources.list

It shows me that I am not updated to Ubuntu 6.01 etc....great.... how do I do that? 

[COLOR="Blue"]cloud@cloud:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
[/COLOR]

---

### Post by Kateikyoushi on 2007-03-11
Read this page it explains the ways to upgrade. [LINK]("https://help.ubuntu.com/community/UpgradeNotes")

---

### Post by gotquestions on 2007-03-12
I tried updating and I got problems. When i load the new kernel it just hangs. I gave up :(

So what I did was I took my friend's ubuntu 6.10 and boot from this disc. i hit to install and I got this message.

Out of range signal
Cannot display this video mode.
change computer display input to 1900x1200 ....

I cant install! help

---

### Post by Kateikyoushi on 2007-03-12
Did you try the safe video mode ?

---

### Post by gotquestions on 2007-03-12
yes i tried safe video mode too and that failed also on that ubuntu 6.10 cd .

---

