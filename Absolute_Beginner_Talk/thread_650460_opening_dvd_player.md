---
title: "opening dvd player"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by apple pie maker on 2007-12-26
Problem: Can't open dvd drive when it's empty...Similar problem was described by thinsoldier and stixy...I have XP and Gutsy on separate hard drives, and I have a cd-rom and a dvd writer, both internal and behind doors...In "Hardware" both drives are listed and recognized...When I highlight the dvd in "Computer", open a terminal, and type "eject" the cd-rom opens instead. When I right click on either icon and click "eject" the message returned is "Can't do this/Probably there is no media." (Duh!) Can't close the cd-rom either, except by pushing the drawer. (Too much manual labor!)..So I use XP to open the drives and then reboot to Gutsy - some workaround! Any ideas on how to make this work better? Thanks

---

### Post by bone2006 on 2007-12-26
Try opening up a navigate to /media directory and eject the one you want to eject:

Here's how I'm ejecting mine via the terminal  

$ cd /media/
a$ ls
cdrom  cdrom0  cdrom1  hda1
$ eject cdrom
$ eject cdrom1

OR
type in the terminal lshw and you can see where your devices are:

For instance I see:

              *-cdrom
                   product: LITE-ON DVDRW SOHW-1633S
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb

I then type in eject /dev/hdb and it opens

hope this helps

---

### Post by SR_ELPIRATA on 2008-03-03
Im having this problem as well, but unlike Apple Pie Maker... my drive wont show up on the Hard Drive list.

Its a Lite ON DVD, but what is surprsing is that it works IF I boot up ubuntu with a CD or DVD in it. If I dont.... it wont open nor be listed on the Hardware list.

I have another weird thing happening, whenever I put a CD or DVD in it mounts it but as:

/media/BLACK_HAWK_DOWN (a DVD, which btw works well, VLC plays it fine)
/media/Ubuntu... (as in the ubuntu live cd)

Whenever you try and see both /media/cdrom and /media/cdrom0 it will never show any information related to any of the above examples.

SR_ELP

---

