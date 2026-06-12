---
title: "Help with Installation"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Xian81 on 2007-07-15
Hi everyone,

I used to run an windows xp installation on my cpu but then recently the hdd which the xp was on crashed. Hence i removed that hdd and decided to install ubuntu on my secondary hdd. The Hdd whcih crashed was a 40Gb hdd and then the secondary one is a 160Gb hdd. They were not running on raid. I removed the primary hdd and switched the secondary hdd to become the primary hdd. The secondary hdd has 4 partions in it of which 3 contained old data, and one of the empty partitions i deleted the partition and used it to install ubuntu.
However after installation, i always get the grub error 17, as far as i know this means the grub loader cannot mount the selected partition. Also when i tried to reinstall windows xp it also gives me a error when i try to reinstall. So what could be the problem. Can anyone help me pls.
Thanks.

---

### Post by anewguy on 2007-07-16
Yeah, the error 17 usually means it can't find the rest of the grub stuff, which I think would also include your operating system menu.  There are several things on this forum and on the net for recovering this, but I think the first thing you should do is boot using the LiveCD then run grub in it to see if it can see your hard drive.  If so, you'll need to use grub to reinstall the grub menus, etc..  I had to ths also, and found the following post just the thing I needed:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I hope it can work for you as well!:)

BTW - I'm just new at this so this is the one I found that I could follow without downloading more stuff, etc.   I assume you have the drive jumpered correctly for master/slave/cable select, and, if cable select, have the correct cable connector attached to the drive.

---

### Post by confused57 on 2007-07-16
> **Xian81 said:**
> Hi everyone,

I used to run an windows xp installation on my cpu but then recently the hdd which the xp was on crashed. Hence i removed that hdd and decided to install ubuntu on my secondary hdd. The Hdd whcih crashed was a 40Gb hdd and then the secondary one is a 160Gb hdd. They were not running on raid. I removed the primary hdd and switched the secondary hdd to become the primary hdd. The secondary hdd has 4 partions in it of which 3 contained old data, and one of the empty partitions i deleted the partition and used it to install ubuntu.
However after installation, i always get the grub error 17, as far as i know this means the grub loader cannot mount the selected partition. Also when i tried to reinstall windows xp it also gives me a error when i try to reinstall. So what could be the problem. Can anyone help me pls.
Thanks.

I may be able to help you boot your Ubuntu...if you're using Feisty, highlight your Ubuntu entry in the grub boot menu, press "e" to edit, then change root from (hdx,y) to (hd0,y), then press "b" to edit...I believe you need to press "e" again when you highlight the line with root...this is temporary if it works, but can be made permanent.

If you root is already (hd0,y) and you're using a version earlier than Feisty, you would need to change to root entry in the kernel line from /dev/hdb1 to /dev/hda1, then press "b" to boot...substitute your root partition for hda1, e.g. hda2, hda3, etc.

You might have trouble booting Windows if you install it on a partition that is physically located after the Ubuntu partition...the Window's installer probably doesn't recognize the ext3 format, if you're trying to install on the same hard drive as Ubuntu...I have seen some people have success installing Windows located after Ubuntu, but most have problems doing so.

---

### Post by Xian81 on 2007-07-16
> **anewguy said:**
> Yeah, the error 17 usually means it can't find the rest of the grub stuff, which I think would also include your operating system menu.  There are several things on this forum and on the net for recovering this, but I think the first thing you should do is boot using the LiveCD then run grub in it to see if it can see your hard drive.  If so, you'll need to use grub to reinstall the grub menus, etc..  I had to ths also, and found the following post just the thing I needed:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I hope it can work for you as well!:)

BTW - I'm just new at this so this is the one I found that I could follow without downloading more stuff, etc.   I assume you have the drive jumpered correctly for master/slave/cable select, and, if cable select, have the correct cable connector attached to the drive.

Thanks for the link i tried the method of reinstalling the grub but still iget the error 17 when i restart and it is unable to boot into ubuntu.

---

### Post by Xian81 on 2007-07-16
> **confused57 said:**
> I may be able to help you boot your Ubuntu...if you're using Feisty, highlight your Ubuntu entry in the grub boot menu, press "e" to edit, then change root from (hdx,y) to (hd0,y), then press "b" to edit...I believe you need to press "e" again when you highlight the line with root...this is temporary if it works, but can be made permanent.

If you root is already (hd0,y) and you're using a version earlier than Feisty, you would need to change to root entry in the kernel line from /dev/hdb1 to /dev/hda1, then press "b" to boot...substitute your root partition for hda1, e.g. hda2, hda3, etc.

You might have trouble booting Windows if you install it on a partition that is physically located after the Ubuntu partition...the Window's installer probably doesn't recognize the ext3 format, if you're trying to install on the same hard drive as Ubuntu...I have seen some people have success installing Windows located after Ubuntu, but most have problems doing so.

how do i get into the grub boot menu ?

---

### Post by Xian81 on 2007-07-16
Is it possible that i do not have a MBR on this hdd as the previous hdd which crashed was the one which had the Os in it so this causes my current hdd not to boot up.

---

### Post by ramjet_1953 on 2007-07-16
You might try the Super Grub Disk

it is an iso that you download and burn to a CD. You then boot from this CD.

I have found it very useful with its auto GRUB recover feature.

