---
title: "iMac G5 not detecting SSD w/ fresh Ubuntu install"
date: 2012-05-11
forum: Apple Hardware Users
---

### Post by spaceballl on 2012-05-11
Anyone know what the issue might be? I'm trying to install a fresh install of Ubuntu on a "factory fresh" SSD. I installed it in the iMac, but Ubuntu says it can't detect the drive... booting from the liveCD... Do I need to "prep" it by formatting it somewhere else? Thanks!

---

### Post by stepking2 on 2012-05-13
You probably need to format it. Go into the Disk Utility in Ubuntu and see if there are any free space or unallocated disk space.
Use the ext4 file system.
For mounting points:
 - The root mounting point is /, so set a partition around 30-40Gb, depending on how big your SSD is.
 - The home mounting point is /home, this will store all your music, videos, documents etc. so this will be a little bigger, but again, it depends on how big your SSD is.
 - You can also choose to set a swap partition, this is for hibernation purposes, but since the Ubuntu developement team has removed the GUI function of this feature, you don't have to have one. But if you choose to set it, it should be bigger than the amount of RAM you've got.

Good luck :-)

---

### Post by spaceballl on 2012-05-13
But wouldn't the Ubuntu installer let me format the disk?

---

### Post by eastone on 2012-05-14
> **spaceballl said:**
> But wouldn't the Ubuntu installer let me format the disk?

Disk must be formated in hfs.

---

### Post by spaceballl on 2012-05-14
> **eastone said:**
> Disk must be formated in hfs.

Oh is that right? Just for the installer to *detect* a hard drive, that drive must be formatted in HFS?

---

### Post by eastone on 2012-05-14
> **spaceballl said:**
> Oh is that right? Just for the installer to *detect* a hard drive, that drive must be formatted in HFS?
Yes, OF does not see "ext" partitions. Is necessary to format disk first under mac disk utility.

---

### Post by spaceballl on 2012-05-14
Thanks! You made my morning... I was thinking that I'd have to send the drive back, etc etc, or that maybe my G5 somehow didn't support SSDs. I look forward to working on it this evening! I'm excited to get my G5 up and running w/ a 128GB SSD + 2GB RAM.

---

### Post by spaceballl on 2012-05-14
Hi All,

So... I'm not sure what the issue is. I formatted the SSD w/ OS X Disk Utility on my MacBook Air, and it's recognized as HFS. But... still the Ubuntu Installer doesn't seem to detect it. This time, however, when I boot up, I get the folder question mark thing on the iMac so I know that it can see the drive, I think I do at least.

Just to make sure I wasn't crazy, I put the spinning disk of Ubuntu back in the iMac and booted right up. So... my next test is i'm going to use Carbon Copy Cloner now to make an image of the hard drive, and then I'll image that back to the SSD, and I'll see if that works.

But i'd really just like to get this darn iMac G5 to detect the SSD on boot!

---

### Post by Hatsune Miku on 2012-05-14
> **spaceballl said:**
> Hi All,

So... I'm not sure what the issue is. I formatted the SSD w/ OS X Disk Utility on my MacBook Air, and it's recognized as HFS. But... still the Ubuntu Installer doesn't seem to detect it. This time, however, when I boot up, I get the folder question mark thing on the iMac so I know that it can see the drive, I think I do at least.

Just to make sure I wasn't crazy, I put the spinning disk of Ubuntu back in the iMac and booted right up. So... my next test is i'm going to use Carbon Copy Cloner now to make an image of the hard drive, and then I'll image that back to the SSD, and I'll see if that works.

But i'd really just like to get this darn iMac G5 to detect the SSD on boot!

There is a kernel issue with detecting SSD. If I were you, I would try to make it a blank disk, boot into Ubuntu live, format it was MBR and move from their.

---

### Post by eastone on 2012-05-15
> **spaceballl said:**
> Hi All,

So... I'm not sure what the issue is. I formatted the SSD w/ OS X Disk Utility on my MacBook Air, and it's recognized as HFS. But... still the Ubuntu Installer doesn't seem to detect it. This time, however, when I boot up, I get the folder question mark thing on the iMac so I know that it can see the drive, I think I do at least.

Just to make sure I wasn't crazy, I put the spinning disk of Ubuntu back in the iMac and booted right up. So... my next test is i'm going to use Carbon Copy Cloner now to make an image of the hard drive, and then I'll image that back to the SSD, and I'll see if that works.

But i'd really just like to get this darn iMac G5 to detect the SSD on boot!

I was not so clear last time ;)
Maybe this can help: support.apple.com/kb/HT2595
Apple Partition Map must be used for internal disk too, especially for internal in ppc mac ;)

---

### Post by spaceballl on 2012-05-15
> **eastone said:**
> I was not so clear last time ;)
Maybe this can help: support.apple.com/kb/HT2595
Apple Partition Map must be used for internal disk too, especially for internal in ppc mac ;)
I see... However, I only have an Intel Mac around - i'm guessing the partition map is different than that used on the Intel macs so I'm not sure how to best get the disk formatted.
> **Hatsune Miku said:**
> There is a kernel issue with detecting SSD. If I were you, I would try to make it a blank disk, boot into Ubuntu live, format it was MBR and move from their.
I see. So you think Ubuntu Live would detect the disk, even if the installer didn't? I have the "white screen of death" issue with Ubuntu Live... maybe if i try video=ofonly I can boot into Live and try to get it going from there.

---

