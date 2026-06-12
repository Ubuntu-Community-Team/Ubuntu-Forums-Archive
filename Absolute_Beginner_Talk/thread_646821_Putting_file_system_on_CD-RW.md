---
title: "Putting file system on CD-RW"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by mnb on 2007-12-21
Hi all,

Still stumped on how to put an ext2 or ext3 file system on a CD-RW - there were no replies to my last post.  So maybe someone could at least help or comment on some of the issues I have when I attempt this?

Problem #1:  Ubuntu auto mounts the CD when I put a blank CD-RW in the drive and mke2fs won't work with a mounted device.  I DO A UMOUNT ON THE DEVICE... YES?

Problem #2:  mke2fs warns the following:"/dev/cdrom is entire device, not just one partition!"
Proceed anyway? (y,n)"   I CAN PROCEED..... YES?

Problem #3: mke2fs then complains: "/dev/cdrom: Read-only file system while setting up superblock".   I DON'T UNDERSTAND THIS ONE... HOW IS IT READ-ONLY IF THE DEVICE IS NOT MOUNTED?  HOW DO I GET RW ACCESS TO THIS DEVICE WITHOUT MOUNTING IT? 

Thanks for any insight,

MIchael

---

### Post by mellowd on 2007-12-21
Why do you want to do this? CD-ROM's use their own types of filesystems

---

### Post by Leslie Viljoen on 2007-12-21
mellowd is right, ext2/3 are likely to seek all over the disk, something that is quite slow on a cdrom. I seem to remember doing this on a floppy disk once and it didn't work well at all.

---

### Post by CCNA_student on 2007-12-21
Could you please explain why you want the ext3 file system on a CD. 

     Sin Cere,

     CCNA

---

### Post by mnb on 2007-12-23
Ok... an explanation to my maddness...

I want to put a file system on a RW-CD to have a significant chunk of flexible off-machine storage.  I want to be able to add to and *remove* files from this storage at will - just like a floppy.

As far as I know - there is no way to do this with a CD-RW in ISO9660 format... I'd have to create the entire new image and reburn the CD if I wanted to add or remove a file or two.

As I mentioned in my first post - I did this in Windows with no problem.... sure it's a little slow, but it is flexible and convenient if I want a *dynamic* archive of some files that I can lock up in a fire safe.

Surely, this is not that unusual of a need?  How is this any different than a big floppy?  How does the Linux community handle off-machine dynamic storage?

Thanks,

Michael

---

### Post by Rocket2DMn on 2007-12-23
There really isn't any point to doing this.  For what you want, you can get USB flash drives for dirt cheap nowadays - a 1GB drive goes for 10-20 dollars.  Even better, check this out - [http://shop3.outpost.com/product/4855520;jsessionid=IylCED44FwTjz+ImR6gBQg**.node2?site=sr:SEARCH:MAIN_RSLT_PG](http://shop3.outpost.com/product/4855520;jsessionid=IylCED44FwTjz+ImR6gBQg**.node2?site=sr:SEARCH:MAIN_RSLT_PG)
1 dollar after rebate! (+ shipping i imagine).  I have one of these - it works great.

CDs use their own ISO file systems and I'm not even sure if it's possible to format the file system on them.

---

### Post by maybeway36 on 2007-12-23
I've seen it work in Windows, but I'm not sure if it works in Linux. USB is your best bet.

---

### Post by mnb on 2007-12-25
> **Rocket2DMn said:**
> There really isn't any point to doing this.  For what you want, you can get USB flash drives for dirt cheap nowadays - a 1GB drive goes for 10-20 dollars. .

Yes, thanks for the input - I've considered a USB flash drive... a little pricy at 10 bucks a pop - especially when I've got this stack of CD-RW sitting here... but looks like it may be the only option.

A big thanks to everyone who scratched their heads a bit on this.

Michael

---

