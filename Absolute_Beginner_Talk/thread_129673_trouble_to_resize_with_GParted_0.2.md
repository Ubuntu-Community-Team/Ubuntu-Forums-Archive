---
title: "trouble to resize with GParted 0.2"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Markus2006 on 2006-02-14
I made a screenshot of Gparted, but I can't upload a jpeg in this forum. If anybody knows how to resize with GParted, then I would like to e-mail my jpeg Smile

I'll try to describe my problem: I boot from CD and GParted 0.2 opens up. My 2 harddrives are there. Everything's fine. I choose my 2nd harddrive. It looks like this:
/dev/sda1 fat16, Size 40 MB, Used 6 MB, Unused 33 MB
/dev/sda2 ntfs, Size 20 GB, Used 12 GB, Unused 8 GB (boot)
nicht zugeteilt (not partioned): 49 GB
/dev/sd3 extended, Size 44 GB, Used ---, Unused --- (lba)
/dev/sd5 ntfs, Size 44 GB, Used 19 GB, Unused 25 GB
nicht zugeteilt (not partioned): 8 MB

I want to enlarge my /dev/sd5 from 44 GB to 93 GB, by using the not partioned 49 GB. But GParted won't let me do that. I can only enlarge /dev/sd3 to 93 GB, but then i can't enlarge also /dev/sd3.
I think the reason is, because sd5 has to be at the beginning of sd3, but I can't move sd5, or I don't know how.
Any help is very well appreciated...
Markus

---

### Post by davmac on 2006-02-15
I think you're right in your guess about what is causing this problem. Is there anything on sd3 and sd5 that you need to keep? In your position I'd be backing up the whole disk (always wise when resizing partitions). Then I'd delete sd3 and sd5 partitions, recreate them at the size I wanted and then restore the data from the backup.

Hope this helps,

Dave Mac

---

### Post by Markus2006 on 2006-02-15
Sorry, Dave, but unfortunatly your answer doesn't help me at all. Everyone can delete partitions and create new ones. I wouldn't need gparted for this, I could do that with windows!

Please: Isn't anyone with gparted knowledge in this forum?

Thank you,
Markus

---

### Post by davmac on 2006-02-15
Markus,

Apologies if it wasn't the answer you wanted. I was trying to provide the simplest answer to the question, since this is "Absolute Beginner Talk". Perhaps you might have more luck in "Installation & Upgrade Help" where most of the paritioning question seem to get dealt with.

Dave Mac

---

### Post by cotcot on 2006-02-15
I do not know if you are a little bit familiar with command line. Posting the output of a couple of commands could be helpfull 

[SIZE="5"]sudo fdisk -l[/SIZE]

this will give info like this (sorry it is in dutch) :

Schijf /dev/hda: 41.1 GB, 41110142976 bytes
255 koppen, 63 sectoren/spoor, 4998 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1         638     5124703+   b  W95 FAT32
/dev/hda2             639        2550    15358140   83  Linux
/dev/hda3            2551        4894    18828180   83  Linux


[SIZE="5"]sudo parted /dev/sda[/SIZE]

this will give you the "parted prompt"

[SIZE="5"]print[/SIZE]

this will give info like this : 

Using /dev/hda
(parted) print
Disk geometry for /dev/hda: 0.000-39205,687 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0,031   5004,624  primair   fat32       opstart
2       5004,624  20002,807  primair   ext3
3      20002,808  38389,702  primair   ext3

[SIZE="5"]quit[/SIZE]

This will exit you from parted

---

