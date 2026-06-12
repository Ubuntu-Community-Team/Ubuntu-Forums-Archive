---
title: "Partitioning Help..."
date: 2008-08-09
forum: Apple Hardware Users
---

### Post by JradG on 2008-08-09
I have a 100g hard drive I want to partition into 30g for mac, 10g for ubuntu, and 50something GB for a share partition between the two.

My first question is should I do NTFS or FAT32 for the share?  I have read that NTFS works for read-write for both ubuntu and mac os x but the ntfs-3g website ([www.ntfs-3g.org](www.ntfs-3g.org)) seems to be down so I couldn't get anymore information on it.

Also, I am using Disk Utility from the 10.5 install CD and I cannot partition in NTFS but only "FAT" (don't know if that's FAT or FAT32).  How would I go about partitioning my share drive in NTFS if I dont want to use Gparted (don't trust it since last time I used it I had way too many problems).  Can I throw in the windows install CD just to format in NTFS then quit the window installation?

Is there any kind of walkthrough for what I am doing?

Thanks in advance!

---

### Post by cyberdork33 on 2008-08-10
Use Disk Utility to create your intial Mac Partition and the space for the shared partition (FAT32 is really the most compatible, but there is a 4GB filesize limitation) and the Ubuntu space as "MSDOS". This will give a layout similar to:

1. EFI
2. HFS+ (OS X)
3. Shared (FAT32)
4. Ubuntu Space (FAT32)

Then boot into the Ubuntu Live CD, and start gparted. Select the last partition and delete it. Close gparted. Start the Ubuntu Installer. When prompted tell it to install to the largest free space. After that, your partitions will look something like this:

1. EFI
2. HFS+
3. FAT32
4. Ext3
5. Swap

Be sure to check this thread about problems with the installer and the way to fix it.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

If you really want NTFS then I would suggest formatting that before your Ubuntu Installation. I wouldn't use Windows to do anything to your partitions as it doesn't know how to deal with GPT like gparted does.

---

