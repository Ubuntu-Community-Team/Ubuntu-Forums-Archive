---
title: "help w/ running ubuntu from an sd card"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Watchtow3r on 2007-12-09
I'm trying to put ubuntu onto a 2 GB sd card. I've been using [these]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") instructions. Firstly, the instructions for a usb drive would be the same as one for an sd card, right?  OK, so here's my problem: I typed sudo su in the terminal. I typed fdisk -l. It says note which device is your flash drive, then it gives an example: /dev/sda. Here's what my terminal looked like after I typed that:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ae1ea1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13786   110736013+   7  HPFS/NTFS
/dev/sda2           13787       14593     6482227+   7  HPFS/NTFS

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984     1983619+   7  HPFS/NTFS

It looks to me like it's saying that my sd drive is mmcblk0, which doesn't look anything llike the sda example that they gave. I wouldn't know how to use this for the rest of the steps. Unless it's one of the sda1 or sda2 devices? How do I know which one is the SD card? Thanks.

---

### Post by Arthur Archnix on 2007-12-09
I think you're right that the mmc one is your sd card. One way you can check it by opening the card. See where it's mounted, maybe /media/mm* and try and create a directory there with 'mkdir test'. Or if you can see it on your desktop right-click on it and see what device it is and where its mounted.

At a minimum, your computer will need to be able to boot from the SD card for this to work.

---

### Post by Watchtow3r on 2007-12-09
Sorry, but I'm still not sure how to tell where it's mounted. I right-clicked on it, but all it says that looks useful is something under Volume that says Mount Point: /media/TIM'S (my name) and a lot of things listed in Mount Options. Also, in Volume, in Media it says SecureDigital/MultiMediaCard.

---

### Post by Arthur Archnix on 2007-12-09
So, multimediacard... and you have a device called mmc. Pretty safe bet that that's your monster right there. Just unplug it though then do another fdisk. If the mmc is gone, that's the target alright.

---

### Post by Watchtow3r on 2007-12-09
yeah... thanks I got it now. The only problem is, that in [this]("http://ubuntuforums.org/showthread.php?t=635738") post, I explain that I was trying to use the sd card, but I messed up so I reformatted it... Now when I access the fdisk -l thing it looks like I messed something up. can someone help me out please? and btw thanks for your help so far.

---

### Post by Arthur Archnix on 2007-12-09
Well, you should try to keep things in one post so that people can follow your problems easily. Why not post the command you typed to format the sd card, then ask a moderator to merge the threads so we can easily see your error message as well.

I did notice that there are a bunch of partitions on that media card. So, you'll have to be sure to give the right command that wipes it all clean.

---

