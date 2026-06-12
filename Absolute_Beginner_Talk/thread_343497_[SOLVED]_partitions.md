---
title: "[SOLVED] partitions"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-01-21
is there a way to rename partitions or mount points

---

### Post by taurus on 2007-01-21
Mount point, yes.  Unmount the drive first, create a new mount point, and mount it to the new mount point.

---

### Post by Ecthelion on 2007-01-21
You can easely rename mountpoints.

Just make a dir at the place you want them to mount, and change your fstab to make it mount your disk in that dir.
If tyour not sure how to do, post your fstab and the place where you want it to mount your disk.
```
cat /etc/fstab
```

---

### Post by rusty4r on 2007-01-21
sorry for being so new but how do i do that?

---

### Post by taurus on 2007-01-21
Where do you want to mount it (new mount point) and what drive/partition you want to mount it to that new mount point?  Post your /etc/fstab here if you have it mount automatically upon boot.

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by rusty4r on 2007-01-21
for example i would like to change "documents" to say "shared" here is what came up when i put in whatever that was that you told me to do again please excuse my ignorance but i love learning this stuff # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdf1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdf3       /documents      vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdf6       /firstblank     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdf10      /fourthblank    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdf2       /home           ext3    defaults        0       2
/dev/hdf5       /programs       vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdf7       /secondblank    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdf8       /thirdblank     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hde1       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hde5       /winpro         vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdf9       none            swap    sw              0       0
/dev/hdh        /media/cdrom0   udf,iso9660 user,noauto     0       0
rusty@rusty-desktop:~$

---

### Post by taurus on 2007-01-21
Edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line
```
/dev/hdf3 /documents vfat defaults,utf8,umask=007,gid=46 0 1
```
with this line.
```
/dev/hdf3 /shared vfat defaults,utf8,umask=007,gid=46 0 1
```
Save the change.  Now, create a new mount point for /dev/hdf3.

```
sudo mkdir /shared
```
Reboot and see if /dev/hdf3 mounted to /shared.

```
df -h
```

---

### Post by rusty4r on 2007-01-21
Thanks Taurus that worked great. in the file browser it still shows an icon for "documents" but also one for "shared" should i just delete that icon now

---

### Post by taurus on 2007-01-21
There shouldn't be anything in documents so you can check to be sure.  Then, delete it.

---

### Post by rusty4r on 2007-01-21
it is empty but it wont let me delete it says i am not the owner

---

### Post by taurus on 2007-01-21
Applications -> Accessories -> Terminal
```
sudo rmdir /documents
```

---

### Post by rusty4r on 2007-01-21
Yes sir its gone thanks again you are the man

---

