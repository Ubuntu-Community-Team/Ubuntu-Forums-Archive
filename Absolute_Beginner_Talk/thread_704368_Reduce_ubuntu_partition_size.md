---
title: "Reduce ubuntu partition size"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by AlanBigBird on 2008-02-22
I have a dual boot system. It had windows on it first on a 40 gig drive. I added a 250 gig drive to the system and installed Ubuntu on it giving it the entire 250 gig. I now need more space for my windows system. I would like to resize the Ubuntu partition to a smaller size and then create a partition on the 250 gig drive for my windows system.  How can I do this?

---

### Post by webjames on 2008-02-22
I think the easiest way to do this would be to boot up the live cd and then install gparted and use that to shrink the partition. By using the live cd you don't need to worry about the partition being mounted.

```
sudo apt-get install gparted
```

you can then shrink the partition, and create a fat,ntfs partition for windows.

please _REMEMBER_ although it is unlikely, should something to go wrong it's always nice to have a backup. So **backup** before attempting this.

---

### Post by laidback on 2008-02-22
You can get a Gparted Live CD, really useful to have anyway, Google for Gparted.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by AlanBigBird on 2008-02-22
Thanks everyone I booted using my disk and then used gparted to changes the size of the Ubuntu partision.  Now I can't seam to get windows xp to reconize the other drive so that I can add a partition.  Do I need to create the partision using gparted but formated for windows?  Any suggestions?

---

### Post by AlanBigBird on 2008-02-22
I know this is a little off the subject but how do I get the command prompt to open up. I know unix but I can't seam to find how to open a screen in ubuntu so that I can use the command line.

---

### Post by laidback on 2008-02-22
Command prompt...Applications>Accessories>Terminal in 7.04. If you don't have those choices look for Terminal.

Re partition. You could format the empty space to e,g, NTFS or FAT32, for Windows use.

---

