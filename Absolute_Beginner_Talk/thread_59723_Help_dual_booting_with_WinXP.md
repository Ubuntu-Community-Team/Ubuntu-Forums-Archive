---
title: "Help dual booting with WinXP"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by sharpobject on 2005-08-25
I just built a new computer (DFI board, AMD64 chip, one HDD) and went on to install Windows and Ubuntu.  After failing at that for a while, I came to ask for help.  The process looked something like this:

- Install Windows XP
I had no problems.

- Install Ubuntu
I could not successfully format a FAT32 partition during installation, could not install GRUB, could not install LILO, could not boot after installation.  My machine would not boot any OS afterward.

- Install Ubuntu 
This time I removed the Windows partition.  I still could not format a FAT32 partition, but GRUB installation worked.  The machine booted successfully into Ubuntu.

-Install Windows XP
Well yes, it installed successfully.  I also had no way of booting Ubuntu.

That's just about where it stopped, then I came here.  My problems are thus: I cannot dual boot Windows XP and Ubuntu, and I cannot format a FAT32 partition >32GB to share between the OS's if they ever work.

Any help is appreciated, and I'll be sure to provide more detail if someone asks.

Thanks,
Rob

---

### Post by Buffalo Soldier on 2005-08-25
From what I've [read ](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkc_fil_tdrn.asp)32GB is the maximum size that FAT32 can support. 

How about making the partition a bit smaller? How about giving it a try again at 31GB?

---

### Post by sharpobject on 2005-08-25
FAT32 supports partitions up to 2 TiB.  My drive is much smaller, and the shared partition would need to be at most 140GB.  Windows versions 2000 and later cannot format FAT32 partitions >32GB for some reason, most likely because MS felt I should use NTFS.


EDIT: Someone on IRC said to install Ubuntu over Windows.  While this had already failed, I tried it anyway.  After telling it to format a FAT32 partition of roughly 130GB, I get:
```
The attempt to mount a file system with type vfat in
IDE1 master, partition 4 (hda4) at /home failed.

You may resume partitioning from the partitioning menu.
Do you want to resume partitioning?

<Go Back> <Yes> <No>
```

When the install disk is reinserted, the FAT32 partition is identified as allocated but unformatted.  Setup is clearly failing to format it.

GRUB and LILO both failed to install again, though one of them decided to mark the root partition as active despite it being unbootable.  I fixed this by setting my NTFS partition to active using the Ubuntu installation CD and booted Windows normally.  Just in case anyone can help this situation, I'll leave my HDD partitioned the way it is:

primary 1 - NTFS (about 10GB)
primary 2 - ext3 (about 10GB)
primary 3 - swap (3GB)
primary 4 - unformatted (about 130GB)

---

### Post by Buffalo Soldier on 2005-08-25
[MS official page](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkc_fil_tdrn.asp)> Maximum volume size	32 GB (implementation)

[http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)
> In theory, this should support a total of approximately 268,435,438 (< 228) clusters, allowing for drive sizes in the range of 2 terabytes. However, due to limitations in Microsoft's scandisk utility, the FAT is not allowed to grow beyond 4,177,920 (< 224) clusters, placing the volume limit at 124.55 gigabytes, unless "scandisk" is not needed. [1] Windows 2000 and XP placed a limit on the size of FAT32 partitions they can create at 32 GB, Microsoft says this is by design but does not explain why, and those versions of Windows are quite capable of reading and writing larger FAT32 partitions created by other means.

[http://www.windowsitlibrary.com/Content/175/07/2.html](http://www.windowsitlibrary.com/Content/175/07/2.html)
> VFAT has a partition limitation of 4 GB and a maximum file size of 4 GB. You can have only 512 files in the root directory, but the number of files in a non-root directory is unlimited. VFAT supports both the 8.3 and long file naming systems.

[http://linux.org.mt/article/filesystems](http://linux.org.mt/article/filesystems)
> Although the theoretical maximum size for FAT32 is 8 TB, Windows98's scandisk only supports 128Gb, and Windows2000 does not permit the creation of FAT32 disks larger than 32Gb.

Main issues:[list]
[*] Theoritically can support larger than 32Gb, but some MS quirks makes it max at 32Gb
[*] while linux may not face the same problem but, **maybe** some linux partitioner also impose the same limit as not to cause some quirky conflict to anyone dual booting with MS win.[/list]

My own vfat partition is only 4.3Gb. I could be wrong about this limitations though.

In any case, it's no harm in trying to set a smaller fat32 partition first... just to test this theory.

Anyway, here's my "settings", if in case you want some reference.

Output of *sudo fdisk -l*:```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4505    36186381    7  HPFS/NTFS
/dev/hda2            4506        5127     4996215    b  W95 FAT32
/dev/hda3            5128        9662    36427387+  83  Linux
/dev/hda4            9663        9729      538177+  82  Linux swap / Solaris
```

output of *df -H*```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/hda3               37G   3.9G    32G  11% /
tmpfs                  264M      0   264M   0% /dev/shm
/dev/hda1               38G   6.7G    31G  18% /media/windows
/dev/hda2              5.2G   459M   4.7G   9% /media/dmz
/dev                    37G   3.9G    32G  11% /.dev
none                   5.3M   2.9M   2.4M  56% /dev
```

*fstab* entry:```
proc            /proc           proc    defaults        0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda2       /media/dmz  vfat    iocharset=utf8,umask=000   0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
```

---

### Post by Catachan on 2005-08-25
I want to install Ubuntu onto my computer into a separate Partition from XP, I have a Linux Partition that is formatted right, and I have the xp Partition, I do not want to lose the data from Xp, however, in the install screens, it won't tell me if it sees that I have the Partitions, and it can't seem to guide me through the partition process, if I hit Continue should it work corectly? Or am I running a risk that it will Nuke windows? :?  ](*,)

---

### Post by Buffalo Soldier on 2005-08-25
Just follow the instruction at this site: [https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

But as with everything else, there is no 100% guarantee. Do backup your essential files and data first. And also it's a good idea to defrag your NTFS drive first.

---

### Post by Catachan on 2005-08-25
thanks that helps but I still don't know wheather I should continue since it won't tell me that my drive has any Partitions at all, is it programed to find a pre-fab linux partition or to over write what ever it sees has been used?

---

### Post by Buffalo Soldier on 2005-08-25
If you select manual editing of the partition table during installation.. it will go to a page that list all the partitions that you have. It detects NTFS and FAT32 smoothly for me.

---

### Post by Catachan on 2005-08-25
I shall give that a shot
Thanks

---

### Post by Catachan on 2005-08-25
do I need to format the planned for partition in a linux format, and if not, how should it be formatted?

---

### Post by aysiu on 2005-08-25
[QUOTE=Catachan]do I need to format the planned for partition in a linux format, and if not, how should it be formatted?[/QUOTE] Yes. It should be formatted as EXT3, not FAT32. Linux can read from and write to FAT32, but the Linux system itself should be installed on a native format. You can reformat  during the installation process.

---

### Post by Catachan on 2005-08-25
by the way I am down loading 5.4, but the trouble was with 4.1, so maybe it will work better this time

---

