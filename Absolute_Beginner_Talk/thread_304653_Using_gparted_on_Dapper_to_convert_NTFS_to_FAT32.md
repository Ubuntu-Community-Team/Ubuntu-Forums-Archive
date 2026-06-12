---
title: "Using gparted on Dapper to convert NTFS to FAT32"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-22
I have a 250GB NTFS USB hard disk that I would like to convert to FAT32 so I can use it in both Win XP and Dapper.

Last night I copied all the data to another drive, then launched gparted in Dapper and tried to convert the partition into FAT32.

But this doesn't seem to work, gparted tried to partition the drive, then 1 or 2 seconds later it labels the drive as 'unallocated'.

In Win XP under run > diskmgmt.msc will only allow me to use the NTFS filesystem when making a new partition.

Anyone have any experience and advice?
Thank you.

---

### Post by steve.horsley on 2006-11-22
You can do it from Ubuntu, I think, with the command:
**sudo mkfs.vfat -F 32 /dev/whatever**
but it may not like making a FAT partition that big. I know that Windows has a limit on the FAT size it is prepared to make.

See the manual for mkfs.vfat with this command:
man mkfs.vfat

---

### Post by Bachstelze on 2006-11-22
The limitation of 32 gigs for FAT32 filesystems was introduced in Win 2000 with absolutely no reason - by design, they say... The filesystem itself is still the same and can go up to approximately 8 terabytes.

[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

---

### Post by bigken on 2006-11-22
the reason for the 32gig limit is to force people to use ntfs ;)

---

### Post by Bachstelze on 2006-11-22
Yeah, well, that's not an acceptable reason to me :p

---

### Post by PartisanEntity on 2006-11-22
So if I go ahead and make the entire drive FAT32 will windows complain when I plug the drive in under win xp?

---

### Post by CatKiller on 2006-11-22
> **PartisanEntity said:**
> So if I go ahead and make the entire drive FAT32 will windows complain when I plug the drive in under win xp?

Not according to that Wikipedia page:

> Windows 2000 and Windows XP can read and write to FAT32 filesystems of any size, but the format program on these platforms can only create FAT32 filesystems up to 32 GB. Thompson and Thompson (2003) write[4] that “Bizarrely, Microsoft states that this behavior is by design.” Microsoft's knowledge base article 184006[3] indeed confirms the limitation and the by design statement, but gives no rationale or explanation. Peter Norton's opinion[5] is that “Microsoft has intentionally crippled the FAT32 file system.”

---

### Post by PartisanEntity on 2006-11-22
Tried, and this is what I get:

```
me@ubuntunb:~$ sudo mkfs.vfat -F 32 /dev/sdc
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sdc' (use -I if wanted)
```

---

### Post by CatKiller on 2006-11-22
> **PartisanEntity said:**
> Tried, and this is what I get:

You don't appear to have specified a partition.

---

### Post by PartisanEntity on 2006-11-22
In gparted the drive is labeled as /dev/sda and as unallocated

---

### Post by CatKiller on 2006-11-22
> **PartisanEntity said:**
> In gparted the drive is labeled as /dev/sda and as unallocated

If you've got the drive up in GParted anyway, can't you use that to make a partition that spans the whole disk and format it to FAT32?

Anyway, this is what **man mkfs.vfat** says about the -I option. >        -I     Normally  you  are  not  allowed  to  use  any ’full’ fixed disk
              devices.  mkdosfs will complain and tell you that it refuses  to
              work.   This  is  different  when  usind  MO disks.  One doesn’t
              always need partitions  on  MO  disks.   The  filesytem  can  go
              directly  to  the whole disk.  Under other OSes this is known as
              the ’superfloppy’ format.
 If that sounds like what you want to do, then use it, as it suggested.

---

### Post by PartisanEntity on 2006-11-22
I just tried to format it to fat32 in gparted, I get an error and it is labeled as unallocated.

---

### Post by CatKiller on 2006-11-22
Fair enough. I'd never tried it. Hopefully someone will be able to tell you what your error message means.

---

### Post by PartisanEntity on 2006-11-22
It worked, I have converted the hard disk to fat32.

(New issue moved to new thread)

---

### Post by PartisanEntity on 2006-11-22
I have been trying to figure it out but I just don't get it, is it a case of multiple mount points or improper formatting?

If I copy a file to 'usbdisk' it doesnt show up in 'usbdisk-1'.

---

### Post by CatKiller on 2006-11-22
> **PartisanEntity said:**
> Now in Places > Computer it shows up twice.

See screenshot. Why is it doing that?

Does [this]("http://www.ubuntuforums.org/showthread.php?t=185697") seem relevant?

I mention this post because it's one that I saw. There are probably others that will explain it better.

---

### Post by PartisanEntity on 2006-11-22
I am not sure if it is relevant? I have a laptop and the hard disk I formatted is a usb external type. Does that thread you linked to apply to my case?:confused:

---

### Post by PartisanEntity on 2006-11-22
(new issue moved to new thread)

---

### Post by CatKiller on 2006-11-22
> **PartisanEntity said:**
> I am not sure if it is relevant? I have a laptop and the hard disk I formatted is a usb external type. Does that thread you linked to apply to my case?:confused:

The information I took from it is that you can either refer to devices as /dev/whatever, or as the UUID of the partition. Possibly for consecutive times of plugging in your drive you used a different port, or the wind was blowing in a different direction, or whatever, and so the drive got assigned a different automatic mount point. I know that used to happen to me in Windows, but since I got Ubuntu I got a cable modem so I'm not plugging and unplugging USB devices as much.

So you could instead specify the UUID of that drive as a partition to be mounted at a particular mount point and delete the other mount point. Or something.

This is all entirely speculative, which is why I pointed you at the only piece of information I had to find a solution.

It's probably worth starting a new thread about anyway, if you can't find a solution yourself.

---

