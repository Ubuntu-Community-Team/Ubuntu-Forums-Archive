---
title: "[SOLVED] Reinstalling Ubuntu and XP  Need help with the partitions"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by doowgof on 2007-11-30
Here it is my situation:
I have switched to Ubuntu for about a month. During this time I found Ubuntu is great and decided to continuously use Ubuntu.
However I installed the English version of Ubuntu and had great difficulties with installing Chinese input into my computer. Therefore I decide to reinstall Ubuntu, but this time I will choose Chinese as the default language. And 1 minor thing: I'm a gamer and I need Windows XP to play games, and maybe do some word processes (don't quite know how to use OpenOffice Presentation).
So I will install XP back to my computer. But the next bit is a bit complicated: I only have Toshiba XP system recovery CDs (basically Ghost), so I don't think they can do the partition.
So I will use Debian installing CD or Ubuntu Alternate Install CD to do the partition and then install XP. :(
What partitions shall I have then? Fat32/NTFS for XP, but which is better for Ubuntu to read/write? My disk has 80 gig, I'm planning to leave 30 gig for XP, so shall I use the debian/ubuntu disk to make a 30 gig FAT32/NTSF partition and the rest of 50 gig untouched, or shall I make the whole disk FAT32/NTFS and then use the Ubuntu disk to resize it to get Ubuntu installed?

Pls help! Thank you!

---

### Post by notoriousdbp on 2007-11-30
You've got 2 options really, I would first install XP then Ubuntu having done this before it does work better this way.  Alternatively, you can install XP on a virtual machine.  your ghost image should work on it and you lose nothing if it doesn't.  
The best way to do it is to use the trial copy of VMWare Workstation as this will let you create a virtual machine with support for USB 2.0 among other things and use this virtual machine in VMWare Player which is free.

---

### Post by notoriousdbp on 2007-11-30
Oh and Ubuntu 7.10 will read/write to either FAT32 or NTFS as ntfs-3g is installed by default now

---

### Post by doowgof on 2007-11-30
> **notoriousdbp said:**
> You've got 2 options really, I would first install XP then Ubuntu having done this before it does work better this way.  Alternatively, you can install XP on a virtual machine.  your ghost image should work on it and you lose nothing if it doesn't.  
The best way to do it is to use the trial copy of VMWare Workstation as this will let you create a virtual machine with support for USB 2.0 among other things and use this virtual machine in VMWare Player which is free.

Thank you. But I checked VMWare and I remember it says it doesn't support large games.
So I'll take your 1st advise n install XP 1st then resize the disk and install Ubuntu.
Thank you again.

---

### Post by quandary on 2007-11-30
> **doowgof said:**
> Here it is my situation:
I have switched to Ubuntu for about a month. During this time I found Ubuntu is great and decided to continuously use Ubuntu.
However I installed the English version of Ubuntu and had great difficulties with installing Chinese input into my computer. Therefore I decide to reinstall Ubuntu, but this time I will choose Chinese as the default language. And 1 minor thing: I'm a gamer and I need Windows XP to play games, and maybe do some word processes (don't quite know how to use OpenOffice Presentation).
So I will install XP back to my computer. But the next bit is a bit complicated: I only have Toshiba XP system recovery CDs (basically Ghost), so I don't think they can do the partition.
So I will use Debian installing CD or Ubuntu Alternate Install CD to do the partition and then install XP. :(
What partitions shall I have then? Fat32/NTFS for XP, but which is better for Ubuntu to read/write? My disk has 80 gig, I'm planning to leave 30 gig for XP, so shall I use the debian/ubuntu disk to make a 30 gig FAT32/NTSF partition and the rest of 50 gig untouched, or shall I make the whole disk FAT32/NTFS and then use the Ubuntu disk to resize it to get Ubuntu installed?

Pls help! Thank you!

Why do you want Ubuntu to write on your Windows partition?
Well if you want Ubuntu to write on your windows partition, then FAT32 is better.
Install Windows (windows lets you make partitions. make a 32000 MB partition for Windows, leave the rest blank)

after you installed windows, install ubuntu on the partition you left blank. That's all there is to it.

---

### Post by doowgof on 2007-11-30
> **quandary said:**
> Why do you want Ubuntu to write on your Windows partition?
Well if you want Ubuntu to write on your windows partition, then FAT32 is better.
Install Windows (windows lets you make partitions. make a 32000 MB partition for Windows, leave the rest blank)

after you installed windows, install ubuntu on the partition you left blank. That's all there is to it.

I want ubuntu to write on windows partition because I want to use it as a storage.
I don't have xp installing disk so I can't use xp to do the partition.. All I have are Ghost recovery disks. So I'll use debian/ubuntu disk to do the partition. The rest will follow your instruction. Thank you,

---

### Post by quandary on 2007-11-30
> **doowgof said:**
> 
 So I'll use debian/ubuntu disk to do the partition. The rest will follow your instruction. Thank you,

You can also use gParted instead of Debian/Ubuntu disk. gParted is fully graphical, so it's easy to use.

But Debian/Ubuntu disk will work, too.


You can also install a ext2/3 pluggable installable filesystem for windows, so you can read & write to the Linux partition from Windows. See:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by doowgof on 2007-11-30
> **quandary said:**
> You can also use gParted instead of Debian/Ubuntu disk. gParted is fully graphical, so it's easy to use.

But Debian/Ubuntu disk will work, too.


You can also install a ext2/3 pluggable installable filesystem for windows, so you can read & write to the Linux partition from Windows. See:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

But I have to burn another cd for gParted. I'll use debian/ubuntu for convenience. 

PS I'll try to make a usb gParted, but I don't know if my computer can be booted from usb or not. The bios says it can but when I actually made a damn small linux usb it didn't work.

---

### Post by quandary on 2007-11-30
> **doowgof said:**
> But I have to burn another cd for gParted. I'll use debian/ubuntu for convenience. 

PS I'll try to make a usb gParted, but I don't know if my computer can be booted from usb or not. The bios says it can but when I actually made a damn small linux usb it didn't work.

Oh i tried the same once. 
That's because you have to make your USB-stick partition active first.
Use the hp utlitily for windows:
[http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html](http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html)
to format the USB-stick partition active.

Or read this, but this is a slightly more difficult way:
[http://www.weethet.nl/english/hardware_bootfromusbstick.php](http://www.weethet.nl/english/hardware_bootfromusbstick.php)

It will work, then!

---

### Post by doowgof on 2007-11-30
> **quandary said:**
> Oh i tried the same once. 
That's because you have to make your USB-stick partition active first.
Use the hp utlitily for windows:
[http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html](http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html)
to format the USB-stick partition active.

Or read this, but this is a slightly more difficult way:
[http://www.weethet.nl/english/hardware_bootfromusbstick.php](http://www.weethet.nl/english/hardware_bootfromusbstick.php)

It will work, then!

I tried the hp utility method and a "syslinux" method, neither worked for my damn small..

---

### Post by quandary on 2007-12-01
> **doowgof said:**
> I tried the hp utility method and a "syslinux" method, neither worked for my damn small..

Hmm, have no idea why. If the option for booting from USB is in your BIOS, it should work. I used featherlinux to be exact. So featerlinux works for sure with that, if not it's probably because you did something the wrong way when trying to make the partition active...

---

### Post by doowgof on 2007-12-01
> **quandary said:**
> Hmm, have no idea why. If the option for booting from USB is in your BIOS, it should work. I used featherlinux to be exact. So featerlinux works for sure with that, if not it's probably because you did something the wrong way when trying to make the partition active...

I guess so.. And thank you very much for your help!

---

