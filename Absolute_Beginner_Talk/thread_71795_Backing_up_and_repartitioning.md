---
title: "Backing up and repartitioning"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by astronerd on 2005-10-04
Hi all, few questions.  I have recently changed the size of my HD dual boot partitions.  It goes like this:
dev/sda1     Fat16       63 Mb
 /dev/sda2     Ntfs          20.5 Gb
Unallocated               65.5 Gb
/dev/sda3     ext3        102 Mb
/dev/sda4     extended    67 Gb
/dev/sda5   ext 3       64 Gb
/dev/sda6   swap        2.5 Gb

I would like to use that empty space(65 GB) to add to my Ubuntu partition.  I have been told that:  fdisk /dev/sda,  Type p for partition,  Then d for delete,  and it will ask for a number...  Tell it #3,  then p again,  <to see what happen>,  
Then n for new..
And it will ask for start and end records/cylinders..


Will this work, and/or is there an easier less risky way?  I also backed up my /etc and /home/username with tar cpf command but it gave me some huge 8Gb home.tar file and I only have a CD burner.  Any way that I can compress this to make it fit on something smaller?  Thanks alot in advance

---

### Post by SilentCacophony on 2005-10-04
Hi. Which partition is your Ubuntu on? I'm guessing sda5, which is quite large.

To me, it's eaiser just to store large files on another partition, and mount it for access through the /media directory.

You could also check out [this]("http://ubuntuforums.org/showthread.php?t=46866") thread on how to move your /home directory to the new partition, which may help.

---

### Post by astronerd on 2005-10-04
Yes my ubuntu is on that partitoin.  The problem is that you can only have 4 partitions, and I already have that.   My fourth partition is the extended on that can be broken down to / and swap.  I want to know if I can get rid of /dev/sda3 which I dont think is anything, then take the extra space which is not a partition and combine them.  Then take that new space and add it to ubuntu... Make Sense?  So that is why I am asking about the fdisk commands, they would supposedly do that..  But I dont want to do it for 2 reasons
1) I cant/havent moved my backup stuff cause its too big to put on a CD, so if something screws up I am screwed.
2)  I dont know if this will even work, the fdisk that is, so it might cause more damage.  
Is this making more sense?

---

### Post by SilentCacophony on 2005-10-04
Sorry, I don't know if you can non-destructively expand your Ubuntu partition, but I think it's unlikely at best.

If you're not using sda3 for anything, then it'll be no problem to delete it and make a new partition out of the now larger unallocated space, though. I'd suggest trying gparted, qtparted, or parted to partition with. Make sure that sda3 is not mounted into the filesystem before trying to delete it.

Is there any particular reason you'd want just one extremely large partition for ubuntu? It's often more flexible to have a separate partition to store large files on, and your current ubuntu partition seems quite large already.

---

### Post by astronerd on 2005-10-04
Well basically I just want to be able to use that extra space that I cut off of my windows partition with gparted.  See I had originally cut the 160 Gb HD in half and now I want to give more to ubuntu since I use it more.  So I am willing to have another partition as long as I can save and use it for ubuntu stuff, instead of one 120 Gb ubuntu one.  How can I make sure that I am not using /dev/sda3, and how do I unmount it, add it to the other space, and then remount it to be usable by ubuntu?  Thanks, 
Charles

---

### Post by SilentCacophony on 2005-10-04
Well, if you take a look at your */etc/fstab* file, and don't see an entry for */dev/sda3* in the first column, then it shouldn't be mounted. If it is there, then run **sudo umount <mount point>** in a terminal, replacing <mount point> with the path in the second column (usually like /media/sda3.) That will unmount it.

Run gparted and delete the sda3, which will make the unallocated space bigger, then make that space a new partition. You can use Ext3 if you only want to use it for linux, or FAT32 if you want to access it from Windows as well. You can read the docs in /usr/share/doc/gparted if you have gparted installed and don't know how to use it, or type **man gparted** in a terminal.

Afterword, you can mount the new partition by changing the old sda3 entry in /etc/fstab to reflect the new filesystem type (ext3 or vfat), or add a new entry for it. Use **sudo nano /etc/fstab** to edit it. Then a **sudo mount -a** will remount everything in fstab. For reference, I'll post my setup so you can see how it looks.

```
brian@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32
/dev/hda2             313         697     3092512+  83  Linux
/dev/hda3             698        1338     5148832+  83  Linux
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux
/dev/hda6            1852        2364     4120641   83  Linux
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA)

brian@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda5       /media/hda5     ext3    defaults        0       2
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hdb1       /media/share    vfat    rw,user,umask=000        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

