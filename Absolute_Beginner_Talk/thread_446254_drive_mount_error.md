---
title: "drive mount error"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by elchucko on 2007-05-16
Well, I've been fighting my way along for the last little while with taking suggestions. I recently tried unmounting my sda1 drive, and formatting it. I ended up editing fstab and trying to change the identification of sda1 from ntfs to ext3. After this, I tried to re mount the sda1 partition, but I'm getting an error: 

:~$ sudo mount /dev/sda1
Password:
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/9CF4C389F4C363DC,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


any suggestions?

---

### Post by taurus on 2007-05-16
Can you post 

```
sudo fdisk -l
cat /etc/fstab
```

p.s.  When you reformat a partition, the UUID would change too so you either need to inlcude the new UUID or replace it with /dev/sda1.

---

### Post by elchucko on 2007-05-16
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b49ad7f6-a9c0-4b99-b03f-62fd3849249d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9CF4C389F4C363DC /media/sda1     ntfs   defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4f1ad687-c5c0-4c31-a720-cd269b1f79b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


there ya go, hope you can make some sense of it. 

cheers!

---

### Post by taurus on 2007-05-16
> **elchucko said:**
> :~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b49ad7f6-a9c0-4b99-b03f-62fd3849249d /               ext3    defaults,errors=remount-ro 0       1
[COLOR="Red"][B]# /dev/sda1
UUID=9CF4C389F4C363DC /media/sda1     ntfs   defaults,nls=utf8,umask=007,gid=46 0       1[/B][/COLOR]
# /dev/sda2
UUID=4f1ad687-c5c0-4c31-a720-cd269b1f79b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


there ya go, hope you can make some sense of it. 

cheers!

What about the output of the first command in my previous post?

```
sudo fdisk -l
```
On the other hand, since /dev/sda1 is ext3 filesystem now, how come you still have it down as ntfs in /etc/fstab?  It should now be

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```

---

### Post by elchucko on 2007-05-16
:~$ sudo mount /dev/sda1
Password:
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/9CF4C389F4C363DC,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

charles@neves:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8454    67906723+   7  HPFS/NTFS
/dev/sda2            8455        8578      996030   82  Linux swap / Solaris
/dev/sda3            8579        9729     9245407+  83  Linux
charles@neves:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b49ad7f6-a9c0-4b99-b03f-62fd3849249d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9CF4C389F4C363DC /media/sda1     ntfs   defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4f1ad687-c5c0-4c31-a720-cd269b1f79b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



ok, there's the whole output from the terminal from the commands you asked for. I haven't changed anything yet, just incase you have something else in mind....

---

### Post by taurus on 2007-05-16
How did you convert /dev/sda1 from ntfs to ext3?  It is still ntfs, according to "sudo fdisk -l."  Is there anything on /dev/sda1 that needs to be saved first?

---

### Post by elchucko on 2007-05-16
[http://ubuntuforums.org/showthread.php?t=446145](http://ubuntuforums.org/showthread.php?t=446145)

that's where I started this process, there's nothing on the drive that I wish to save, I'm just planning on using it for file storage once I get it formatted and re-mounted.

---

### Post by taurus on 2007-05-16
Okay, try to reformat it again.

```
sudo mke2fs -j /dev/sda1
```
Then, you need to edit /etc/fstab 

```
gksudo gedit /etc/fstab
```
and replace his line

```
UUID=9CF4C389F4C363DC /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
with this one.

```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
Save the change.  Then, mount it and change the ownership of /media/sda1 from root to your login name so you can write to it.

```
sudo mount -a
sudo chown -R **username**:**username** /media/sda1
ls -la /media
```
Replace **username** with your actual login name.

---

