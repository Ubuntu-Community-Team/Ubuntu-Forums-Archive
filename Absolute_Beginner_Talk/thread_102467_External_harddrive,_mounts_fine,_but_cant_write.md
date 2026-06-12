---
title: "External harddrive, mounts fine, but cant write"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by qiemem on 2005-12-12
Hi,

Just switched to Linux from WinXP. I have an external harddrive (Western Digital 120gb USB 2.0 if it matters) on which I backup files, keep my music, etc. Anyway, it mounts fine, automatically and everything, and I can read off it (hell, I'm listening to music off it right now), but I can't seem to write to it at all. Its listed as having 0 free space left.  I've looked around for how to fix this, but everything I find either doesn't apply to me (assumes new hard drive, etc) or goes way over my head. What should I do? Obviously, I'd like to keep all my old data.

Thanks in advance :)

---

### Post by frodon on 2005-12-12
Does your harddrive use NTFS ?, if yes you have to know that there's no write support for NTFS with linux. There's just few projects about it but nothing reliable.

---

### Post by Jussi Kukkonen on 2005-12-12
It probably has NTFS file system. That's bad news in the sense that you won't be able to write to it from linux. Do a 
```
sudo fdisk -l
```
to find out what file system your disk has. NTFS will be listed as *HPFS/NTFS*.

If the disk turns out to be FAT instead of ntfs , then this is easy. You'll just have to mount the disk correctly.
If it is NTFS, you'll have to format the disk to be able to write to it.

Post the output from the command I gave, and we'll see.

---

### Post by qiemem on 2005-12-12
ya, i figured this would be coming... honestly, i can't remember. how can i find out? (sorry if this is a dumb question, or if i just overlooked info about it when searching)

EDIT: heh oops Jussi posted while i was writing. thanks for anticipating my question!

---

### Post by qiemem on 2005-12-12
> 
bryan@BryanH:/$ sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6996    56195338+  83  Linux
/dev/sda2            6997        7296     2409750    5  Extended
/dev/sda5            6997        7296     2409718+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241   fd  Linux raid autodetect


hmm... where would it say?

---

### Post by majed on 2005-12-12
Hi quiemem..

can you post the output of these commands:

```
mount
```

and

```
cat /etc/fstab
```

That would give more insight to how it is automatically mounted.. (red only/ read write/ etc..)

---

### Post by qiemem on 2005-12-12
> 
bryan@BryanH:/$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=bryan)
/dev/sdc1 on /media/WD USB 2 type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)


bryan@BryanH:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0

here ya go..

---

### Post by Jussi Kukkonen on 2005-12-12
> ...Linux raid autodetect
Well, it's a little more complicated than I thought, as you seem to have a raid partition. Someone with some experience with those should probably tell you how to proceed here -- I'm not qualified.

*Mount* does indicate the filesystem is vfat, so this should be doable -- you'll just have find the correct mount options and add a line into /etc/fstab.
 By the way, who is the owner of the files on the disk (check with *ls -l* or in nautilus check the file properties window)? your umask setting on */media/WD* seems to be 077, which means only owner has any rights, if I recall correctly...

---

### Post by qiemem on 2005-12-12
> By the way, who is the owner of the files on the disk (check with ls -l or in nautilus check the file properties window)? your umask setting on /media/WD seems to be 077, which means only owner has any rights, if I recall correctly...
it appears my primary account is (bryan).

> 
Mount does indicate the filesystem is vfat, so this should be doable -- you'll just have find the correct mount options and add a line into /etc/fstab.
While I'll certainly do my own looking, I was just wondering if you had any ideas about where to start looking for info on this, as I'm not exactly sure what even to search for (mounting a raid partitioned hard drive maybe?)

Anyway, thank you! You guys have been most helpful and I've even learned a thing or two along the way.

EDIT: I checked for drivers on WD's site and only found MSWin stuff... All posts I've been finding about this stuff are way over my head... Any suggestions?

---

### Post by qiemem on 2005-12-12
Anybody know about mounting RAID partitioned hard drives with read/write capabilities? (see above for specifics) or know where I should go for help on this?

---

### Post by majed on 2005-12-13
hummm... i never worked with RAID.. but reading around, it seems u need to know if this is hardware or software RAID and then go from there...

here are some links that could lead u to something.. (and please post the solution when u find it!) :

[http://linas.org/linux/raid.html]("http://linas.org/linux/raid.html")
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html")
[http://linux.yyz.us/sata/faq-sata-raid.html]("http://linux.yyz.us/sata/faq-sata-raid.html")

---

### Post by qiemem on 2005-12-13
Thanks for the references! It'll take me a while to sift through those bad boys, but at first glance I'm not exactly sure they're really talking about the same thing... Well, they are, but at a very fundamental level... whatever, anyway, I'll look through them and if nothing else learn a bunch.

Anyway, so I was perusing the device manager and it definitly lists the drive as FAT32. It doesn't mention RAID anywhere, but I don't know if that means anything. So I tried the ubuntu documentations guide to mounting fat32 drives, and ran into same problem. No errors or anything, it just lists the drive as completely full (0 free space). Anyway... don't know if this is useful info; just thought I'd post just in case.

---

### Post by eMuNiX on 2005-12-13
What I find with my external drive (Buffalo drivestation 250GB FAT) is that I had to change the permissions to allow it to be writeable by users, ‘chmod –R 777 *’ changes all directories, subdirectories and files to rwx and I can now use the drive normally with the exception of Azureus which refuses to write directly to the drive.

---

### Post by qiemem on 2005-12-13
Ya so, uh, the reason it couldn't write... It said it had 0 bytes left, and I thought there was no way I could've used up every single byte. Just to be sure, I deleted a file, and guess what? Well, thanks for your help everyone. (man I feel like an asshole)

Just out of curiousity, what does a umask of 077 mean? Shouldn't it be 777? (as emunix suggested...)

---

### Post by Jussi Kukkonen on 2005-12-14
Heh, happens in the best families...

077 is fine, it means user has all rights, and Group and Others have no rights. If you want to give other users some rights then change it, otherwise don't.

If you do change the rights, I suggest you use the format 
```
chmod o+rw
```
(gives Others read/write access)
using the number format is trickier since umask and chmod numbers look similar, but are not. Unix user interface design shows its best sides here...

---

