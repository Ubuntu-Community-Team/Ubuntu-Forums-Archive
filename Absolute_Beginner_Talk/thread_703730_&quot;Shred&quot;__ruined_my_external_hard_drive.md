---
title: "&quot;Shred&quot;  ruined my external hard drive"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by jbrown96 on 2008-02-21
I recently constructed my own tinfoil hat to wear, fearing for my privacy. Naturally, this security paranoia spilled over into computing, and so I tried to encrypt/secure all of my data. I "shreded" my internal HD and external HD, using
```
shred -z /dev/sdb1
```
for the external. The whole thing took forever (250GB drive), but it seemed to work. I also got a new computer with much more storage, so the external HD hasn't had much use, so it remained "shreded." 

This is where the problem began. My DVD player has a USB port and a really cool feature where it can play movies (almost any format you can throw at it) on a USB flash drive. I figured out that any USB drive will work as long as it has a FAT32 partition as the first partition. This is a great feature because I don't have to burn discs.The problem is that the DVD player does not recognize the HD anymore, no matter how I try to format it.

Did the shred command somehow erase information that the player needs to read it?
The drive works fine in Ubuntu, and I only put a FAT32 partition that is less than 10GB on it because I remember that FAT32 doesn't like partitions that are too big.

---

### Post by ByteJuggler on 2008-02-21
Well it's hard to say... 

Plug in the external disk to your PC and boot up Ubuntu.  Press alt-f2 and enter (or copy/paste):

```
gksudo fdisk -lu >/tmp/fdisk.txt; gedit /tmp/fdisk.txt
```

Copy the resulant output in the editor that opens here.  Then, repeat the process with a usb key/disk that does work with the player so we can see partition information for it too.  That might give us a clue.

---

### Post by beatryder on 2008-02-21
The problem could be you DVD player not being able to recognize a disk that large.

Do you have a smaller HDD to test with, something in the 40-80GB range.

---

### Post by seventhc on 2008-02-21
The player may have had software that enabled it to play "(almost any format you can throw at it)" but if that were the case, I would think they would give you a disk with the program that you need.
Is there a hidden partition on it somewhere? Like a recovery partition?

---

### Post by jbrown96 on 2008-02-25
Thanks for the help, but I think it may be the DVD player. I used a 256MB flash drive (unfortunately, I had to format it first) and erased all partitions on my external and created a 1GB FAT32 partition. The DVD player does not recognize either. That means either Ubuntu is doing something crazy or the DVD player is broken. I think the second is more probable. Thanks for all the help.

Just for reference it's a Philips DVP 5960, which worked amazing until this.

---

