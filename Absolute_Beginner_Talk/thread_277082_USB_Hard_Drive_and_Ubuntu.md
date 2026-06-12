---
title: "USB Hard Drive and Ubuntu"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by bigd0gg on 2006-10-13
I am planning on purchasing a USB Hard Drive to backup my files, mostly pictures.

I was wondering what manufacturer would be recommended to use with Ubuntu, my primary concerns are reliability and compatability.

Please chime in with your 2 cents.

Than from what I read in another thread ext3 would be the ideal file system.

On a lesser important note, I see some external drives that offer disaster recovery, is this going to cause me any issues with Ubuntu, as I assume this feature is designed for windows users.

Thanks.

---

### Post by gvgerman on 2006-10-14
Any Disastor Recovery feature / software is most likely a back-up / recovery feature for the failure of the drive hardware.  It is highly likely any recovery software included w/ the drive will be Windows-based.  To my knowledge, you can use the drive w/o the software if you choose to do so.

Based on my experience, USB drives are for the most part formated in Fat32 since that would  be recognized on the broadest range of computers - Mac, various OS versions of Windows, and Linux. 

Since it is a portable drive, I assume you may want to be able to access the pictures from Windows, as well.  You can read & write FAT32 from Ubuntu - at least I know of no restrictions.  Windows can not read & write ext#. There may be softare available that allows you to do this.

Googling for disk reliability / comparisons might result in some useful information of one manufacture vs. another.  Know that even though there many names / labels on the outside of the drive, many share common interal hardware under the skin.

---

### Post by RktMan on 2006-10-14
> **bigd0gg said:**
> 
I was wondering what manufacturer would be recommended to use with Ubuntu, my primary concerns are reliability and compatability.

...

Than from what I read in another thread ext3 would be the ideal file system.

On a lesser important note, I see some external drives that offer disaster recovery, is this going to cause me any issues with Ubuntu, as I assume this feature is designed for windows users.


you'd probably have to go surf the 'net for a while to get info about reliability. i think these days, most mfrs. have MTBF numbers that make this issue moot. iow, for average users, reliability is a non issue.

as far as FS, i think they mostly *all* work well. if you want to share this drive with non-linux machines, you are going to want to use FAT32. ext3 seems to still be the more "common" FS in use, but i don't think that it is generally known to be "better", just different. i think the Reiser file systems are the second most common file systems.

and as far as "disaster recovery" ... i'm pretty sure this is reffering to the "backup solution" many of these vendors are now putting together for their USB drive untis.

Usually this means that the drive some big, cool looking button on the front cover, that is basically a hotkey that kicks off their backup software ... under windows, backing up your files to the disk.

This is a windows feature, and to the best of my knowledge, there aren't any applications for Linux that make use of the "button".

and finally, compatability.

basically, the Linux kernel seems to support external USB drives pretty will i think these days.

i think the kernel support for this is "generic" ... which i'm pretty sure means that any compliant USB 1.1 or 2.0 drive will work.

on my machine, i bought an IBM hardrive a while back, and then bought a "generic" USB (1.1-2.0) drive enclosure for it.

it works like a champ.

Tony

---

### Post by bigd0gg on 2006-10-14
Thanks for the help guys.

I am going to format under ext3 because I already have a USB drive that is formatted on NTFS, so that will be my mobile drive.

This drive is purely storage.

The disaster recovery was just a general question, I am not going to use it but didn't want it to cause me any issues.

As far as reliability, I am going to search on google.  I'll keep you guys posted on my findings.

---

### Post by bigd0gg on 2006-10-14
Right now I am leaning towards the Seagate.  They have a 400GB drive for $200-$300.  This seems quite reasonable to me.

---

### Post by oliverb on 2006-10-14
About a year ago I bought two Freecom classic external drives and they were not recognised by Knoppix or by a Buffalo Linkstation. I wasn't using Ubuntu back then. The supplier wouldn't exchange the drives as they worked in windows so eventually I ended up stripping down the enclosures and fitting the drives in alternative cases. 

Newlink cases worked fine.

---

### Post by gn2 on 2006-10-14
I would advise buying an external USB enclosure, then you can swap drives in it.

This is an excellent facility to have.

I have a Raidsonic Icybox, and it works fine with 32-bit Ubuntu 6.06

---

### Post by pregoeater on 2006-10-14
they have a 500 gig my book at costco for 199.99 great deal 


pre

---

### Post by bigd0gg on 2006-10-15
500GB for $199 is an awesome deal.

As for the enclosure, I already have a hard drive I am using with an enclosure.

This go around I want to try the 1 piece.

How is Lacie, has anybody had any issues with them?

---

