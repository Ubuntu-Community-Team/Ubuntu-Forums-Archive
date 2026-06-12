---
title: "Sharing data with Windows- [Resolved]"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Kobi Haron on 2007-02-22
I have Ubuntu 2.10 on a PC that also has W2000. I have dual boot and the Linux resides in a separate hard disk. In Linux I see the Windows C: drive as hda1 and I can copy everything from there to the Linux desktop. 

I am looking for a way to copy data from my Linux file system to hda1. Right now I use a flash disk for this purpose but I need to move large files.

Thanks for any help.

---

### Post by apjone on 2007-02-22
what is the w2000 File system? 

You may need to sudo 
eg
sudo cp x /media/w2000

---

### Post by Spr0k3t on 2007-02-22
Double check to see if the drive is not compressed with NTFS.

```
mount | grep ntfs
```

If it is compressed you will only be able to read, but not write.  Also, if the device was not shut down properly (in Windows), it will not mount the /dev/hda1 without the "-o ro" option flag.

```
sudo umount /dev/hda1
sudo mount /dev/hda1 -o ro
```

Give that a shot and post your results.

---

### Post by george29 on 2007-02-22
I presume you mean windows 2000 with NTFS files system dual booting with Ubuntu using Ext3 filesystem.

Do you not have any spare space on either drive to create anther partition using the FAT32 which both OS's can read and write to?

or you can install a driver which lets windows read and write to Ext2 and Ext3 partitions.

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

george

---

### Post by bigken on 2007-02-22
george29 is right I have have used this for about 12 months now without any 
problems 
**[IMG]http://www.chrysocome.net/images/logo.jpg[/IMG] **

---

### Post by anaconda on 2007-02-22
linux can now write to ntfs partitions, but you need to install a program for that, and it is still in beta, so no guarantees.. altought I have heard it works perfectly.

The better solution would be to install fs-driver to windows so that windows can read/write to your ubuntu (ext3) partition.
[http://www.fs-driver.org/](http://www.fs-driver.org/)
This is what I used to use. And I think this is more reliable, because ext3 is open standard.  Not secret like ntfs, which drivers have had to be made by "guesing" and testing how ntfs works..

---

### Post by Kobi Haron on 2007-02-22
Thanks folks,

I'll try one of the drivers soon.

---

### Post by Ben Sprinkle on 2007-02-22
There is a howto here (search), search in ntfs3g or ntfs-3g. You will be able to write to ntfs partitions now and it's pretty stable. :)

---

### Post by Platinum89 on 2007-02-23
> **Spr0k3t said:**
> Double check to see if the drive is not compressed with NTFS.

```
mount | grep ntfs
```

If it is compressed you will only be able to read, but not write.  Also, if the device was not shut down properly (in Windows), it will not mount the /dev/hda1 without the "-o ro" option flag.

```
sudo umount /dev/hda1
sudo mount /dev/hda1 -o ro
```

Give that a shot and post your results.

Tried this and I get the error message that the hard drive is not removable so the mount command failed. I really need to access the data from Ubuntu if at all possible.

O/S - Win98SE, Ubuntu 6.06 (Dual Boot)
HD1 - 10GB Fat32
HD2 - 80GB Fat32, Ubuntu

Appreciate any wisdom folks. I'm new to this, but I'm learning!:)

---

### Post by Kobi Haron on 2007-03-08
OK, This is OK now,

In W2000 I installed from [http://www.fs-driver.org](http://www.fs-driver.org) and in Ubuntu I use the new NTFS-3g driver. Thanks for the help I got here.

Kobi

---

