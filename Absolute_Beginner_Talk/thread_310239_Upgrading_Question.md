---
title: "Upgrading Question"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by marcusgleason on 2006-11-30
New to Linux, currently running Dapper.  Since this was my first delve into the world of Linux, I have naturally made a mess of my current setup:p .  I wanted to upgrade to Edgy, so I downloaded the image.  I have my hard drive partitioned three ways: 1 for the OS install, 1 for all of the downloaded files after the install (music mainly), and 1 for the swap partition.  If I run the iso disc I just burned, will it format all of my partitions, or can I select which partition(s) to format?

---

### Post by loell on 2006-11-30
yes, you will have a choice on which partition to format

---

### Post by marcusgleason on 2006-12-01
Okay, new problem now.  I tried to update to Edgy but the disk I burned it to had errors.  I edited my partition table, left the one partition that had all of the music and other files I wanted to keep, and installed Dapper back on the boot partition.  I am only showing a main partition and a swap partition mounted.  I cannot figure out how to mount the old partition I had.  Half my hard drive is hidden haha.  I *believe* it is sda1, but it could be sda2 or 3.

When I type mount at the terminal, below is what I get:

root@marcus-desktop:~# mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
tmpfs on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw,mode=0755)

Thanks for your help.

---

### Post by loell on 2006-12-01
you can restart, and run the livecd again , click on install icon ,then you can view the name of the partion where your music is stored.go back to the installed dapper on your system, you can now add that partition in fstab.

after adding that partition to /etc/fstab, reload fstab by

```
sudo mount -a
```

---

### Post by igknighted on 2006-12-01
When you go to install edgy try this:  in the same screen where you select what partitions to format, click on the partition you want to save and then 'edit' and enter a mount point for it (I personally like /storage or something like that, but you could mount it in your home directory by /home/<username>/storage).  This way, when the system is set up you just navigate in you file browser to the folder you specified and access will be automatically set up.

---

