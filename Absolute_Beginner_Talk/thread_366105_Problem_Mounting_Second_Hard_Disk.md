---
title: "Problem Mounting Second Hard Disk"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by tkennedy13 on 2007-02-20
I'm having a bit of trouble getting a second hard drive to mount properly (i.e. the way I want it). I have a second hard disk that was an NTFS disk that was mounding fine. Since I'm no longer using Windows, I used GNOME Partition Editor and removed the partition, created a new partition and formated it as ext3. Now that I have a nice  clean ext3 partition I'm trying to get it to mount as hdb1 when Ubuntu boots. I order to do this I have edited /etc/fstab and removed the entry for the NTFS partition and added a line for the new ext3 partition. I have tried several different methods and the partition will mount, but it mounts as read only

This is a copy of my current /etc/fstab file. The drive does mount (I see it on my desktop) but it is read only.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=c8923f48-004a-434d-9ecb-4b07f5146c12 /    ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
#/dev/hdb1 	/media/hdb1	ext3	defaults	0	0
UUID=912a6480-ce89-4623-a971-f94c40657d5b /media/hdb1  ext3     defaults 0       1
# /dev/hda1
UUID=0cf85f36-6a61-43ff-92d1-bda3039db2e3 none            swap    sw              0       0

```

The mount command returns:

```

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hdb1 on /media/hdb1 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

So it looks like the file system should be read/write, but if I look at the mount properties (through GNOME) it shows that the owner is root and the group is root. I'm guessing this is why I cannot access the partition? How can I mount the partition so that anyone that logs in has rw access to it? Is it better to give permissions only to a particular user group (the one with my ID in it)?

Ohh and one other thing I am curious about. Is there a way to mount the drive and not have it show on my GNOME desktop, but still have it show under the Places menu?

---

### Post by taurus on 2007-02-20
You need to change the ownership of /media/hdb1 (not /dev/hdb1) so you can write to it.  Assuming your login name is kennedy, open a terminal and do

```
sudo chown -R kennedy:kennedy /media/hdb1
ls -la /media
```

---

### Post by wortel on 2007-02-20
Will this permanently change the permissions? I've seen a directory's owner etc. change as it is mounted/umounted

---

### Post by taurus on 2007-02-20
> **wortel said:**
> Will this permanently change the permissions? I've seen a directory's owner etc. change as it is mounted/umounted

Yes, that would change /media/hdb1 to owner kennedy permanently.

---

### Post by glabouni on 2007-02-20
permanently until you change it again to someone else using the same command: chown

---

### Post by tkennedy13 on 2007-02-24
> **taurus said:**
> Yes, that would change /media/hdb1 to owner kennedy permanently.

Would this allow every user that logs in to have read/write access to the drive? I thought that this could be done through FSTAB...? I thought that I could use *rw,user* mount option (which I tried), but it doesn't seem to work for me. Am I not understanding what this option does?

---

### Post by taurus on 2007-02-24
If you want everybody to read and write to /media/hdb1, then do

```
sudo chmod -R 777 /media/hdb1
```

---

### Post by tkennedy13 on 2007-02-26
> **taurus said:**
> If you want everybody to read and write to /media/hdb1, then do

```
sudo chmod -R 777 /media/hdb1
```

Thanks for your help, this worked. It's odd to me that the FSTAB settings don't seem to affect the drive. I guess I just don't understand FSTAB. I'll have to keep reading on it. 

thanks for your help taurus.

---

### Post by bodhi.zazen on 2007-02-26
It is odd, but mounting and permissions depend on the file system.

Here is a link of fstab : [http://www.ubuntuforums.org/showthread.php?t=283131](http://www.ubuntuforums.org/showthread.php?t=283131)

Also, ownership of the mount point /media/hdb1 will change with mount/umount.

When the partition is mounted ownership will be  kennedy:kennedy

If you unmount the partition, ownership will revert to root:root

That should be no problem :)

---

