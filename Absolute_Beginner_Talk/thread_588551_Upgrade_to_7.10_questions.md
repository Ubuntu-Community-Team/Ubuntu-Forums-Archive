---
title: "Upgrade to 7.10 questions"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Snoopy1966 on 2007-10-23
Hello everyone

I did the upgrade to Gutsy and everything went pretty good Alhamdulilah.  I think some of my repos are not correct.  This is my sources list
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://ftp.debian.org sarge main
# deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
# deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

#Ubuntu Muslim Edition
deb http://www.ubuntume.com/repository feisty main #Ubuntu Muslim Edition
#siahe.com
deb http://siahe.com/zekr/apt feisty main #siahe.com
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main multiverse universe

ahmed@ahmed-desktop:~$ 
```

I get this error for a partial update -  slanga1a-utf8 unauthorized package

I have Compiz fusion kinda working, but I can not get the cube to work.  I am using the restricted driver for my ATI Radeon 9800 
I have successfully had Beryl running before, and I have tried all the settings in Advanced Desktop Effects.  

I have been running Linux for about a year now but I still struggle at these things.  Any help would be greatly appreciated.

---

### Post by Daveth on 2007-10-23
how did you upgrade- from dapper, to feisty, then to gutsy? And was your range of repositories as broad as that when you did upgrade? Looks like you should have dropped down to the core ubuntu set for your upgrade path. I see some feisty repos there, so it looks like a gutsy-feisty hybrid rather than pure bred gibbon!

---

### Post by Snoopy1966 on 2007-10-23
Thanks for the reply,
I did the upgrade through the system update.  I did a clean install of Fiesty from CD.  Should I download the CD for Gutsy and install again?  I did an update to Ubuntu Muslim Edition before the upgrade to Gutsy.  Is there any hope for me??  

How do I get the cube to work in Compiz fusion??  All I get is a screen that flips over now instead of a cube.  No mouse wheel activated cube rotate.

---

### Post by Snoopy1966 on 2007-10-23
I also get this error when doing the system update.  I forgot to add this part.  This may help my problems.  I do not know how to get the public key

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277

---

### Post by rsambuca on 2007-10-23
You have a debian repository mixed in there, which will definitely cause you problems.  Comment out this line in your sources.list:

deb [http://ftp.debian.org](http://ftp.debian.org) sarge main

---

### Post by rundee_f on 2007-10-23
my upgrade proccess to 7.10 always stopped at the 2nd stage (modifying the software channel),,, errors occured said 'MD5Sum mismatch'... what's wrong? what should i do?

---

### Post by Snoopy1966 on 2007-10-23
@ rsambuca  Thanks for the reply.

Should I remove the fiesty repos for the avant window manager as well?  How about the software channel?  Is there anything I should modify in that?

@  rundee_f

I am not an expert at this but it sounds like you have a bad hash tab.  Did you verify it with the checksums they have posted on the download page??  I think you will have to download the ISO again and make sure you have a correct MD5 sum
Someone else may know the name of the program to check it.  I always download from bit torrent so you know you have a good copy.  I hope that helps some

---

### Post by rsambuca on 2007-10-23
> **Snoopy1966 said:**
> @ rsambuca  Thanks for the reply.

Should I remove the fiesty repos for the avant window manager as well?  How about the software channel?  Is there anything I should modify in that?



You don't have to, they are already commented out by the '#'.

---

### Post by rundee_f on 2007-10-24
nope.. ive figured that my local server was the source of my problem.. ive changed it to main server and everything works well... :)

---

