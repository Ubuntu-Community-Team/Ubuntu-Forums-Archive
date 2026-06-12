---
title: "Please help me with CDEMU"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by xxrealmsxx on 2007-07-18
Guys,

I am trying to use CDEMU to mount some images I have. The goal is to install some games through wine but I have misplaced the CD's.

I got CDEMU installed correctly but I can't seem to mount the images.

Here is what I am looking at and I am a bit perplexed:

realms@realms-desktop:~$ cdemu -s
Drive Loaded Comment
  0:     1   RZR-WC3.CUE
  1:     0   NO_CD_LOADED
  2:     0   NO_CD_LOADED
  3:     0   NO_CD_LOADED
  4:     0   NO_CD_LOADED
  5:     0   NO_CD_LOADED
  6:     0   NO_CD_LOADED
  7:     0   NO_CD_LOADED

realms@realms-desktop:~$ sudo mount -t iso9660 /dev/cdemu/0 /media/iso
mount: special device /dev/cdemu/0 does not exist

I don't really get it :( but I need to figure it out because I have .cue and .bin files not .iso's.

Thanks in advance.

---

### Post by xxrealmsxx on 2007-07-18
Problem solved by following this: [http://ubuntuforums.org/showthread.php?t=276743](http://ubuntuforums.org/showthread.php?t=276743)

---

