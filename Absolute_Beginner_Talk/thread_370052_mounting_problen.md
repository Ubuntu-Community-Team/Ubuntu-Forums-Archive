---
title: "mounting problen"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by webofunni on 2007-02-25
I had 5 ntfs windows partition and 1 ext3 partition. All my windows partitions are listed at desktop, Since i am not able to write with ntfs I installed ntfs-3g and ntfs-config. After running ntfs config all my partition icon in my desktop get disappeared. But all my partitions are mounted at /media/sd1 /media/sd3 etc . I can read and write with them. But i dont know how to bring up those desktop icons of my windows partitions

---

### Post by givré on 2007-02-25
webofunni, try to reboot.

---

### Post by webofunni on 2007-02-25
Yes i rebooted but i dont get my icons back.

modprobe -l fuse says /lib/modules/2.6.15-26-386/kernel/fs/fuse/fuse.ko 
and when ever i try for rmmod fule it says that module fuse in use

also my attempt to mount ant drive shows following warning

sudo mount /dev/sda1
WARNING: Deficient FUSE kernel module detected. Some driver features are
         not available (swap file on NTFS, boot from NTFS by LILO), and
         unmount is not safe unless it's made sure the ntfs-3g process
         naturally terminates after calling 'umount'. The safe FUSE kernel
         driver is included in the official Linux kernels since version
         2.6.20-rc1, or in the FUSE 2.6.0 or later software packages,
         except the faulty FUSE version 2.6.2. Please see the next page
         for more help: [http://www.ntfs-3g.org/support.html#fuse26](http://www.ntfs-3g.org/support.html#fuse26)


i installes fuse 2.6.3 with --enable-kernel-module but after configuration it says

checking if FUSE is configured in the kernel... yes
configure:
NOTE:     Detected that FUSE is already present in the kernel, so
NOTE:     building of kernel module is disabled.  To force building
NOTE:     of kernel module use the '--enable-kernel-module' option.
configure: creating ./config.status
config.status: creating Makefile

what is the method to remove the older fuse kernal module

---

### Post by givré on 2007-02-25
> Yes i rebooted but i dont get my icons back.
webofunni, like i said in the ntfs-3g forum, it's simply because you missed some bits which you can get via my repo. 
Add my dapper repo. Do :
```
sudo apt-get update
sudo apt-get upgrade
```
reboot
install ntfs-config :
```
sudo apt-get install ntfs-config
```
run ntfs-config (in the menu) if you don't see it, it seams that installation fail, and so you should post the output of your installation. (E means error)

---

### Post by givré on 2007-02-25
Better to continue here [http://forum.ntfs-3g.org/viewtopic.php?p=1023](http://forum.ntfs-3g.org/viewtopic.php?p=1023)

---

### Post by vampire666eng on 2007-09-18
Moved to appropriate forum.
I'm sorry.

---

### Post by vampire666eng on 2007-09-18
Moved to appropriate forum.

---

