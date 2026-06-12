---
title: "Cannot Open home directory or any folder"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by moooody on 2007-06-03
Hi, 
I have been using ubuntu for a while... 
Well..I trying to download and installing ubuntu studio.... when I was done .... I couldn't open my home folder or any other folder or external drive. I restarted and now the desktop disappeared and I cannot right click or open any folder. I tried to oepn it with NAUTILUS. I was able to find home folder and all the files. but still I cannot access any thing from the menue.. Also I forget to mention that I cannot access trash also. 

 any tips

---

### Post by sandwitch on 2007-06-03
wow that's a serious problem :(
Can you run a terminal and become root with sudo su -?
If that works examine the output of the mount command and compare it with /etc/fstab...
Is everything mounted were it should? And is it mounted with the correct options?

I'll check later again..

---

### Post by moooody on 2007-06-03
when I did mount             this is what I got:

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
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

I don't know much... but sda2 on /type ext3 have and error.
I have two partition .....XP First partition.C          and Ubuntu on second partition..
any help..

---

### Post by annda on 2007-06-03
can you also tell us what your /etc/fstab file looks like?

also, what are the permissions of the files in your home folder?

---

