---
title: "QTParted &amp; GParted inconsistent"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by phil54601 on 2007-01-30
Hello;
I have 2 hard drives installed, hda and hdc. I dual boot to XP & Ubuntu, by selecting which drive to boot from in Bios setup.  I eventually want to dual boot with only the second drive installed. I use fstab to automount all the hda partitions, and hdc6.  The  inconsistency stems from QTParted showing the swap partition as hda5, and GParted showing it as hda9.  This is the output from 'mount' with fstab matching GParted:

phil@phil-t23:~$ mount
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda5 on /home/phil/LinWin type vfat (rw,umask=0000)
/dev/hda6 on /home/phil/linux2 type vfat (rw,umask=0000)
/dev/hda7 on /home/phil/linux3 type vfat (rw,umask=0000)
/dev/hda8 on /home/phil/linux5 type vfat (rw,umask=0000)
/dev/hdc6 on /home/phil/Drv_'E'_on_disk#2 type vfat (rw,umask=0000)
phil@phil-t23:~$

The LinWin folder contains one empty subfolder '2203 PMT Hard', which is on hda5.  This matches Gparted.  If I modify fstab to match QTParted, and reboot, the LinWin folder is empty, & hda9 doesn't get mounted.  Disk manager agrees with GParted, swap is on /dev/hda5.
This all inclines me to think that QTParted is not reporting hda correctly.  Is this correct?  Where does '2203 PMT Hard' come from -- Possibly XP? Please Help me undestand?
Phil

---

### Post by n8bounds on 2007-02-25
```

sudo fdisk -l

``` 
is never wrong, only difficult to read at first:  just base everything off it's output

---

