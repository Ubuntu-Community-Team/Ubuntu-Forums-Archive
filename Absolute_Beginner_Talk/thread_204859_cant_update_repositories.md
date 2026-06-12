---
title: "cant update repositories"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by njzillest on 2006-06-27
I cant update my Repository list. In Synaptic, it sais i have a 1200 links. I Used to have alot more. 

Here is the list of my /etc/apt/sources.list 

 ```
njzillest@njzillest:~$ cat /etc/apt/sources.list.save
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe mul tiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted univers e multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted uni verse multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted m ultiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe m ultiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
## created by arniewinechanged

```

---

### Post by shoot2kill on 2006-06-27
follow this link... use source-o-matic to create a fresh sources.list

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Dr. Nick on 2006-06-27
look at the word "multiverse" it has spaces in it in a few spots, it should be all one word

not sure if that is the only problem though.

sudo "apt-get update" or synaptic should throw some errors with them like that though.

---

### Post by njzillest on 2006-06-27
thanks alot.. I got the sources from that site you gave me :-) 

I tried gedit /etc/apt/sources.list 
it wont let me edit the files

I also tried VIM.

How can i edit the sources??


thanks alot in advance ;-)

---

### Post by njzillest on 2006-06-27
lol nvm i just had to type sudo 


well now it did it nd it still doenst work... 

Is there any way to restore my comp without a clean install?

---

### Post by Dr. Nick on 2006-06-27
post your new sources.list and then the procedure you use to update it.

When you say it wont update does it give you a specific error message?

should only require to save the new sources.list file and run

sudo apt-get update

Or opening synaptic and hit refresh/reload.

---

### Post by 3rdalbum on 2006-06-28
You have quite a few 3rd party repositories there. Some 3rd party ones don't actually work; maybe one of those is giving you the error.

---

