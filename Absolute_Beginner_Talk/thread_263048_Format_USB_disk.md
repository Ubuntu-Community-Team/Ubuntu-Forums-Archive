---
title: "Format USB disk?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by pompiuses on 2006-09-22
I need to format my USB disk. How can I do that?

It's mountet in /media/usbdisk and I have root access.

---

### Post by andypaxo on 2006-09-22
If you are happy with the command line, find out about mkfs for formatting.

If you are more comfortable with a graphical interface, try gparted (which you can get through apt - or it might even be in the default install, can't remember right now).

When dealing with formatting disks, you don't want them mounted. Unmount the disk and use /dev/whateveryourdiskiscalled.
(Could someone give instructions on how to find out what the disk is called on the filesystem, please?)

Hope this helps

---

### Post by pompiuses on 2006-09-22
When I mount it I see the following files
/dev/disk/by-id/usb-Crucial_Gizmo__overdrive_02110000000000000000148F
/dev/disk/by-id/usb-Crucial_Gizmo__overdrive_02110000000000000000148F-part1
/dev/disk/by-path/usb-02110000000000000000148F:0:0:0
/dev/disk/by-path/usb-02110000000000000000148F:0:0:0-part1

So I have to format one of those files?

---

### Post by crokett on 2006-09-22
What does ```
mount
``` show you?  

It will list /dev/<somedevice>  mounted to /media/usbdrive

---

### Post by pompiuses on 2006-09-22
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda7 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda1 on /media/hda2 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid =1000,gid=1000,umask=077,iocharset=utf8

---

### Post by Haegin on 2006-09-22
ok
Open gparted (install from synaptic if you dont have it) and delete all the partitions on /dev/sda and create a new single partition on the drive. apply changes and your done. remember you will lose all your data on the stick.

---

### Post by crokett on 2006-09-22
> **Human Prototype said:**
> ok
Open gparted (install from synaptic if you dont have it) and delete all the partitions on /dev/sda and create a new single partition on the drive. apply changes and your done. remember you will lose all your data on the stick.

Yup.  But you need to unmount the drive first:

```
sudo umount /media/usbdrive 
```

---

