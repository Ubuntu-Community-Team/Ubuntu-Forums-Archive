---
title: "Dual Boot"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by someonedumb on 2007-03-18
Hi,

I'm trying to get dual booting to work better. I have two hard disks, one dedicated to Windows XP, and the other dedicated to Ubuntu. Ubuntu is on IDE channel 1. Windows is on IDE channel 2. Neither channel has a slave drive.

Right now I just use BIOS to select which drive to boot from, when the windows boot loader is working BIOS will be set to boot the disk on IDE channel 2.

I'm trying to figure out how to have the windows boot manager point to Ubuntu on IDE channel 1. 

Several dual boot guides suggest you use data dump to create a file like this:

```
dd if=/dev/hda1 of=/home/whatever/Ubuntu.bin bs=512 count=1
```

I get the file and put it on the windows partition and add the entry in Boot.ini which points to it.

```
C:\Ubuntu.bin="Ubuntu"
```

When I select the Ubuntu option in the boot menu instead of booting Ubuntu it just goes to a black screen, no error messages.

Am I using the wrong partition to input dd? Isn't hda1 the boot partition on the linux drive?

Most dual boot tutorials assume you are trying to have both operating systems on the same disk, does this method not work for multiple disks?

---

### Post by Kobalt on 2007-03-18
> **someonedumb said:**
> Isn't hda1 the boot partition on the linux drive?
That is for you to tell us... It depends on your partition table and HD scheme (could be hdb instead of hda for example). You might find out by displaying your fstab (from Ubuntu) : 
```
cat /etc/fstab
```

Wouldn't it be easier to use Grub and configure it point to your Win partition to boot under Windows ?

---

### Post by someonedumb on 2007-03-18
Here is fstab

```
someone@something:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

> Wouldn't it be easier to use Grub and configure it point to your Win partition to boot under Windows ?

I'd prefer to have only one boot loader. Daisy chaining more than one boot loader together just strikes me as very inelegant.

My windows partition has both DOS and Windows XP on it, I don't think Grub can distinguish between the two.

Oh, and I dont have an entry for my Windows disk in fstab yet, I'm mounting it manually each time I need it. It is hdc1

---

### Post by Kobalt on 2007-03-18
Your boot partition is hda1. 
I'm no grub & boot expert but I think it is possible to point from grub to your windows boot sequence and then, if you select it in grub, to chose between dos or xp. I even doubt grub can't boot directly on xp or dos... 
Anyway, since you don't want to use it.

I'm no expert of the windows boot loader, I'm afraid I can't help you out more then... :)

---

### Post by someonedumb on 2007-03-18
This is a quick clarification/summary of my question.

I'm trying to get the windows boot manager to boot linux. Linux is on the primary IDE channel. The drive that contains the windows boot manager is the secondary IDE channel, and this is the drive that BIOS tries to boot first.

In linux my boot partition is hda1, and according to several dual boot tutorials the following data dump command will create a 512kb file that can be placed in the windows partition, and used by the windows boot manager to boot the linux partition.

```
dd if=/dev/hda1 of=/home/whatever/Ubuntu.bin bs=512 count=1
```

However, when I put this file on the windows drive and add an entry for it in the windows boot manager and try to boot into Ubuntu I only get a black screen.

The tutorials usually assume you're putting linux and windows on the same physical drive but on different partitions, does this method not work with separate drives?

What exactly is in this 512kb file anyways?

---

### Post by Sbarton on 2007-03-18
Hi! am I wrong in assuming you have a dual boot with Windows on the master HDD and Ubuntu on slave drive?
If you have the above setup why not have grub on the master drive and add Windows to the Grub menu list? That way you can choose, at boot up what OS you want to use! Perhaps I have missed the point of your question, in which case maybe you can explain further.
regards

---

### Post by dstew on 2007-03-18
Your plan is to extract the grub boot loader stage 1 from the partition it is installed in, and make a file that Windows can use to boot linux. The success of your plan depends critically on whether or not you installed the grub boot loader stage 1 on the partition boot sector (hda1), or in the drive master boot record (hda). Since you can boot the drive from BIOS directly, my guess is that you installed grub stage 1 on the MBR. If so, you are not copying grub stage 1 to your file, but a piece of grub stage 1.5, and this will not work. You might try instead 

dd if=/dev/**hda** of=/home/whatever/Ubuntu.bin bs=512 count=1

I am not sure if this will work, but that is how I see it.

---

### Post by someonedumb on 2007-03-18
> If so, you are not copying grub stage 1 to your file, but a piece of grub stage 1.5, and this will not work. You might try instead

dd if=/dev/hda of=/home/whatever/Ubuntu.bin bs=512 count=1

I'm afraid this didn't work. The explanation sounded very promising. It did however give more than just a black screeen; it printed "GRUB" to the screen before hanging.

> Hi! am I wrong in assuming you have a dual boot with Windows on the master HDD and Ubuntu on slave drive?
If you have the above setup why not have grub on the master drive and add Windows to the Grub menu list? That way you can choose, at boot up what OS you want to use! Perhaps I have missed the point of your question, in which case maybe you can explain further.
regards

The drives are not master and slave, they are on separate IDE channels as described. Each drive is capable of booting without the other even being in the machine.

Originally I thought I could use a simple arcpath in boot.ini to specify the linux drive, but I couldn't get that to work, not sure why.

---

### Post by dstew on 2007-03-18
Did it print grub and give you a prompt, like this?

grub>

---

### Post by someonedumb on 2007-03-18
No, it printed "GRUB" followed by a "_". Not a prompt, it was frozen hard. Caps lock wouldn't toggle and CTRL+ALT+DEL did not work either, had to press the reset button.

---

