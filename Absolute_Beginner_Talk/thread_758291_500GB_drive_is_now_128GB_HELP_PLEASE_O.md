---
title: "500GB drive is now 128GB?? HELP PLEASE :O"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2008-04-17
I have a 500GB sata drive. Somehow it has magically become a 128Gb drive...Does anyone know what happened??

```
Disk /dev/sdb: 137.4 GB, 137437871104 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16710   134216640    b  W95 FAT32
root@ben-desktop:/home/ben# 

```

```
root@ben-desktop:/home/ben# e2fsck /dev/sdb
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

```
root@ben-desktop:/home/ben# e2fsck /dev/sdb1
e2fsck 1.40.2 (12-Jul-2007)
The filesystem size (according to the superblock) is 122096000 blocks
The physical size of the device is 33554160 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? 

```

WTF HAPPENED???

---

### Post by wolfen69 on 2008-04-17
you might want to try what is suggested. insert live cd and:
```
sudo su
```
then ```
umount /dev/sdb1
```
then
```
e2fsck -b 8193 /dev/sdb1
```

---

### Post by PmDematagoda on 2008-04-17
Actually wolfen69, the error message says:-
> If the device is valid and [B]it really contains an ext2
filesystem (and not swap or ufs or something else)[/B], then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
According to fdisk the drive has a vfat filesystem and not an ext one. So in the OP's case he aught to try:-
```
sudo umount /media/sdb1
```
and then:-
```
sudo fsck -t vfat -r /dev/sdb1
```

---

### Post by e1ektrob0y on 2008-04-17
```
root@ben-desktop:/home/ben# umount /dev/sdb1

root@ben-desktop:/home/ben# e2fsck -b 8193 /dev/sdb1

e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by e1ektrob0y on 2008-04-18
is there an option i can add to e2fsck to answer yes to everything? cause i'm kind of sick of holding down the "y" key haha...

---

### Post by hyper_ch on 2008-04-18
well, a few things come to my mind:

Your bios/motherboard cannot support disks larger than 128 GB
Isn't there a FAT 32 limit of 128 Gb?

Check your bios what it says about the drive size and why using fat32 anyway?

---

### Post by e1ektrob0y on 2008-04-18
> **hyper_ch said:**
> well, a few things come to my mind:

Your bios/motherboard cannot support disks larger than 128 GB
Isn't there a FAT 32 limit of 128 Gb?

Check your bios what it says about the drive size and why using fat32 anyway?

I thought it was ext2 to be honest. I have no idea why it says fat32...It WAS ext2 before this all happened?? what the hell does that mean?

---

### Post by hyper_ch on 2008-04-18
if you have no important data on it, just format it to something else... gparted would be a good tool to do that.

---

### Post by e1ektrob0y on 2008-04-18
> **hyper_ch said:**
> if you have no important data on it, just format it to something else... gparted would be a good tool to do that.

not an option, but thanks anyway. I need the data thats on the drive so...

---

### Post by e1ektrob0y on 2008-04-18
So, when i mount it it says this...
[IMG]http://i74.photobucket.com/albums/i247/dales618/Screenshot-diskProperties.png[/IMG]

But when otherwise is says 128GB fat32 even though disk properties says etx2?? I'm really confused :(

---

### Post by bumanie on 2008-04-18
> sudo apt-get install gparted and then provide a screenshot of what gparted shows.

---

