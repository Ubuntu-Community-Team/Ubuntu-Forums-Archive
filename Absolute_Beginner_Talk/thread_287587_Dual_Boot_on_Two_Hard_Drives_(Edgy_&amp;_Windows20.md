---
title: "Dual Boot on Two Hard Drives (Edgy &amp; Windows2000)"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by adriankitch on 2006-10-28
Ok I'm starting a new thread on this despite my earlier post.

I'm still having trouble getting a working dual boot system going.  These threads that were forwarded have been very helpful.

[http://www.ubuntuforums.org/showthread.php?t=275728]("http://www.ubuntuforums.org/showthread.php?t=275728")
[http://www.ubuntuforums.org/showthread.php?t=179902]("http://www.ubuntuforums.org/showthread.php?t=179902")

However after following the instructions to edit GRUB I've still no luck in getting the Windows drive to boot.

I'm using the option where GRUB remaps the drives.

> 
title              Windows NT/2000/XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


It doesn't appear that the Windows drive likes this and I get a "disk read error occurred".  This appears whenever the Windows drive is not Master.

I've tried having Windows master and Ubuntu slave but Ubuntu (Edgy) doesn't seem to like being slave either and throws a system error.

It's getting annoying having to swap master/slave pins to choose the drive I want to boot. ](*,)  

Is there any issues that Edgy has that would be different to previous releases and Dual Booting?

My prefered set up is

Ubuntu Disk: Master
Windows 2000 Disk: Slave
Boot choice through GRUB

Both drives are IDE.  My fdisk output is:
> 
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9732    78172258+   7  HPFS/NTFS


---

### Post by confused57 on 2006-10-29
Have you checked in your bios that the slave drive controller is set to "auto" or "enable"?

---

### Post by adriankitch on 2006-10-29
slave is set to "auto"

---

### Post by confused57 on 2006-10-29
You could try changing the line root (hd1,0) to  rootnoverify (hd1,0)...sometimes this works.

You probably already know to make sure the hard drive jumper settings are correct.

If rootnoverify doesn't work, you can try "copying and pasting" the Window's grub entry in this link to your /boot/grub/menu.lst:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by adriankitch on 2006-10-29
Ah confused57 you're a legend... and I'm a duffus.
I had my jumper setting wrong on one of the drives (moved pin on wrong drive).

Always the things right under the nose that get ya.

Cheers

---

### Post by confused57 on 2006-10-29
> **adriankitch said:**
> Ah confused57 you're a legend... and I'm a duffus.
I had my jumper setting wrong on one of the drives (moved pin on wrong drive).

Always the things right under the nose that get ya.

Cheers

Been there, done that...glad you got it working.

---

