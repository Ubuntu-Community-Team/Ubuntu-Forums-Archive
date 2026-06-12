---
title: "Trying to access free space"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-13
Hi guys
Just at the end of the msg I have my fdisk -l output. I am just trying to make sense of it. First of all... what is the relation between hda2 and hda6? I have two hard drives in my amd64. I can see clearly my second HD which has windows (80 GB). The first HD is a Maxtor 200GB and when I installed linux and create two partitios... one of about 60GB and the rest of free space I named it /export/home.

I did this because I was advised to split the huge amount of space from my 200GB HD so to have in one partition only root files and in the other partition to have my files. Looking at the fdisk -l I do not understand the meaning or relation between hda2 and hda6. If I save files in /export/home (as I define it in my ubuntu installation), where am I storing those files? Also do I have to mount those partitions to get access to them?



 	
root@NARUTO:/# fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8052    64677658+  83  Linux
/dev/hda2            8053       24321   130680742+   5  Extended
/dev/hda5           23971       24321     2819376   82  Linux swap / Solaris
/dev/hda6            8053       23970   127861272   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9728    78140128+   7  HPFS/NTFS
root@NARUTO:/#

---

### Post by taurus on 2007-05-13
The thing is you can only have 4 primaries partitions to a drive and if you want to have more than 4, then you need to make one of them as extended partition.  So, your /dev/hda1 is the first primary and /dev/hda2 is your extended partition.  Under that extended partitions, you have two more partitions, one for swap and one for as you have mentioned, /export/home.  Therefore, you can mount /dev/hda6 anywhere you want but since you want to mount it to /export/home (like Solaris) instead of /home, you can use that as a storage.

Any reason why you want to mount /dev/hda6 to /export/home instead of /home?

---

### Post by krisfrajer on 2007-05-13
I was advised to do so... actually I could called it anything, but I decide to go with /export/home to differentiate with the standard /home from linux root... if that makes any sense. 

So root does chunk of hard drive (hda6) as /export/home or do I have to do that? Also if I want to change the mount name... how can I do that so it works every time I restart the computer?

---

### Post by krisfrajer on 2007-05-13
hey tarus... anyways thnxs for the promptly reply. What you told makes totally sense. I have experience doing partitions in DOS and now that you explain it to me, I can see it. The only thing that surprised me is that ubuntu did those extra steps automatically.

---

### Post by taurus on 2007-05-13
You can mount /dev/hda6 anywhere you want so /export/home is fine too.  You can tell the installer to mount it automatically when you get to the partition part during the installing process or you can add an entry to /etc/fstab later if you wish.  Should be real easy.  And if you want to write to it, you can just change the ownership of /export/home from root to your login name, assuming /dev/hda6 is an ext3 filesystem, with the chmod command.

---

### Post by lneely on 2007-05-13
hda2 is an extended partition.  hda6 is a logical partition inside of hda2.  The Large Disk HOWTO explains it best:  hda2 (your extended partition) is just a box.  You can't use hda2 itself, but rather you would use the partitions inside (hda6, etc.).

You should have a look at the [Large Disk HOWTO]("http://www.linux.com/howtos/Large-Disk-HOWTO-13.shtml").  It should answer any questions you have about partitioning a large hard disk.  Post if you have any more questions about it or don't understand something in the HOWTO.

---

### Post by krisfrajer on 2007-05-13
> **taurus said:**
> You can mount /dev/hda6 anywhere you want so /export/home is fine too.  You can tell the installer to mount it automatically when you get to the partition part during the installing process or you can add an entry to /etc/fstab later if you wish.  Should be real easy.  And if you want to write to it, you can just change the ownership of /export/home from root to your login name, assuming /dev/hda6 is an ext3 filesystem, with the chmod command.

What is that of changing ownership from root to my user name using chmod? What is the use of doing this? Does it mean that when I am as the root user, I will not have access to /export/home? Does it mean also that if I am under my login name (i.e. Cristian) then everytime I save a file in my HD, would that file be saved in my /export/home device?

Also one more thing. Assuming (I emphasize this ... assuming) I did not created that extra partition... taht I mount linux in all my 200GB HD, where would my files be saved? in the directory /home/cristian? (here cristian is my user login name)

I check my /dev/hda6 as it is a ext3 file system: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=601d89de-166e-485f-bd7f-9464a7586628 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=15d9b8bd-c34f-477a-87b8-a54400855074 /export/home    ext3    defaults        0       2
# /dev/hdb1
UUID=C800E53F00E534DA /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=43628781-6785-4072-8766-2ec290bbd01a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
root@NARUTO:/etc#

---

