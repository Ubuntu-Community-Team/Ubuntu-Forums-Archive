---
title: "manually partitioning SATA drive"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Twig E. Pottox on 2007-07-19
Help!  I'm trying to partition a 250 GB SATA HDD manually prior to installation of 7.04. I first exorsized the Evil BSOD MS scourge with "Derik's boot and nuke". I then made a "/" partition and placed it a the beginning of the drive. I then made the /swap partition and placed it at the end of the drive. When I attempt to    take the remainder of the drive and create a /home partition I get an error: "Can't have the end before the start". Hmmm... I tried to do the /home before the /swap and still got the same error. Is there a partition size limit? Would  appreciate any advice. Thanks in advance.

---

### Post by Nythain on 2007-07-19
this order works well for me
/boot
swap
/
/home

---

### Post by Twig E. Pottox on 2007-07-19
Thanks  but i'm still getting the "cant have the end before the start" error message.
what size is appropriate for a boot partition drive? this is an ubuntu only machine.

---

### Post by Golyadkin on 2007-07-19
My /boot partition is usually 32MB, but with current harddisk sizes it can be bigger. I don't really make a seperate partition for it even. 
I boot from a 320 GB SATA2 drive, manually partitioned to 3 partitions, /, /home and swap.

---

### Post by Twig E. Pottox on 2007-07-19
the heart of the problem i am having is that when i try to make the /home partition , no matter how many partitions i have it gives me a "Can't have the end before the start" error. what does this mean. I have partitioned several hdds though not a SATA.

---

### Post by Golyadkin on 2007-07-21
hmmm, maybe your BIOS doesn't support such large drives? You can try updating your BIOS so it can use 
 LBA for drives > 120GB

---

### Post by Trebaruna on 2007-07-21
What are you using to partition?
In my experience, Gparted always gets the job done, even when you want something a bit out of the ordinary.

You should be able to simply fire it up from the Ubuntu LiveCD (alt+f2 then type "gksudo gparted" but leave out the quotes). Alternately, you can get the Gparted LiveCD from [this site]("http://gparted.sourceforge.net/livecd.php") and boot into that.

EDIT: the ubuntu CD has a mildly annoying property (bug perhaps) of mounting partitions as you make them. This can sometimes cause trouble if you first create a partition and then apply a filesystem to it in one operation. Simply unmount them and continue.

---

