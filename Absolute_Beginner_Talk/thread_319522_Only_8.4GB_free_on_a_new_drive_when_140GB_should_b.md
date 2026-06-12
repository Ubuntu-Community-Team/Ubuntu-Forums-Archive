---
title: "Only 8.4GB free on a new drive when 140GB should be"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by feap on 2006-12-15
One more in the on-going saga of getting an external HDD to work properly:

If I format the drive with the portable HDD enclosure (Hyperdrive SPACE) and connect the HDD to my laptop I only see 8.4GB free on the drive although it should have 140+GB free. Fdisk and drive information show that 140.69GB are in use out of 149.05GB, with only 123 MEGAbytes of data on the drive.

But when I format using fdisk all is fine. EXCEPT I can't turn on data verification on SPACE - which I need to copy camera RAW files and keep my sanity - as it yields errors for some reason - no errors when using SPACE-formatted setup. Therefore it appears that I need to use the drive formatted with the portable HDD enclosure.

But how do I get the free space to be usable? This is the pertinent output after formatting with SPACE:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19458   156290872+   c  W95 FAT32 (LBA)

It is identical to the one when I format with fdisk so it's really strange that Ubuntu can't see all the free space.

Bottom line: everything works fine but I only have access to 8.4GB of free space. So, how do I get access to the 140+GB I should be getting by using my computer?

update: appears that 8.4GB is a magic number. Due to some strange legacy reasons:

# FDISK /X [Windows 95 + MS-DOS 7.00 and above ONLY]

"FDISK /X limits disk access to a total of 8.4 GB even on larger physical drives, even if the BIOS supports INT13h extensions for hard disks over 8.4 GB, thus preventing the use of 0E and 0F partition types, by ignoring LBA (Logical Block Addressing) and extended disk information.
This makes possible disk partitioning on computers with older BIOSes without support for hard disks larger than 8.4 GB.
Use /X to start FDISK if you receive disk access, stack overflow and/or data corruption error messages." from [http://www.mdgx.com/secrets.htm](http://www.mdgx.com/secrets.htm)

---

### Post by moshuptrail on 2006-12-15
If it will help, this is what feap is dealing with...

[Hyperdrive SPACE]("http://www.hypershop.com/shop/product_info.php?cPath=27&products_id=43")

This is a USB HD.

feap:  What is the output of the df command?

---

### Post by fritz_monroe on 2006-12-15
Obviously you have the reason for this.  Are you fdisking and formatting with a Windows system or your Ubuntu?

---

### Post by feap on 2006-12-15
fdisking with Ubuntu. Here's fd output (sda1 is the portable HDD):

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3495    28073556   83  Linux
/dev/hda2            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19458   156290872+   c  W95 FAT32 (LBA)
me@laptop:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hda1             27632244  25936448    292120  99% /
varrun                  257904        80    257824   1% /var/run
varlock                 257904         4    257900   1% /var/lock
udev                    257904       116    257788   1% /dev
devshm                  257904         0    257904   0% /dev/shm
lrm                     257904     18856    239048   8% /lib/modules/2.6.15-27-386/volatile
/dev/hdc               4473632   4473632         0 100% /media/cdrom0

---

### Post by moshuptrail on 2006-12-15
I'm no wizard, but this is odd 
I see that your root filesystem is 99% full
but the filesystem at /dev/sda1 is not listed.

Is it not mounted?

---

### Post by feap on 2006-12-15
I think it's mounted. I didn't do anything but to plug in the drive and it opens up the drive dialog. Running "mount" command in terminal gives this line (among others):

/dev/sda1 on /media/COMPACTDRV type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid=1001,umask=077,iocharset=utf8)

sda1 is the moniker for the drive in question so it appears to me that it's mounted?

---

### Post by moshuptrail on 2006-12-15
How do you know it's only got 8.4G? I mean, what output are you looking at?

If you go to the HDDSPACE and press> Feature > Browser > HDDSpace
Is that when it shows 8.4G?  What DOES it show?

It appears to be mounted at /media/COMPACTDRV

---

### Post by feap on 2006-12-15
HDDSpace shows 148GB. The 8.4GB is from file browser within Ubuntu, and I can't copy anything beyond 8.4GB. There are no files taking up that 140GB but system/administration/discs shows 140GB in use, as does gparted.

---

### Post by moshuptrail on 2006-12-15
I might have missed this earlier, but what utility did you use to format it in the first place?
The manual (p6) says it must be FAT32.  Did you use the HDDSPACE to format it's own HD?

Feature > Advance > Format


I wonder what would happen if you used Gparted to format it FAT32?

---

### Post by feap on 2006-12-15
Yes you missed it but no worries :) I formatted to FAT32 with both SPACE and Ubuntu.

The problem is that if I format it with Ubuntu, SPACE itself doesn't work properly with the formatted drive (namely file verification). The problem with SPACE-formatted is that I get the 8.4GB free space -problem in Ubuntu. Neither is a good option.

I don't think FAT16 supports 160GB drives.

I haven't used gparted for any of the formatting as it gives an error. So I've used the command sudo mkfs.vfat -n <label_name> <device>

---

### Post by moshuptrail on 2006-12-15
Ahhh.  That might be your problem.

I wonder if it's defaulting to FAT16.  The man-page for mkfs.vfat directs me to mkdosfs(\8\) which requires -F FAT32 to make a FAT32 filesystem.  You could try that, in case the .vfat part of the command isn't working like you expect.  There's a lot of other parameters there.  (Ugh)  I wonder if it actually formats the drive or just makes a file system.  That is, puts an entry in the partition table.

I'm just guessing, but if it were me, I'd use Windows to truly format it as FAT32. 

(I would have tried Gparted first, as you did, and I would have used the Live CD version)

---

### Post by feap on 2006-12-15
It is FAT32, verified in gparted.

So I guess this is yet another thing I need Windows for.

---

### Post by feap on 2006-12-15
I finally found a decent work-around:

I made 2 partitions:

- a large partition formatted with ext3 for use as external HDD for movies, mp3s and backups
- a small partition formatted with FAT32 for use as a dump for camera RAW files. I set this at 20GB which is enough for my shooting. The problem is that it again has the same free space problem which started this thread (ie. it displays 8.4GB free in file browser although it should be 20GB according to gparted).

It appears that although Hyperdrive SPACE works ok with multi-partition files, it's quite finicky at how they are formatted. So when I had 2 partitions, both FAT32 it broke data verification. But when I have 2 partitions formatted with different file systems everything works fine.

Now the only question that's left is whether I can access data beyond that 8.4GB limit in Linux...

---

