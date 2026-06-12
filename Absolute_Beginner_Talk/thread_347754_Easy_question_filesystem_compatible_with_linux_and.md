---
title: "Easy question: filesystem compatible with linux and windows?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by pantsroptional on 2007-01-27
I have 3 partitions right now: one with ubuntu on it, one with my music and documents and everything, and another which is empty now but i plan to put xp or vista on it. is there a filesystem format that I can use for the second partition that linux and windows can read and write to easily?? what about a format that linux, windows AND os x can all read and write to?? thanks! :D

---

### Post by loren95404 on 2007-01-27
This question has been asked a million times, but I'm glad to extend my .02 and experience

I found the best way to go is to run NTFS on one hard drive, Ubuntu on another, and I use my iPOD formatted to FAT32 as a 4GB inbetween place.


You will have to choose which Operating System is more important to you, and likely your files will follow, my only advice is DO NOT RUN REISERFS, it killed 300GB of files, ext3 however is reliable and recoverable too!

It's worth going out and spending the $30-100 for a hard drive for each OS, and it's wisdom that it eliminates problems. [http://www.newegg.com/ProductSort/Category.asp?Category=15&name=Hard-Drives](http://www.newegg.com/ProductSort/Category.asp?Category=15&name=Hard-Drives)




The other choice, is if you have a powerful enough computer (Dual Core, or 64-bit, 1+ GB Ram) then maybe run Windows Vista in VMWare Server (for free) [http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

I personally have a WindowsXP copy on my iPOD so I can take it with me anywhere!


Regards,

    Loren

---

### Post by pantsroptional on 2007-01-27
Oh yea I have 4 harddrives. My second partition is over 2 of them and for each OS I will have a dedicated disk for each of them. You're totally right this is THE way to do it. I love this harddrive setup for many reasons but the best is whenever I'm doing something weird with the disks, or installing an OS, I can literally unplug my files on my second partition and I know they're safe from being accidentally erased.

Right now the second partition is in NTFS, and Ubuntu can't write to that (is that right?) and it's a pain for me right now. I'm going to install XP on another disk soon and then that second partition will be readable/writeable in XP, but I use Ubuntu a lot and like a lot about it... Ubuntu is my main guy but I need a filesystem that both can read and write to.. are you suggesting ext3 then? Can OS X read and write to that? I'm thinking that OS X is a Unix kernel so anything that works with Ubuntu SHOULD in theory work with OS X but it's a really really modified kernel and that could be totally wrong. Can anyone answer that?

---

### Post by igknighted on 2007-01-27
I would recomend ext3 for your sharing partition.  There is a perfectly stable driver for ext3 and windows, and its a very reliable file system.  FAT32 is nothing but a pain, I would avoid it like the plague.  Ext2 is also a good choice, but its not journaled like ext3, dunno how that effects a share partition.

---

### Post by VraiChevalier on 2007-01-27
I believe I read in these forums or in the Wiki that FAT32 is the file system which both Ubuntu and MS Windows can read and write to. (or I may have read it on the psychocats pages)

---

### Post by pantsroptional on 2007-01-27
I don't think windows xp supports FAT32 anymore.. what does journaled mean? what about MS-DOS format?

---

### Post by Tomosaur on 2007-01-27
Journaling essentially means that you don't need to defrag your ext3 hard drive. That's not ENTIRELY true, since fragmentation does occur when the drive / partition is reaching it's capacity, but on the whole, your files are contiguous.

WinXP does still support FAT32, as far as I'm aware. The computer I'm on at the moment has a FAT32 recovery partition, which it can read just fine - but whether the required drivers were streamlined into this particular Windows installation, I have no idea.

I do know, however, that most USB drives tend to be some FAT variant, and Windows seems to have no trouble reading those.

---

### Post by AndyCooll on 2007-01-27
If it's on the same box you will need it to be a FAT32 partition. I wasn't aware that Windoze can read Ext3 (though please correct me if I'm wrong). If your partition is on another box you can use Ext3 and share the partition using Samba.

:cool:

---

### Post by smiggs on 2007-01-27
Install [http://www.fs-driver.org/](http://www.fs-driver.org/) on your Windows installation and 'enjoy' full access to your Linux partitions from Windows (note despite the name it is ext3 compatible).

---

### Post by coolen on 2007-01-27
I wasn't aware that Windows was able to read ext3...
I have a 20GB shared partition in fat32. Useful if you ever need to reinstall Windows and find yourself without ext3 support. Besides, I wouldn't trust Windows not to wipe my Ubuntu install if it could find it :P

---

### Post by raul_ on 2007-01-27
Ext2/3 would save you the trouble of defragmenting

---

