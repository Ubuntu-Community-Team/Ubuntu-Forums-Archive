---
title: "[SOLVED] Drive loses permission at startup"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2007-08-21
I'm new to Linux and have reinstalled it a few times to make up for some problems I've caused.  Right now I have my dual boot setup working OK and I have been able to fix most problems.  I have two hard drives (SATA and PATA).  My second hard drive was formatted as ntfs and after installing ntfs-3g I still wasn't able to write to it.  To make a quick fix, I reformatted the drive as FAT32.  This drive is were all my documents are stored and needs to be accessed by the two OS.  After formatting the drive, every time Ubuntu boots up, I have to open the drive and enter my user password before it is available to my various applications.  I clicked on the drive to change access permissions (read/write to everyone) but the permissions are not carried after I shut down the machine.  How can I change the drive permissions so that the permissions are not reset? TIA

---

### Post by Inxsible on 2007-08-21
I don't think permissions can be set on NTFS or FAT32 drives. These filesystems cannot inherently store permissions.

---

### Post by notbitmonk on 2007-08-22
Well then, is there any way that the drive can be mounted automatically when my systems boots?  These are my fstab and my mount files.
#/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d31c600f-82b4-4605-aab4-2fe9ce91bd91 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4dafa99e-8a57-4bd0-ae72-de4582156277 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

MOUNT AFTER I "LOGGED IN" TO THE DRIVE

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/hda1 on /media/SHAREDDATA type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

---

### Post by schorsch on 2007-08-22
Just edit /etc/fstab
```
gksu gedit /etc/fstab
```
add the following lines to /etc/fstab
```
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1
/dev/hda1 /media/SHAREDDATA vfat rw,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1
```

---

### Post by Terl on 2007-08-22
When I install ntfs3g I always also install ntfsconfig.  Using the config tool lets you set the drives up.  They always automount after that.  It is a very nice tool.  After using the tool I can read/write without a problem.

---

### Post by notbitmonk on 2007-08-22
Terl, unfortunately I reformated the drive as FAT 32 but I'll have your tip handy.

Scorch - I believe I only need to add
/dev/hda1 /media/SHAREDDATA vfat rw,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1
because the previous line refers to my USB flash drive (I think).  By adding that line to my fstab I will have read/write access for all users at boot time, right?  Also, how do I write to fstab and what do all those letters mean? Thanks.

---

### Post by schorsch on 2007-08-22
> **notbitmonk said:**
> /dev/hda1 /media/SHAREDDATA vfat rw,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1
because the previous line refers to my USB flash drive (I think).  By adding that line to my fstab I will have read/write access for all users at boot time, right?  Also, how do I write to fstab and what do all those letters mean? Thanks.
No, the only user that has reda/write access on this drive with these options will be the user with the GID 1000 ... and I guess, that is you. (I just used the options that your output of the mount command gave us). To enable read/write access for everyone you have to use a umask=000. If you want to keep it simple, just use the following line:
```
/dev/hda1 /media/SHAREDDATA vfat defaults,utf8,umask=000,gid=1000,uid=1000 0 1
```
You can edit /etc/fstab with the command I mentioned already before:
```
gksu gedit /etc/fstab
```
For detailed information what these "letters" mean please take a look in the manpage of mount:
```
man mount
```

---

### Post by notbitmonk on 2007-08-22
Thanks.  I should've noticed you already mentioned how to edit fstab.  I'll post back tomorrow on how things went.

---

### Post by notbitmonk on 2007-08-24
Thanks I had to use
```
sudo mount mkdir /mnt/SHAREDDATA
```
or else an error occurred each time.  The fstab line ended being
```
/dev/hda1	/mnt/SHAREDDATA	vfat		defaults,utf8,umask=000,gid=1000,uid=1000	0	0
```

---

