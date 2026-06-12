---
title: "Odd behavior in nautilus"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by phil54601 on 2007-02-23
Hello all;
Yesterday I found a virus on my Ubuntu installation.  It was a downloader for 'trogan 656' according to clamav virus scanner.  Today I noticed that when I access a file on /dev/hdc7 (which is my second HDD and used as a go-between for Win2000 & Ubuntu) that in nautilus, I am listed as owner & my group 'phil' is correct.  But when I select a file or folder on that drive & try to change the permissions, the 'check mark' just flashes.   The permissions are 'rwx' for owner, 'group' & 'others' is only 'r-x'.   Trying to add 'w' for either of them is where the trouble is.  Is this more virus behavior, a corrupted installation of Ubuntu,or what?
Thanks
Phil

---

### Post by chggr on 2007-02-23
What is the filesystem of hdc7

Linux cannot write on NTFS Volumes, so if the filesystem is NTFS, it's pretty logical that the w flag cannot be enabled.

---

### Post by steve.horsley on 2007-02-23
Neither FAT nor NTFS can store Unix permissions flags, so any differences between owner, group and world permissions is artificially created, defined at the time the drive is mounted. The command **mount** lists mounted drives and will show a umode, which is the inverse of the permissions flags that are emulated.

---

### Post by phil54601 on 2007-02-27
Hello All;
Sorry for the over site.  The file system is fat32.   Here is the output from 'sudo mount':

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/hda6 on /mnt/Linux2 type ext3 (rw)
/dev/hda7 on /mnt/LinWin type vfat (rw,uid=1000,gid=1000)
/dev/hdc6 on /mnt/Drv_E_on_60GB_Disk type vfat (rw,uid=1000,gid=1000)
/dev/hdc7 on /mnt/Future_Linux_disk_2 type vfat (rw,uid=1000,gid=1000)
/dev/hdc8 on /mnt/Drv_2_hdc8_G type vfat (rw,uid=1000,gid=1000)
I don't quite follow your comments about 'umode'?

Here are some of the fstab lines:
/dev/hdc6  /mnt/Drv_E_on_60GB_Disk  	vfat auto,uid=1000,gid=1000     	0       0
/dev/hdc7  /mnt/Future_Linux_disk_2  	vfat auto,uid=1000,gid=1000     	0       0
/dev/hdc8  /mnt/Drv_2_hdc8_G 		vfat defaults,uid=1000,gid=1000     	0       0
Some of the strange behavior was the 'rt. click' menu had 'rename' greyed out & nautilus said the drive was 'read only'.  Those problems have corrected them selves.
Thanks
Phil

---

