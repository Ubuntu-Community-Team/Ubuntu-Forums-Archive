---
title: "fat32 vs NTFS"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-11-04
So i've got my linux partions and then a blank 20GB fat32 that i intend to use for windows...eventually i suppose:rolleyes:.  Anyway, i know it is suggested to have a fat32 partion to use for moving things between linux and the windows NTFS filesystem.  What if windows is just installed to a fat32 to begin with?  I'm pretty sure i've seen windows on a fat32, but i may be mistaken and therefor all i've written is nonsense.  But assuming windows can be installed on a fat32, is there any reason why i shouldn't do it?  Wouldn't it make the process of transfering stuff easier since linux can read and write straight from that?

---

### Post by aysiu on 2005-11-04
If your Windows partition is FAT32, you can read/write to it straight from Linux and don't need another partition.

However, if you've already installed Linux and then install Windows afterward, your boot loader might get messed up. Then, you'll have to [restore Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by bionnaki on 2005-11-04
fat32 has an annoying filesize restriction which I believe is 3 gigs.

I used to have a XP partition with my external harddrive (used for music/movies) formatted as fat32. but then I realized that fat32 was unstable & had a filesize restriction. and then I realized I never booted into xp because I used ubuntu for everything. so I reformatted the entire harddrive...only have ubuntu....and reformatted the external has reiserfs.

---

### Post by aysiu on 2005-11-04
[QUOTE=bionnaki]fat32 has an annoying filesize restriction which I believe is 3 gigs.[/QUOTE] I'm wondering if that matters. How many files do you have bigger than 3 GB? The biggest files I have are about 700 MB (ISOs for Linux distributions).

---

### Post by Griff on 2005-11-04
Huh.  I did not realize there was a restriction of file size.  Good to know. Still unsure which would be best route.  I don't really have any files that large, but i don't know how much of an issue the stability will be.  Quite honestly, how much worse does it get.  Thanks for fast/helpful responses.

---

### Post by dbott67 on 2005-11-04
[quote=Griff]So i've got my linux partions and then a blank 20GB fat32 that i intend to use for windows...eventually i suppose:rolleyes:. Anyway, i know it is suggested to have a fat32 partion to use for moving things between linux and the windows NTFS filesystem. [/quote]
Yes, it does make things easier, although there is a package called Captive NTFS that offers stable read/write access to NTFS.
[quote=Griff]What if windows is just installed to a fat32 to begin with? I'm pretty sure i've seen windows on a fat32, but i may be mistaken and therefor all i've written is nonsense. [/quote]
Window XP can be installed on FAT32 or NTFS.  During installation you will be asked what type of filesystem to choose.
[quote=Griff]But assuming windows can be installed on a fat32, is there any reason why i shouldn't do it? Wouldn't it make the process of transfering stuff easier since linux can read and write straight from that?[/quote]
NTFS is generally faster and more robust than FAT32.  Add to that the permissions, encryption (XP Pro only) and auditing capabilities and there would be good reason to use it in a multi-user environment.  If max file size is also an issue, as bionnaki suggests, (ie. DVD .iso >= 3 GB) it might be an issue as well.

You could always install XP to NTFS and then create a separate FAT32 partition for data/linux.

-Dave

---

### Post by raublekick on 2005-11-04
[QUOTE=aysiu]I'm wondering if that matters. How many files do you have bigger than 3 GB? The biggest files I have are about 700 MB (ISOs for Linux distributions).[/QUOTE]

It's generally not a huge deal, but I have run into bumps in the past (it's actually 2Gb). 

I used the Windows backup feature to make a backup file of a lot of my stuff (about 30Gb worth). I had no idea how this feature worked, I just decided to try it and see what happens. So I tell it to back up the 30Gb of files, and it starts at it. What it actually does is make one file for the entire backup, like a .zip file. Unfortunately the Windows programmers didn't have the forsight to think "Hmm... what happens if a user selects more the the 2Gb....?" So I let my computer chug along for a few hours and then it comes up with and error telling me that it can't continue because the file size is too big! Grrr...

---

### Post by super on 2005-11-04
i recently switched my winxp drive from ntfs to fat32. it works ok, but there is a significant loss in terms of performance. it probably wouldnt be too bad if you have a good amount of ram in your machine. (i found it to be worst when it was using the swap file)

---

### Post by bionnaki on 2005-11-05
[QUOTE=aysiu]I'm wondering if that matters. How many files do you have bigger than 3 GB? The biggest files I have are about 700 MB (ISOs for Linux distributions).[/QUOTE]

I have several dvd .isos that are 4.7 gigs.

---

### Post by railz68 on 2005-11-05
[QUOTE=bionnaki]I have several dvd .isos that are 4.7 gigs.[/QUOTE]

The max file size for FAT32 is 4gigs, has to be just under a fraction of it actually. Any file over 4gigs is Impossilbe with fat32.

[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkc_fil_tdrn.asp]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkc_fil_tdrn.asp")
> 
Table 13.6   FAT32 Size Limits
Description	Limit
Maximum file size 	4 GB minus 1 byte (232 bytes minus 1 byte)

If you have a file thats over 4gigs, you are not using fat32.

---

### Post by railz68 on 2005-11-05
oh, and the reason I found this thread. I want to read my ntfs partition. It's not my windows install. It's a large partition that I'd like to use for all types of media. And, yes, I just want to "read" from it. But it's not listed in my /etc/fstab.
How do I know how to enter it correctly.
Hard disk 1 - WinXP FAT32
Hard disk 2 - Linux / Fat32 / ntfs

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows vfat defaults,exec,umask=000 0 0
/dev/hdb7 /media/fat32 vfat defaults,exec,umask=000 0 0
```

---

### Post by paddyg on 2005-11-05
[QUOTE=railz68]oh, and the reason I found this thread. I want to read my ntfs partition. It's not my windows install. It's a large partition that I'd like to use for all types of media. And, yes, I just want to "read" from it. But it's not listed in my /etc/fstab.
How do I know how to enter it correctly.
Hard disk 1 - WinXP FAT32
Hard disk 2 - Linux / Fat32 / ntfs

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows vfat defaults,exec,umask=000 0 0
/dev/hdb7 /media/fat32 vfat defaults,exec,umask=000 0 0
```[/QUOTE]


i think it's hdb6

try and mount it before adding any lines to fstab. It should be RO or umask=0222

---

### Post by railz68 on 2005-11-05
yes, thank you, it was hdb6.
It works

---

