---
title: "FAT32 Partition Write Permission?"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Kid G on 2006-03-02
HI,

I got a new harddrive recently and set up a 50Gb FAt32 partition to share files with Windows - but I cant copy/cut and paste files into it. How do I permanently change the permissions for this partition?

Here are the contents of /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hdb5       /media/hdb5     vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


hdb5 is the partition in question.

---

### Post by Q4U on 2006-03-02
As far as I know, permissions are per-file, unless you mount your partition as read-only (ro) which is not you case, judging from what you posted. 

I guess you have to change the permission of the files you want to copy, rather than doing anything with the partition.

Q4U

---

### Post by Kid G on 2006-03-02
This is my second Ubuntu installation and I didnt have this problem with my Fat32 partition the first time - I'm just not sure what I did differently this time :confused: 

G

---

### Post by Q4U on 2006-03-02
This is not necessarily a problem.

Perhaps the first time you created the files logged in as the same user that tried to move them around, while this time you created the files are root  and then tried to operate on them while logged in as a user.

Try to see the ownership of the files and permissions with ls -l, and if necessary change them with chmod.

Let us know if this solves your problem. ;) 

Q4U

---

### Post by ebutton on 2006-03-02
I know that when I start nautilus (File Browser), as root, I see that I have full permissions on my M$ partition.  I think that I had to change my nautilus options to see the permissions.

I also tested by copying a file to my desktop, renaming it, then pasted it back to my M$ partition.  It works! ... however, there may be a much safer way.  (I'm a newbie too.)

Regards,
EdB

---

### Post by Sutekh on 2006-03-02
Change these lines
[QUOTE=Kid G]
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hdb5       /media/hdb5     vfat    defaults        0       0[/QUOTE]
To these lines
```
/dev/hda1      /media/hda1     vfat    iocharset=utf8,umask=0000    0    0
/dev/hda2      /media/hda2     ntfs    nls=utf8,umask=0222          0    0
/dev/hdb5      /media/hda5     vfat    iocharset=utf8,umask=0000    0    0
```
Then use
```
sudo mount -a
```
To remount the partitions

This will make the FAT32 partitions have full access, and the NTFS partition read/execute access.

Read this link for more info

[http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

---

### Post by bailout on 2006-03-02
What does the iocharset=utf8 do? Sometimes people recomend using it and others leave it out.

---

### Post by Sutekh on 2006-03-02
I'm hopeless at explaining things like this.  If you have special charaters (such as é) on the partition, you need iocharset=utf8 so that you won't get an encoding error

I don't think it could ever be a problem though

---

### Post by Kid G on 2006-03-02
Thanks for the help

Hda1 and hda5 are now both accessable but I still cant write to hdb5 - the FAT32 partition. I also tried creating a fat_files directory but permissions are still set at root?

G

---

### Post by aysiu on 2006-03-02
Can you post your modified /etc/fstab?

---

### Post by Kid G on 2006-03-02
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    iocharset=utf8,umask=0000    0    0
/dev/hda2       /media/hda2     ntfs    nls=utf8,umask=0222          0    0
/dev/hdb5       /media/hdb5     vfat    iocharset=utf8,umask=0000    0    0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I also tried the following: 
sudo umount /dev/hdb5
sudo mkdir /fat_files
 
That directory is still in my file system if that makes any difference?

---

### Post by aysiu on 2006-03-02
[QUOTE=Kid G]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    iocharset=utf8,umask=0000    0    0
/dev/hda2       /media/hda2     ntfs    nls=utf8,umask=0222          0    0
/dev/hdb5       /media/hdb5     vfat    iocharset=utf8,umask=0000    0    0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I also tried the following: 
sudo umount /dev/hdb5
sudo mkdir /fat_files
 
That directory is still in my file system if that makes any difference?[/QUOTE] That confuses me, as your previous post said you could access /dev/hda5--that's the swap file... > Hda1 and hda5 are now both accessable but I still cant write to hdb5 - the FAT32 partition. I also tried creating a fat_files directory but permissions are still set at root? I don't know if it makes a difference, but I usually do ```
umask=000 0 0
``` instead of ```
umask=0000 0 0
``` Also, it's not enough to just make the directory called /fat_files. You actually have to tell /etc/fstab to mount your partition there. Change this line ```
/dev/hdb5       /media/hdb5     vfat    iocharset=utf8,umask=0000    0    0
``` to this line ```
/dev/hdb5       /fat_files     vfat    iocharset=utf8,umask=000    0    0
``` and then do ```
sudo umount /dev/hdb5
sudo mount -a
```

---

### Post by Kid G on 2006-03-02
Seems to be working now! 

Thanks for the help :D

---

### Post by aysiu on 2006-03-03
[QUOTE=Kid G]Seems to be working now! 

Thanks for the help :D[/QUOTE] No problem. Glad it worked out for you.

---

