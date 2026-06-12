---
title: "insurance post about extended partition"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2007-03-14
i did a fresh install  of edgy from the cd and did default settings

i have a  extendedpartition (hda2) that is 1.59 gig
i have been reading and with just Ubuntu on the drive i think i do not need that partition and could use qtparted to recover the space?
qt parted shows 

hda1 active  with 37 gig of space
hda2 extended 1.59 N/A for used space
hda5  swap   1.59    0 used
and fdisk shows
  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4791    38483676   83  Linux
/dev/hda2            4792        4998     1662727+   5  Extended
/dev/hda5            4792        4998     1662696   82  Linux swap / Solaris

it is only 1.59 gig so i can keep it but hate to see it just sitting there;-)

no dual boot or anything just 100% UBUNTU on it 

ps i now turn on my windows box once a week to do my anti-spyware a/v updates
and then turn on and get back on my Ubuntu
thanks for any advice

---

### Post by yabbadabbadont on 2007-03-14
It isn't "just sitting there".  It contains your swap partition, hda5.

---

### Post by dhughes on 2007-03-14
You may want to consider, if you reinstall your OS that is, making a separate partition for /home.
 
 You've got everything piled into just one partition, you don't have a lot of room but it's a good idea just to be safe and it will make it easier if you have to wipe your OS or install a new distribution.

---

