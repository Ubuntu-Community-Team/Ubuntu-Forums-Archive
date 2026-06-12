---
title: "Permissions for windows partitions still unavailable"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Baasha on 2006-05-27
I have read through the many threads regarding this subject, and as far as I know I have done everything.  I have my two Windows partitions hda1 and hda2 mounted as read only.

The last two lines of my fstab file are as follows:

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda2 /windows ntfs nls=utf8,umask=0222 0 0

However, as a user I still can not access these partitions.  If I get into Nautilus using gksudu I can see and copy my files from the Windows partitions into a FAT32 partition that I set up on my Ubuntu drive, so I know the files are available.

What more do I need to do to get permission to read these files as a regular user.  At the moment, if I right click on either of the Windows partions in the Desktop it tells me the owner is / and that I can't change the permission.  From what I have read, the edit of the fstab file should have corrected this problem.

Thanks in advance,
Bob

---

### Post by aysiu on 2006-05-27
Since we want to make sure we've covered all the possibilities... have you tried rebooting?

---

### Post by Baasha on 2006-05-27
Yes, I have rebooted several times and I also did the mount -a command in the terminal, but still no luck.

One thing I did notice in the initial Ubuntu screen, that shows when you are booting up, is that it says mounting local files --- failed.  I have access to all other parts of Ubuntu so I am not sure whether this is connected to my problem or not.

Bob

---

### Post by aysiu on 2006-05-27
That's really strange. It looks as if you've done everything right.

Just in case, you can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Maybe someone (not necessarily me) will have a brilliant idea about some step you're missing; though, I highly doubt it.

---

### Post by Baasha on 2006-05-27
bob@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         914     7341673+   7  HPFS/NTFS
/dev/hda2             915        7475    52701232+   7  HPFS/NTFS

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974       24321   187542810    5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris
/dev/sda6           23161       24133     7815591    b  W95 FAT32
/dev/sda7             974       23159   178208982   83  Linux

Partition table entries are not in disk order
bob@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.4G  1.9G  5.1G  28% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/sda7             168G  148M  159G   1% /home
/dev/hda1             7.1G  3.6G  3.5G  51% /media/hda1
/dev/hda2              51G   10G   41G  20% /media/hda2
/dev/sda6             7.5G   48K  7.5G   1% /media/sda6
bob@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/sda6       /media/sda6     vfat    defaults        0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/hda2 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by aysiu on 2006-05-27
Ah, simple! Each partition appears twice in your /etc/fstab: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda7 /home ext3 defaults 0 2
[b]/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda2 /media/hda2 ntfs defaults 0 0[/b]
/dev/sda6 /media/sda6 vfat defaults 0 0
/dev/sda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
[b]/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/hda2 /media/windows ntfs nls=utf8,umask=0222 0 0[/b]
``` To be safe, let's mount them at /windows instead of inside the /media folder. Just do ```
sudo umount /dev/hda1
sudo umount /dev/hda2
sudo mkdir /windows1
sudo mkdir /windows2
sudo nano /etc/fstab
``` Delete the offending entries, change the two good entries to be ```
/dev/hda1 /windows1 ntfs nls=utf8,umask=0222 0 0
/dev/hda2 /windows2 ntfs nls=utf8,umask=0222 0 0
``` and then ```
sudo mount -a
```

---

### Post by Baasha on 2006-05-27
That did it!  Thanks for the help.

I realise now where the problem originated.  In the many threads on this subject, I believe the instructions given say "Add lines to the fstab file"  where in fact it appears the instructions should be to edit the lines.

Anyway, now it works.

Thanks again,
Bob

---

