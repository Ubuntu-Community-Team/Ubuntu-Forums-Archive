---
title: "Problem w/ USB"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by migstriker on 2007-09-04
I installed Ubuntu yesterday, and everything worked just fine. 
Today, I used my USB external HDD, which worked fine as well, but after rebooting no USB device worked. I tried looking through similar threads but couldn't find any answers.

I hope somebody has an answer to this problem,
mike

---

### Post by GMachine_24 on 2007-09-04
> **migstriker said:**
> I installed Ubuntu yesterday, and everything worked just fine. 
Today, I used my USB external HDD, which worked fine as well, but after rebooting no USB device worked. I tried looking through similar threads but couldn't find any answers.

I hope somebody has an answer to this problem,
mike

Hi. This seems to be a fairly good answer. Have you checked it out?

[http://ubuntuforums.org/showthread.php?t=506623](http://ubuntuforums.org/showthread.php?t=506623)


--gm

---

### Post by vanadium on 2007-09-04
This link is just a shot in the dark and utterly confusing for a new user. To the original poster: be as specific as you can. In principle, USB drives should mount automatically. In order to see whether Linux "sees" the drive, make sure it is connected and turned on, then post the output here of the command "sudo fdisk -l". Additionally, to see what is mounted in your system, post the output here of the command "mount". From this information, we might be able to give further tips that help troubleshooting or at least narrow down the problem.

To copy you output here 1) open a terminal 2) run the command 3) select the output (including the command) with the mouse 4) press Shift+Ctrl+C (not just Ctrl+C) and 5) paste it in your message.

---

### Post by migstriker on 2007-09-05
**Thank you for the answers. When I run the sudo fdisk -l command, I get the following output from console:**

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris
[B]
The output for the mount command is as follows:[/B]

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
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
/dev/sda1 on /mnt/usb type ext3 (rw)

The USB ports get electricity, my USB fan will work just fine in case that helps.
Regards, Mike

---

### Post by migstriker on 2007-09-06
As of today, Ubuntu doesn't recognise the soundcard. Please help me, I would really like to continue using Ubuntu.

---

