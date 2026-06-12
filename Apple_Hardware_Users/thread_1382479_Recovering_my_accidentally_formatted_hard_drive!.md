---
title: "Recovering my accidentally formatted hard drive!?"
date: 2010-01-16
forum: Apple Hardware Users
---

### Post by diligence400 on 2010-01-16
Okay, so here's what happened. I'm on the latest Ubuntu OS on my netbook trying to make a USB Startup Disk. I have a 1GB USB and a 500GB hard drive plugged in to then netbook. I run the USB Startup Disk program, and it tells me I need to format the USB drive. Okay, so I press format, only to realize that I'm formatting the 500GB hard drive :---)
However, when I pressed format it give me an error saying the disk could not be mounted. I did something on Disk Utility and now I have a FAT32 system on the hard drive with nothing in it. Now my ultimate question is, am I able to recover the data that was on the hard drive?!!

The hard drive was formatted in HFS+, it was a Mac-formatted hard drive. Will I need to use a Mac in order to try to restore my files? This is pretty serious to me. Any help appreciated!

---

### Post by linuxopjemac on 2010-01-16
I am afraid that it is gone...other ideas anyone ?

PS Now you know that in every tutorial they advize you to do a backup!

---

### Post by oswaldkelso on 2010-01-16
If you've not done a low level format you maybe ablle to recover your data with "testdisk" [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
[http://forums.debian.net/viewtopic.php?f=16&t=42884](http://forums.debian.net/viewtopic.php?f=16&t=42884)

---

### Post by diligence400 on 2010-01-17
Thanks! I'll play around with Testdisk/Photorec and see what it can do.

Just a question in advance, how should I go about restoring files on the FAT32 system when it was originally HFS?

---

### Post by diligence400 on 2010-01-17
I got the static version of testdisk for ubuntu and found instructions for recovering an accidentally formatted hard drive. It tells me to change the type of the partition to the original type. I'm trying to change from fat32 to hfs, however there is no hfs option in the 'type' menu. Do I need to download some other package first?

---

### Post by svenni on 2010-03-23
I managed to do the exact same thing! It's a shame the USB Startup Disk Creator doesn't warn you before it just formats the drive.

Now I'm trying to recover my drive, but I could need some help. I have tried running testdisk, but when doing a "Deeper search" after selecting "Intel/PC" partition table it finds nothing.

I attempted to run a deeper scan with partition table type set to "None" and this time it finds the overwritten partition! :D However, when I attempt to list the files I only get "File system seems to be damaged" or testdisk crashes with a segfault. (It lists the partition twice with different starting sectors).

I'll try to change the partition table, but I cant do this when the table type is set to "None". I'll try to do it manually, but I'm also a bit disturbed about ext4 not being listed. Should I choose the file system type "Linux"?

diligence400: Have you had any luck recovering your drive?

---

### Post by hemantbahirat on 2011-10-04
same thing is happen with me.
Mistakenly formatted usb 1tb disk when i was using bootable-usb creator.

details : 
USB Seagate hard drive - 1TB capacity go flex
Operating system using - ubuntu 10.04
USB disk had only one partition of NTFS (single partition) 

When try to erase Pen-drive using usb-creator-gtk ,   mistakenly erased connected USB Seagate hard disk.
When i notice that i had immediately remove it from USB port.

Now Hard disk status is as follows : 
I try to recover it using TestDisk tool but,
tool shows = Can't open filesystem. Filesystem seems damaged.

Is there any possibility of recover data?
Please suggest.
--
Hemant

---

### Post by svenni on 2011-10-04
I was able to recover some data with testdisk and the other tools mentioned here:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

But it was quite a long journey, and I was not able to recover the entire file system. I could only list files of a certain type and recover these one by one.

My drive was a backup drive and I figured I had no data on it that was not stored elsewhere, so I didn't look further into it when I figured this out.

I would suggest that you read through the wiki page above and see if any of the suggested tools help you out. But first of all make a copy of the drive using a tool such as ddrescue.

---

### Post by JJJ&amp;J on 2011-10-04
I did a accidental quick NTFS to NTFS format of an old, and nearly full 200gig drive. After trying a few programs didn't work very well, or I didn't know how to use... then i stumbled on one that seemed to find everything that was ever on the drive. 2.5 TB worth of data was available for recovery with many save options. Seemed like OS files were there from 5 years earlier before it became an usb external drive. I was shocked. Sorry, cant remember name of program. Point is, data can be recovered witho

---

### Post by ktec on 2012-01-25
+1 for accidentally doing this too!! Clearly my fault for watching TV while doing admin on my computer, but would be nice if the disk-creator was a bit more verbose about which disk you're about to delete all your files from.......

---

### Post by ktec on 2012-01-25
> **JJJ&J said:**
> I did a accidental quick NTFS to NTFS format of an old, and nearly full 200gig drive. After trying a few programs didn't work very well, or I didn't know how to use... then i stumbled on one that seemed to find everything that was ever on the drive. 2.5 TB worth of data was available for recovery with many save options. Seemed like OS files were there from 5 years earlier before it became an usb external drive. I was shocked. Sorry, cant remember name of program. Point is, data can be recovered witho


Would REALLY appreciate if you can do some googling and identify that software?

---

### Post by svenni on 2012-01-25
I think many of the tools here should be useful:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

The biggest issue is whether the list of files on your partition was overwritten or wiped out during the formatting. If not, you might be lucky and get everything back. Otherwise, you might like me end up with a huge list of files without dates or file names that are simply identified as either videos or pictures. But before you try any of those tools I strongly encourage you to make a complete copy of your hard drive using a tool such as dd. That way you don't risk messing up your hard drive even more while trying to recover it.

---

### Post by waelmagdy on 2012-02-11
same thing is happen with me too ](*,) ](*,)

i think we should report about this tool (startup disk creator)

---

### Post by winh8r on 2012-02-11
Try this [http://extundelete.sourceforge.net/]("http://extundelete.sourceforge.net/")

to recover deleted ext 3 and ext4 partitions.

Testdisk is also one of the best.

It is important to stop using the drive with the deleted partition as soon as possible after you realise what you have done.

If you keep using it the system will continue to write to it and can overwrite deleted data making it harder to recover successfully.

I can offer nothing on the Mac recovery question as I have never had any experience of partitioning or recovering from a Mac.

The key to successful recovery is TAKE YOUR TIME!

Read all you can about it and make sure you understand what you are going to do and what will happen when you do it. If you are unsure, then stop, and ask someone. Data recovery is not an instant process and in the case of a full 500Gb drive could run to a couple of days.

If you really need the data then you really need to take the time to do it properly.

Alternatively go and pay a professional data recovery a lot of money and let them take their time over it.

---

### Post by ubantuuser789 on 2012-12-20
Yes! You are able to recover your formatted data as long as you have not rewritten the original data by saving anything new there.
  Here is [COLOR=Red]**a free recovery tool**[/COLOR] for you:
  [http://www.squidoo.com/format-recovery](http://www.squidoo.com/format-recovery)
  Actually, this free application has helped me recovering all my needed files from the mistakenly formatted drive. It is quite efficient.
  Tips for you:
  1. Never try to rewrite the original files, which can make them gone forever.
  2. Do not save the recovered files on the original drive, which can cause recovery failure.
  3. Do not forget to back up your important files as possible as you can in the future.

---

