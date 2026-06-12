---
title: "USB Flash Drive"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by aeroprof on 2007-05-17
I am new to Ubuntu.  I have installed Feisty and love it.  One thing I have been unable to do is read/write a USB flash drive.  I have really not done anything to the system since I installed it from the Live CD (I did download/install the security updates.)  Perhaps I have not configured/activated something necessary to read/write the USB drive?

Thanks in adance for your help,

Aeroprof

---

### Post by k33bz on 2007-05-17
you will need to mount with read and write privilages  if it has not been done so automatically

---

### Post by aeroprof on 2007-05-17
Thank you for the reply - but how do I do what you suggest?  Mouting the drive makes sense to me - I just don't know where to go to do that.  If there is some sticky I need to read, please just let me know.

Thanks for your patience!

Aeroprof

---

### Post by k33bz on 2007-05-17
grrrrrrr, sorry i thought id have that answer for you, but it dont seem to be in my guide i have. I will go look for ya. unless someone else replies soon with hte answer

---

### Post by Hobo Joe on 2007-05-17
I never had trouble with mine.

One thing you could try doing is getting root permission for opening it. To do this, alt+F2, then type
```

gksudo nautilus

```

Then try reading/writing from the drive.

---

### Post by k33bz on 2007-05-17
[http://www.linuxquestions.org/questions/showthread.php?t=380376]("http://www.linuxquestions.org/questions/showthread.php?t=380376")

[http://www.linuxforums.org/forum/300990-post11.html]("http://www.linuxforums.org/forum/300990-post11.html")

[http://www.itslot.com/how_to_mount_usb_drive]("http://www.itslot.com/how_to_mount_usb_drive")

i hope these links help you out :)

---

### Post by esoterica on 2007-05-18
Just for confirmation for other people reading this as well I never had any problems either. I pop in my USB flash drive without doing anything or configuring anything and it just automatically pops a window open with the contents of my flash drive in it. No voodoo or magic required.

---

### Post by k33bz on 2007-05-18
> **esoterica said:**
> Just for confirmation for other people reading this as well I never had any problems either. I pop in my USB flash drive without doing anything or configuring anything and it just automatically pops a window open with the contents of my flash drive in it. No voodoo or magic required.

as neither have i

---

### Post by joe.turion64x2 on 2007-05-18
Is the automount service running?

---

### Post by trent dillman on 2007-05-18
...

---

### Post by aeroprof on 2007-05-18
Thanks to all who responded.   Let me give you an update:

I did the "alt-F2" thing - all that did was bring up a "root - File Browser" window.  Not sure what I was supposed to do with that.

I checked the documents given in the links.  I will apologize in advance, most of the instructons might as well have been in Greek.  For example, statements like:

tail -f /var/log/messages
mkdir /mount/usbdriv
mount /dev/sdb1 /mount/usbdrive

don't mean anything to me.

Let me tell you what I have discovered.  If I plug in my my USB Flash Drive, I can go to Hardware Information (Device Manger) found under System;  scrolling down I can see the flash drive listed under USB 2.0 called out by name (Cruzer mini).  So I guess the system is recognizing the hardware.  So it might just be my stupidity in not knowing how to access it.  Suggestions?

I aplogize again if I am doing someting stupid and I do appreciate everyone's help.

Aeroprof

---

### Post by JerseyShoreComputer on 2007-05-18
Here is another confirmation for some of you out there. I use a 4gb USB memory card and it just pops up on the screen - the same one I've used on PC and Mac as well. It is an IO magic.

just curious- is the drive you are having problems with a U3 drive? maybe that could have something to do with it? Perhaps try a non-U3 drive and see if it pops up.

---

### Post by aeroprof on 2007-05-18
It is not a U3 drive.  Its probably 2 or 3 years old.  It is a SanDisk Cruzer Mini, 256 MB, model SDCZ2-256.  I just checked it and it works on a Windows XP machine.  I could read and write files just fine.

---

### Post by theicyj on 2007-05-18
I would check to see if your flash drive is formatted using ntfs (as already mentioned).  If you do not have any important data on the drive, and it is formatted using the ntfs filesystem, I would recommend formatting it to fat32.  My flash drive is using the fat32 filesystem and works great in Windows or Ubuntu.  

What is the output when you type: 

> sudo fdisk -l

in the terminal (with the flash drive inserted into the USB port)?

---

### Post by aeroprof on 2007-05-18
Here is the fdisk -l output.  I *think* the flash drive is the last one listed?  That is saying it is FAT16.  Let me reformat as suggested and try again...............


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14311   114953076   83  Linux
/dev/sda2           14312       14593     2265165    5  Extended
/dev/sda5           14312       14593     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdb5               2        4865    39070048+   b  W95 FAT32
/dev/sdb6            4866        9729    39070048+   b  W95 FAT32

Disk /dev/sdc: 262 MB, 262144000 bytes
32 heads, 33 sectors/track, 484 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         485      255984    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(254, 31, 33) logical=(484, 27, 5)

---

### Post by aeroprof on 2007-05-18
Just to update...................

I reformatted the USB flash drive as FAT32.  Still no luck.

It is visible in the Harware Information (device manger) under USB 2.0

.

---

### Post by aeroprof on 2007-05-18
FINAL UPDATE..............

I just tried a new USB Flash Drive and it worked fine.  Apprently the problem must be with the flash drive I was using.  It works fine on WinXP but it will not work with Ubuntu.  The drive is a SanDisk Cruzer Mini model SDCZ2-256.

My thanks and appreciation to all who responded.  I feel embarrased I did not try a newer drive at first.  I'll be smarter next time!

Aeroprof

---

### Post by joe.turion64x2 on 2007-05-18
> **aeroprof said:**
> FINAL UPDATE..............

I just tried a new USB Flash Drive and it worked fine.  Apprently the problem must be with the flash drive I was using.  It works fine on WinXP but it will not work with Ubuntu.  The drive is a SanDisk Cruzer Mini model SDCZ2-256.

My thanks and appreciation to all who responded.  I feel embarrased I did not try a newer drive at first.  I'll be smarter next time!

Aeroprof
Can you tell us something more about your flash drive? Is it old? What kind of flash drive is the one you used as replacement?

---

### Post by jynyl on 2007-05-19
> **joe.turion64x2 said:**
> Is the automount service running?

How do I check this?
There is no service named "automount" in System Settings > System Services.  Should it be in there?

Running Kubuntu 7.04 here.  Plugging in a USB device or inserting a CD would cause a box to pup up, asking whether to mount, play music, etc.  This box no longer appears.  I'm not sure when this stopped happening, maybe after some updates.

TIA

---

### Post by joe.turion64x2 on 2007-05-19
> **jynyl said:**
> How do I check this?
There is no service named "automount" in System Settings > System Services.  Should it be in there?

Running Kubuntu 7.04 here.  Plugging in a USB device or inserting a CD would cause a box to pup up, asking whether to mount, play music, etc.  This box no longer appears.  I'm not sure when this stopped happening, maybe after some updates.

TIA
Its proper name is **autofs** and in Fedora it is under Services. I have not checked it in Ubuntu but it ought to be similar.

---

### Post by joe.turion64x2 on 2007-05-19
If that box no longer appears with any media then Automount is not operating.

---