You can get the iso from here:

[http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

Regards,
Roger :cool:

---

### Post by Xian81 on 2007-07-17
> **ramjet_1953 said:**
> You might try the Super Grub Disk

it is an iso that you download and burn to a CD. You then boot from this CD.

I have found it very useful with its auto GRUB recover feature.

You can get the iso from here:

[http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

Regards,
Roger :cool:

Thanks for the link. But i tried the disk and still it wasnt able to help me boot up my system. I still got the stage 1.5 error 17.

---

### Post by Xian81 on 2007-07-17
Maybe i should describe my problem in more detail.
I used to have 2 Hdd one 40Gb and the on the 160Gb. The 40 Gb was the master while the 160 Gb was the slave. Windows Xp was installed on the 40 Gb while the 160 Gb was divided into 4 partitions contained data.

Then the 40 GB hdd crashed. So i removed the 40 Gb hdd and left only the 160 Gb hdd in my comp. I now let the 160 GB be the master with the jumpers set properly too. Now there are still 4 partions in the 160 GB hdd, i deleted one of the partitions so as to create a new space to install a new OS. I tried installing windows Xp but it always gives me a Operating system error after the first part of the installation. 

Now i tried installing Ubuntu, on the same partition and it gives me the stage 1.5 grub error 17. So is this a problem with the Os or is it actually a problem with the hdd. Does the Os have to be installed on the first partition of the hdd or can it just be installed on any partition ?

Thanks

---

### Post by confused57 on 2007-07-17
> **Xian81 said:**
> how do i get into the grub boot menu ?
I suppose this means you're getting the grub error 17, with no grub boot menu...if you were getting a grub boot menu, you could follow the directions I gave in my other reply.

If you're not getting a grub boot menu, you might want to make sure the jumper settings are correct on the drive, either "Cable Select" or "Master"...If this is the only hard drive connected, you might want to go into bios and turn "off" the slave hard drive controller....

---

### Post by confused57 on 2007-07-17
> **Xian81 said:**
> Maybe i should describe my problem in more detail.
I used to have 2 Hdd one 40Gb and the on the 160Gb. The 40 Gb was the master while the 160 Gb was the slave. Windows Xp was installed on the 40 Gb while the 160 Gb was divided into 4 partitions contained data.

Then the 40 GB hdd crashed. So i removed the 40 Gb hdd and left only the 160 Gb hdd in my comp. I now let the 160 GB be the master with the jumpers set properly too. Now there are still 4 partions in the 160 GB hdd, i deleted one of the partitions so as to create a new space to install a new OS. I tried installing windows Xp but it always gives me a Operating system error after the first part of the installation. 

Now i tried installing Ubuntu, on the same partition and it gives me the stage 1.5 grub error 17. So is this a problem with the Os or is it actually a problem with the hdd. Does the Os have to be installed on the first partition of the hdd or can it just be installed on any partition ?

Thanks
Just saw your last post.

Since you're reinstalling your OSes...Windows needs to be on the first partition of the hard drive.  You might want to boot the Ubuntu live cd, open Gnome Partition Editor, and create a FAT32 partition at the very beginning of the hard drive, making it the size you want to give to Windows.  Hopefully, this will enable you to install Windows, reformatting the partition as NTFS.  Ubuntu can be installed on any of the partitions, as long as your bios supports booting to large hard drives.

---

### Post by Xian81 on 2007-07-17
> **confused57 said:**
> Just saw your last post.

Since you're reinstalling your OSes...Windows needs to be on the first partition of the hard drive.  You might want to boot the Ubuntu live cd, open Gnome Partition Editor, and create a FAT32 partition at the very beginning of the hard drive, making it the size you want to give to Windows.  Hopefully, this will enable you to install Windows, reformatting the partition as NTFS.  Ubuntu can be installed on any of the partitions, as long as your bios supports booting to large hard drives.

Thanks for the quick reply.
So i will not be able to get ubuntu to boot unless i install windows on the first partition ?

---

### Post by confused57 on 2007-07-17
> **Xian81 said:**
> Thanks for the quick reply.
So i will not be able to get ubuntu to boot unless i install windows on the first partition ?
No, Ubuntu should boot regardless of where it's installed...Windows probably won't boot unless it's installed on the first partition.   You still might want to check your bios settings, if there might be something that's causing a problem with just the one hard drive attached.

---

### Post by Xian81 on 2007-07-18
> **confused57 said:**
> No, Ubuntu should boot regardless of where it's installed...Windows probably won't boot unless it's installed on the first partition.   You still might want to check your bios settings, if there might be something that's causing a problem with just the one hard drive attached.

Could it be that there is no MBR on this hdd as the MBR was on the hdd which crashed ? hence this hdd is unable to boot up the os ?

---

### Post by confused57 on 2007-07-18
> **Xian81 said:**
> Could it be that there is no MBR on this hdd as the MBR was on the hdd which crashed ? hence this hdd is unable to boot up the os ?
Grub's IPL is probably installed on the mbr or you wouldn't be getting the grub error 17.  If there was not bootloader installed on the mbr, bios would give you an error of "No Operating System Found".

Here's another possibility you could try:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

The above thread was found here:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

If you want to try using the live cd to mount your root partitiion:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
you can then access your /boot/grub/menu.lst & /etc/fstab & examine the files.

---

