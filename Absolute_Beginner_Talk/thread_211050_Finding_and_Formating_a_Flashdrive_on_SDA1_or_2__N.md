---
title: "Finding and Formating a Flashdrive on SDA1 or 2  Need Help"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by vierranet on 2006-07-07
Tried the folliwing:

vierranet@vierranet1:~$ sudo mkdosfs /dev/sda1
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: /dev/sda1 contains a mounted file system.

I'm assuming this is my HD? - What command do I use to find my flashdrive?

Also tried:

vierranet@vierranet1:~$ sudo mkdosfs /dev/sdb1
mkdosfs 2.11 (12 Mar 2005)
/dev/sdb1: No such file or directory

So my question is how do find my flash drive? And, I do I format it?

](*,) Vince

---

### Post by Bloch on 2006-07-07
Use 
mount
to see all mounted devices. Your hard drive will be hda or hdb, and the partition on it (even if there is only one) will be hda1 hda2 etc

> /dev/sda1 contains a mounted file system.
That sounds like your flash memory device. You must umount it before any formatting.
umount /dev/sda1


Or use synaptic to download gparted
This is a tool to show and create partitions on all your disks and format them.

Was the device not formatted when you bought it?

---

### Post by vierranet on 2006-07-07
Dear Bloch,

Thank you for the info. downloading gparted now. I'm assuming it was formatted, but I had a lot of MS files on it and I just want to wipe them off the Flashdrive completely.

One other question please? Whats the command for umounting it before any formatting is done?

Thank You,

Vince

---

### Post by Bloch on 2006-07-07
If it is mounted it should appear as an icon on your desktop. You have the default gnome desktop, do you?

Enter 
mount
to see what devices are mounted.  Then
umount /dev/sda1
(or whatever location the device is) will unmount.
But it is strange that it does not appear when you plug it in. Is there data on it? At what location is it mounted?

> ut I had a lot of MS files on it and I just want to wipe them off the Flashdrive completely.
Why not just delete them? NOTE you have to empty the waste basket after deleting files on a flash drive. The system creates a hidden waste fil on the drive. This makes sense if the drive is an external hard drive, but is just hassle when it is a 128MB memory stick. It's a known bug

---

### Post by vierranet on 2006-07-07
Dear Bloch,

Without Flash: So Far.

vierranet@vierranet1:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
vierranet@vierranet1:~$

With Flash: So Far So Good.

vierranet@vierranet1:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
vierranet@vierranet1:~$

Problem: 

vierranet@vierranet1:~$ umount /dev/sda1
umount: /dev/sda1 is not in the fstab (and you are not root)
vierranet@vierranet1:~$

Now What? Nevermind...

I got it, I was able to unmount using gparted, and I am formating it now... Thank You very much for time and you help, it was and is very appreciated...

Vince

---

### Post by Ptero-4 on 2006-07-07
It probably isn't in /etc/fstab b/c it's mounted by the hotplug/hal/dbus subsystem which does the Plug&Play stuf on linux. you need to append sudo in front of the unmount command for it to work.

---

