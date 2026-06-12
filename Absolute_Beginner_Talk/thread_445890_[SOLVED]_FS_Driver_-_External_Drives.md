---
title: "[SOLVED] FS Driver - External Drives"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-16
Can we use FS-Driver with external hard drives?
 
I mounted my external HDD which is in EXT3 file system in XP and Vista (on separate machines).
 
But the problem is that, when I unplug the HDD (using the 'Safely Remove Hardware' in Windows) the LED on the HDD doesnt go off, even though Windows tells me its safe to remove my drive.
 
Also, the 'mount point' i.e. the drive letter still remains in the Windows Explorer and My Computer, but I can't access it since I have it removed. How can I make Windows recognize the drive as an USB External drive so that it can mount it automatically and unmount it once I do the safely remove hardware thingy -- just like it does for a FAT32 or an NTFS External Drive?

---

### Post by Inxsible on 2007-05-16
Bump

---

### Post by Inxsible on 2007-05-16
Can someone help me out here !  ](*,) 
 
Or I will have no choice but to convert the External Hard Drive back to NTFS......something that I don't really wanna do :(

---

### Post by orb9220 on 2007-05-16
If you would have gone to [http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html) and read it. It would have answered your questions.

>  I am using an external USB hard disk drive with an Ext2/Ext3 volume on it. When I remove that USB drive, the drive letters I have created with "IFS Drives" of the control panel still persist. (USB memory sticks are not affected.)

The current version of Ext2 IFS software is not able to realize Plug and Play events, so it does not delete its drive letters. Please read the Release Notes on how to work around it.

If you recieve no responses then maybe going to site of actual program might help.

---

