---
title: "Auto-mounting a partition"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by tomor on 2008-02-16
Hi, 

I have two disks. In one of them ubuntu is installed and the other one is just for data. I've made two partitions but just one of them is mounted when I start ubuntu and when i try to mount the other one it says permission denied even if i am logged as a root user. So i have to start gparted and mount it from there. How can i make to be automounted?

This is my fstab file: 

> proc /proc proc defaults 0 0
# /dev/hdc1
UUID=8424622f-97c9-4aa3-83fc-185e661fc3b0 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdc5
UUID=7aee9da0-439f-4a17-8965-9672775b4832 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0


/dev/sda1	/media/disk-1	ntfs-3g	defaults,force	0	0 


/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
<device> <mount\040point> auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 /dir1 ext3 nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sda2 /dir2 ext3 nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0

the sda2 is the partition that  i need

---

### Post by benerivo on 2008-02-16
Change the line to```
/dev/sda2 /dir2 ext3 defaults 0 0
```then run 
```
gksudo nautilus
``` 
in a terminal and go to the /dir2 folder. Right click and change the permissions to whatever you want. Then reboot.

---

