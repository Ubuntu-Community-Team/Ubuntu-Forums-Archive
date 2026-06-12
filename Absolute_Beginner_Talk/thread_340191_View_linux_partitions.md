---
title: "View linux partitions?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Gritz on 2007-01-16
In Windows I can view the partitions of my hard drive by going to Explorer ... I see C:\, D:\,E:\ etc. I can view all the contents in each individual partition.  Is it possible to do the same in Ubuntu?  That is, see the files on each partition? :confused: :confused:

---

### Post by bodhi.zazen on 2007-01-16
> **Gritz said:**
> In Windows I can view the partitions of my hard drive by going to Explorer ... I see C:\, D:\,E:\ etc. I can view all the contents in each individual partition.  Is it possible to do the same in Ubuntu?  That is, see the files on each partition? :confused: :confused:

Mounting and permissions depends on the file system:

_Windows:_

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by x1a4 on 2007-01-16
UNIX and Linux systems integrate partitions into the directory structure.  

On my system for example the */tmp* directory is actually a separate partition, so is */boot* with everything else on yet another partition.  I also have a partition which holds all my documents mounted on */docs*.  When I installed XUbuntu I just created a symlink in my home directory pointing to */docs* and all my documents (music, photos, spreadsheets etc.) appeared in */home/x1a4/docs*.  

So...If I want to view files in the partition holding my documents I look in */docs* or */home/x1a4/docs*.  To see what I have in the partition I designated to hold temporary files I look in */tmp*

To view/edit your partitions look in /etc/fstab (although I think Ubuntu changed this and uses something else) or use an app like *parted* (command line partition tool), the GNOME Partition Editor (*gparted*), QtParted (*qtparted*) (a Partition Magic clone) or any other of the multitude of partition tools out there.  

Try Googling "[Linux partition manager](http://www.google.ca/search?q=Linux+partition+manager)"

---

### Post by armware on 2007-01-16
to view all partitions on all drives in windows, don't rely on what's in 'My Computer', there is a much better tool built in.
right click 'My Computer'->Manage->Storage->Disk Management

enjoy

---

### Post by Gritz on 2007-01-16
Thanks guys .....  this will be my tomorrow's project (lesson) since it's way past my bedtime.
I GREATLY appreciate all the advice ................

---

### Post by randomnumber on 2007-01-17
I just want to comment that Linux has what you are talking about done the correct way. Windows got it wrong. Has to do with multiuser environment. File permissions seem to be a pain when you first transfer from windows but you eventually figure out that they are great. C: etc are not logical when you get into networks.

Example, at our school we have a network drive on the windows machines called H:. But if I was to attach a few usb drives etc. Then the drive letter come into question. Will it be H: or will it be I: etc.

Good luck with you experience.

---

### Post by Spitphire on 2008-01-26
I think this is what your asking for:

```

am@lp:~$ sudo /sbin/fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22932292

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9327    74919096   83  Linux
/dev/hda2            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

```

```

am@lp:~$ sudo mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

```

am@lp:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             73742752   4436612  65560188   7% /
varrun                 1021676       192   1021484   1% /var/run
varlock                1021676         0   1021676   0% /var/lock
udev                   1021676        72   1021604   1% /dev
devshm                 1021676         0   1021676   0% /dev/shm
lrm                    1021676     34696    986980   4% /lib/modules/2.6.22-14-generic/volatile

```

---

