---
title: "new installation...will old files be overwritten?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by badperson on 2007-11-02
Hi,

I'm putting ubuntu desktop 7.10 on a machine I have, and it has two hard drives. I want to be able to get at files on the data drive, will the ubuntu installation overwrite those files? How can I protect them? 

(the machine has two physical hard drives, not a partitioned drive)

bp

---

### Post by pay on 2007-11-02
Ubuntu will need to partition atleast one of the drives. Meaning that you will lose the data on that drive. You might be able to shrink the drive though and then leave some space for ubuntu to install .

---

### Post by arkara on 2007-11-02
yes the data will be lost because the hard drive will be formated to the linux filesystem
you can backup any data needed on a dvd or an external hard drive.

---

### Post by badperson on 2007-11-02
thanks, 

the thing is, I got an ugly blue screen in windows, and I was unable to install xp. Windows is installed on one drive, and the data is stored on another,  ubuntu can have a whole drive to itself. 

what are the ubuntu  equivalents of c:\, d:\, etc?
bp

---

### Post by rsambuca on 2007-11-02
As long as you have enough space to create a new partition for Ubuntu, you will not necessarily lose any data, but the odd error has occurred.  In any event, you should always make backups anyways, since drives fail. :)

---

### Post by Sef on 2007-11-02
> what are the ubuntu equivalents of c:\, d:\, etc?

The first hard drive will be hda.  If it is partioned then it will be hda1, hda2,etc for the different partitions.

The second hard drive will be hdb.  If it is partitoned it will be hdb1, hdb2, etc. for the different partitions.

If you want to keep your data drive safe, and you are installing to hda, then unplug hdb, your data drive while installing.   Usually there is not a problem, but people have installed to the wrong hard drive before.

---

### Post by badperson on 2007-11-02
thanks, 

it loaded the kernel ok, now I've just got a blinking cursor...it wouldn't load from the xp disc either, so maybe the machine is just fried. 
bp

---

### Post by overdrank on 2007-11-02
> **badperson said:**
> thanks, 

it loaded the kernel ok, now I've just got a blinking cursor...it wouldn't load from the xp disc either, so maybe the machine is just fried. 
bp

Well maybe not, Could be just a graphics issue. Try boot the live cd in safe graphics mode. Also you can at the screen to start/install Ubuntu press F6 and edit the kernel line and remove quiet splash. This will allow you to see any errors.

---

### Post by badperson on 2007-11-03
Hi,

I tried the safe graphics mode with the same result as the regular install, and when I hit F6, I'm not sure if I was understanding the options;


I also tried to do a complete reinstall of WinXP on this machine, and got a bluescreen, just after the option of reinstall, repair, etc. So I'm thinking this is some kind of hardware issue. The machine sat in a storage locker all summer, so maybe something got jostled loose or broken? 

thanks, 
bp

---

