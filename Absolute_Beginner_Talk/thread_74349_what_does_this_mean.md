---
title: "what does this mean:"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-11
when i run:
$sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by dgrafix on 2005-10-11
here is my fstab, are all iocharsets for ide hdds the same, because for one i dont know what its for and 2 there is no where to look it up

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /media/hdd1     ext3    iocharset=utf8,umask=000        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/hdd3     ntfs    iocharset=utf8,umask=000        0       0
/dev/hdc        /media/hdd2     ext3    iocharset=utf8,umask=000        0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by nitricacid on 2005-10-11
Anyone have any idea what this means?

It shows like 12 of the same thing after I hit dmesg in the bash.
[4310063.872000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310064.000000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310064.000000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known

---

### Post by dgrafix on 2005-10-11
This is what i get in my dmesg:
[4296137.856000] EXT3-fs: Unrecognized mount option "iocharset=utf8" or missing value

---

### Post by John Nilsson on 2005-10-11
Why are you hand edeting your /etc/fstab if you don't know what you are doing? There should be some GUI too for you to do that (In breezy it's System>Administration>Disks.

In any case "iocharset" is a ntfs only options that is deprecated to boot. What you want is now called "nls". "umask" is also something I don't think you wan't to be setting for your ext3 partitions.

I think the options you want to use for your ntfs partition is something along these lines:
```

ro,user,nls=utf8,uid=1000,gid=1000

```

and, by god, why do you mount hda6 as hdd1, hdb as hdd3 and hdc as hdd2?

Are you shure that you have used entire disks (hdb and hdc) as partitions? You aren't thinking of hdb1 and hdc1?

---

### Post by dgrafix on 2005-10-11
i would if the gui one was working, i couldnt get it to work. I would try and enable but no reason was given. 
The reason for the strange mount order is i have a hdd1 and hdd2 as my  main disks (excluding filesystem), hdd3 is just temporarily installed.
I would know what i was doing (i have over 15 years technical support experience with pcs so i am picking it all up quite fast) if there was a total beginners guide to linux on the subject. I need to know what charset etc i need for each filesystem and wether it is a partition or a main drive. Surely with a modern OS things like the character set, file system etc and can be determined automatically?

What i have done now is backed up my fstab and cleaned it out except for the cdrom, floppy, proc and hda1. If i mount all the drives one by one with no extra parameters, it seems to work ok. This being so, Is it alright to just put the drive and the mount location in fstab , without the other stuff?

Am i to understand that mount -a runs the fstab, and that it also runs on startup?

---

### Post by John Nilsson on 2005-10-11
Then mabey you'd want to read the manual?

```

$ man mount
$ man fstab
$ man man

```

Or you could navigate to the same manual pages thorugh Yelp which you will find under System>Help in Breezy.

For the total beginners guide I might point you to the [Unofficial Ubuntu 5.04 Starter Guide]("http://www.ubuntuguide.org/"), see the Windows section, and after that [The Linux Documentation Project]("http://www.tldp.org/").

---

### Post by John Nilsson on 2005-10-11
I get the impression that you are a little confused about harddisks and naming conventions in Linux.

hda: Primary Master
hdb: Primary Skave
hdc: Secondary Master
hdd: Secondary Slave

Note that these four designates the whole disks. If you read the first 512 bytes of one of them for example you would get it's master boot record:

```

$ man dd
$ dd if=/dev/hda of=~/hda.mbr bs=512 count=1

```

The partitions is then designated with digits

1-4 is the primary partitions
5 and up is the logical partitions

On a harddrive that has been used by windows you would probably have a layout like this:
hdb1: C:
hdb2: Extended Partition
hdb3: Not Used
hdb4: Not Used
hdb5: D:

Using hdb and hdc as partitions, though possible, seems very strange to me. You can use the command 'sudo fdisk -l /dev/hda', for example, to list partitions on a drive.

---

### Post by dgrafix on 2005-10-12
Thanks John, thats explained a lot :). I fixed it in the end with a lot of fiddling. 

Lol I didnt know that manual was even there!

i now have :
filesystm on hda1
what im calling;
media/hdd1 from hda6
media/hdd2 from hdb1 (i deleted the ptns and reformatted after getting the data as ext3)
media/hdd3 from hdc1 (this is a mirror of hdd1 using a sync)

seems to be working nicely now

thanks again

---

