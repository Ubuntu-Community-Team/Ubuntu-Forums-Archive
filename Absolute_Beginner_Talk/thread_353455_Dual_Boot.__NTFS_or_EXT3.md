---
title: "Dual Boot.  NTFS or EXT3?"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Wreckless Randy on 2007-02-04
In preparation for going from WinXP to a dual boot
WinXP and Ubuntu...

There seems to be 2 ways I can go (as I have no intention
of going back to FAT32).  [B]I can either use ntfs-g3 to read/write
to NTFS with Ubuntu, or I can use FS-Drive to read/write to
Ext3 using WinXP.[/B]

:KS I would like to hear some *opinions*
on which is better, which is easier, etc.


-I'm thinking the answer is "no", but [B]is it possible to convert
my current hard drive to Ext3 without reformatting it?[/B]

-[B]Does anyone know if it's possible to use something like
[EZ File Transplanter]("http://www.superwin.com/ezxplant.htm")
to drag and drop my current entact programs and files under WinXP onto
a new hard drive that uses Ext3?[/B]

-I'm sure there is a lot of bias towards ext3, but[B] which file system
(if either) is inherently better - ext3 or NTFS?[/B]

---

### Post by Bachstelze on 2007-02-04
What will be the use of the partiton ? If it's purely for data sharing between Windows and Linux, the best bet is ext3 - or even ext2 since you'll have little to no use for the journaling.

FAT32 would actually be the safest bet since it's read/writable natively by both OSes but it's quite unconvenient (becaue of the 4 GiB per file limit, for example) and problems with NTFS-3g are rare but not unheard of.

---

### Post by IYY on 2007-02-04
I usually just install Windows on a FAT32 partition, but it's your choice.

---

### Post by Sef on 2007-02-04
> What will be the use of the partiton ? If it's purely for data sharing between Windows and Linux, the best bet is ext3

I agree.  When I dual booted, that's what I did.

> -I'm thinking the answer is "no", but is it possible to convert
my current hard drive to Ext3 without reformatting it?


No, as far as I know (AFAIK.)  You must reformat if you convert.

---

### Post by chronusdark on 2007-02-04
I will go with the ext because the windows EXT driver works fine only problems i see with it are if you use non windows characters in your ext filesystem for example mp3's with a colon (:) will not load in windows applications

if you keep check that your filenames meet common with both OS's then ext is an excellent way to go

---

### Post by Wreckless Randy on 2007-02-04
Hmm... this gives me more things to ponder.

---

### Post by closetpirate on 2007-02-04
Ease of use and reliability: fat32

versatility and larger file size limit: EXT3

that should some it up

---

### Post by testube_babies on 2007-02-04
I do all of the above:
1.)  Install Windows on NTFS, access with ntfs-3g in Ubuntu.
2.)  Install Ubuntu on ext3, access with ext2ifs in Windows.
3.)  Shared storage on FAT32.

---

### Post by Wreckless Randy on 2007-02-05
> **testube_babies said:**
> I do all of the above:
1.)  Install Windows on NTFS, access with ntfs-3g in Ubuntu.
2.)  Install Ubuntu on ext3, access with ext2ifs in Windows.
3.)  Shared storage on FAT32.

Wow.

There are so many options to choose from.

---

### Post by msandersen on 2007-02-05
Much the same here, though I steer clear of Fat32. Personal bias. Bad memories of Winows95/98/ME, probably. And there's no need with the Ext2IFS driver and NTFS-3G combo. The latter will become part of Linux-NTFS, and possibly the kernel driver later.
So, for sharing Data partitions, I have NTFS-3G on Linux and Ext2IFS on Windows.
Both are under development and both have limitations and bugs. Both mean you have to shut the other OS down properly (no suspend/sleep) before you can access the partition. Exst2IFS currently does not support the Unix permissions or hide dot-files, though the developer emailed me it's on the cards. So sharing your Home directory on Windows means a lot of dot-files getting in the way. Also, if you overfill the Ext2/3 partition with it, the driver currently doesn't handle it correctly; Windows slows to molasses and you'll have to be very patient to restart, followed by booting Linux to have Fschk fix the partition. Never lost any data with either, though.
As an experiment, I made 2 Data partitions when installing Ubuntu, each 15Gb, one NTFS, the other Ext3. Both are available from either OS through Ext2IFS and NTFS-3G respectively. According to the tests by the NTFS-3G developer, NTFS read/write is very fast, faster than Ext2/3.

