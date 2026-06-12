---
title: "Delete files and directories doesn't work"
date: 2017-01-12
forum: Any Other OS
---

### Post by jambel on 2017-01-12
Hi community,

I'm facing a weird behaviour these days on a Banana Pi ([http://bananapi.com/](http://bananapi.com/)) running Lubuntu.

I've tryed many times to remove a directory under my home directory or move but after a reboot it keeps the whole old structure, even if I use sudo rm -rf ~/mydir

It's like restoring everything in its previous state after reboot. Is that possible? Is there any kind of solution?

Thanks in advance.

---

### Post by geeksmith on 2017-01-12
Does it keep new files that you create? Is the OS running in ramfs/ramdisk, rather than from the non-volatile storage?

---

### Post by jambel on 2017-01-12
No it doesn't keep new files or update of them after reboot. It remains in previous state.
Notice that this behaviour wasn't there from start but lately.

The OS is running in microSD, not sure if I follow you :(

---

### Post by deadflowr on 2017-01-12
Simple answer is your microSD card is set to read-only.
Post the method used to put the os on the card.

---

### Post by jambel on 2017-01-12
sudo dd bs=4M if=/src of=card

This behaviour wasn't from start. It's almost runs 3+ years and everything goes well. No, the card is not read only.

---

### Post by geeksmith on 2017-01-12
Please paste the output of the command "mount" and the contents of /etc/fstab.

I suspect your OS is running in volatile memory (initramfs or ramdisk), so any changes made are lost after a power cycle. In order to keep changes, you'll need to mount non-volatile storage (SDCard, USB flash, HDD, etc.) and store changes there. You could mount one of these to /home to keep changes to your home directory.

---

### Post by jambel on 2017-01-12
from mount"
/dev/root on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
devtmpfs on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1001/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=john)
/dev/mmcblk0p1 on /media/john/324A-3901 type vfat (rw,nosuid,nodev,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

and /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM

Anyway, I will proceed to a new installation but that was very strange to me.

---

### Post by jambel on 2017-01-14
I'm trying to recover the microSD with GParted and after delete partitions, no deletion occurred and get that message:

e2label: No such file or directory while trying to open /dev/sdc2
Couldn't find valid filesystem superblock.

tune2fs 1.42.9 (4-Feb-2014)

tune2fs: No such file or directory while trying to open /dev/sdc2
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.42.9 (4-Feb-2014)
dumpe2fs: No such file or directory while trying to open /dev/sdc2

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.


Is is possible the card became defective?

---

