---
title: "Usb drive mounts read-only"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-04-21
I've just moved to feisty and I have a problem. Automatic mount mounts my pen drive read-only. What is more manual mount -w does the same thing. I don't know what is going on, but I want my usb drive work correctly.

This is my mtab

/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/sda3 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
**/dev/sdb1 /media/SanDisk vfat rw,noexec,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower 0 0**

Thanks in advance. Oh, if it matters, then I'm using KDE 3.5.6.

---

### Post by ggaaron on 2007-04-21
Something is terribly wrong. I've managed to mount it with mount -o rw, but only for a short period of time and now it says system is read-only.

---

