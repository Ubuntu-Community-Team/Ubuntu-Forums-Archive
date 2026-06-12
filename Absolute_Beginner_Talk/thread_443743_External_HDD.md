---
title: "External HDD"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by MikeyRibbs on 2007-05-14
It wont let me write to it and it says I don't have permission to write to it. How do I make it let me write to it.

---

### Post by taurus on 2007-05-14
What filesystem is that external harddrive?  If it's ntfs, then you need to install ntfs-3g driver before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by JamieC on 2007-05-14
If you're unsure, post the output of the following (Applications -> Accessories -> Terminal):
```

sudo fdisk -l && mount

```

---

### Post by MikeyRibbs on 2007-05-14
I installed NTFS-3g or whatever and it still wont let me do it.

michael@michael-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        9729    78148161    7  HPFS/NTFS

---

### Post by taurus on 2007-05-14
How did you mount /dev/sdf1 then?

---

### Post by JamieC on 2007-05-14
Post the output of the following (in the terminal) please (to determine what parameters the drive is mounted with):
```

mount

```

---

### Post by MikeyRibbs on 2007-05-14
michael@michael-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdf1 on /media/Mikey type ntfs (rw,nosuid,nodev,umask=222,utf8)

---

### Post by JamieC on 2007-05-14
Run the following in a terminal and then try again:
```

sudo umount /media/Mikey && sudo ntfs-3g /dev/sdf1 /media/Mikey

```

---

### Post by MikeyRibbs on 2007-05-14
Then try what again? the "mount" thing?

---

### Post by JamieC on 2007-05-14
Yup or try actually writing to the drive, sorry for not explaining myself very clearly.

---

### Post by MikeyRibbs on 2007-05-14
michael@michael-desktop:~$ sudo umount /media/Mikey && sudo ntfs-3g /dev/sdf1 /media/Mikey
fusermount: failed to access mountpoint /media/Mikey: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdf1 (Mikey)
michael@michael-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
michael@michael-desktop:~$

edit, so now my comp doesn't even say its here.

---

### Post by JamieC on 2007-05-14
> 
fusermount: failed to access mountpoint /media/Mikey: No such file or directory


That's weird, post the output of this:
```

sudo mkdir /media/Mikey && sudo ntfs-3g /dev/sdf1 /media/Mikey && mount

```

---

### Post by taurus on 2007-05-14
```
sudo mkdir /media/Mikey
sudo **mount -t** ntfs-3g /dev/sdf1 /media/Mikey
df -h
```

---

### Post by MikeyRibbs on 2007-05-14
michael@michael-desktop:~$ sudo mkdir /media/Mikey && sudo ntfs-3g /dev/sdf1 /media/Mikey
michael@michael-desktop:~$

---

### Post by JamieC on 2007-05-14
No error messages, post the output of mount or try writing to the drive to verify that it mounted successfully.

---

### Post by MikeyRibbs on 2007-05-14
It works now, thanks a ton!

---