So I guess the answer is; Depends. Which OS do you consider your main platform? Use its native format. If you use Linux more and Unix filesystem security is important, use Ext3. For a general Data partition, it may not matter.

---

### Post by msandersen on 2007-02-05
Oh, one thing worthy of note... 
Whereas Ext2/3 is fully documented and the Ext2IFS driver is made from the official specs, NTFS is an undocumented proprietary format that various drivers have attempted to reverse-engineer over time. NTFS-3G, a temporary fork of the Linux-NTFS driver, is the first to have full support, is currently Beta, and as such considered unstable, even if testers don't seem to have problems overall.
So, I would consider the Ext2IFS driver safer overall at this stage. But I have no data to back that up.

---

### Post by fluffnik on 2007-02-05
My current favoured arangement for *single user* dual boot machines is to put WXP and Linus system spaces at either end of the drive with an ext3 /home partition in the middle.

I point "My Documents" at /home/$USER/Documents to avoid seing a mess of dotfiles while in WXP.

I think ntfs-3g might be a better bet on multiuser systems since it implements (AFAIK) some level of access control.

FAT should have died long since.

---

### Post by HellTriX on 2007-03-23
I recently converted to Ubuntu from XP. I've had many gigs of data from back in the early 90s that i've managed to keep safe and transfered between upgrades an such for just as long.

Recently I installed the ntfs-3g to access my 1.5 terabytes of storage that I used on my XP install.
Since installing the module I have written about 90 gigs of data from Ubuntu to the NTFS partition successfully. Only doing about 2.38Mbps but this is over 54Mbit wifi from my laptop.

One of the directory trees I write has over 100,000 files in it. It does slow to 190Kbps for some of the tiny file directorys with hundreds of files. But otherwise I have had no odd effects by using this NTFS-3G driver/mod. All my data seems to be working just the same as before.

I also use samba for NAS with Ubuntu hosting 4x500gig NTFS-3g mounted drives.

I thought about converting to ext3 so linux can use it natively but, now I'm thinking there is no point given the NTFS-3G will be come standard eventually.

When i get more drives, I will probably partition them in ext3 just because it will be easier to do from Ubuntu.

---

### Post by buuntuu! on 2007-03-23
> **msandersen said:**
> Oh, one thing worthy of note... 
Whereas Ext2/3 is fully documented and the Ext2IFS driver is made from the official specs, NTFS is an undocumented proprietary format that various drivers have attempted to reverse-engineer over time.

i think that says it all!

---

### Post by stokedfish on 2007-03-23
I recommend NTFS.

Works flawlessly here, both read and write.

---

### Post by maxamillion on 2007-03-23
fat32 would be easiest, but ext3 would be safest in respect to data loss

---

### Post by stokedfish on 2007-03-23
In what way is EXT3 safer in respect to data lass than NTFS?

---

### Post by AndrewBarber on 2007-03-23
Personally I found that the ext drivers for Windows caused it to crash explorer.exe more often.
However I havn't been a Windows user for a long time and things may have inproved.

---

### Post by igknighted on 2007-03-23
> **stokedfish said:**
> In what way is EXT3 safer in respect to data lass than NTFS?

It is not an inherent difference between the file systems (NTFS probably outperforms ext3 easily), but rather an issue with drivers.  Ntfs-3g is a driver built, not from the physical specs of the ntfs format, but rather reverse engineering and trial/error.  Therefor, there is no guarantee.  It has, however, gone stable now, so the odds of you finding a bug that loses data in your day to day experience is so small its almost non-existant.  The ext3 format (being open source) releases its full specs.  Therefor, when building the windows driver there is no guesswork involved.  That doesn't mean it is perfect either, as earlier in the thread some weaknesses of this driver were outlined as well.

Neither ext3 or ntfs are perfect, but both are infinitely better than fat32.  Fat32 is, in its very nature, inherently unstable.  It can crap out for no reason and corrupt data.  There are also file size limits.  I would avoid fat32 if you can.

---

