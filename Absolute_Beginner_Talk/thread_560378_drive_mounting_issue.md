---
title: "drive mounting issue"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Kindredgarou on 2007-09-26
Hi guys I just managed to get fiesty to install after some probs but have found that my boot drive is mounted to /media i have tried to unmount using gnome PE and the use the  sudo mount -t vfat /dev/hda5 /root cmd and i get 

ubuntu@ubuntu:~$ sudo mount -t vfat /dev/hda5 /root
mount: /dev/hda5 already mounted or /root busy
mount: according to mtab, /dev/hda5 is mounted on /media/disk-2

as my output any help would be appreciated

also as a note i installe using a third physical hdd as my primary master (had winxp on) as was only way i could get to boot to live disk) after install i disconnected this could that have affected the system?

Also is there anyway to change to my user account so i can use my access rights?

---

### Post by justleen on 2007-09-26
your boot drive is not the same as your root drive..

looking at your mount command, you are trying to mount it as vfat, so i recon you mean you try to mount your windows boot drive.
your / (root dir, which is not the same as /root!) is already mounted.
you are nou trying to mount a partition to your /root dir.. why do you want to do this? this not common practice, unless you want a separate partition for /root - but again, is that what you want?

another point, its already mounted to /media/disk-2, suggesting that this is no primary/first partition anyway..

further,  what do you mean with gnome-PE? 
normally, you can unmount by right clicking on the drive, and select "unmount"
if that wount work, you can unmount it with ```
sudo umount /media/disk-2
```

please post the output of "sudo fdisk -l " and "sudo mount " so we have some more details on your disk config.

---

### Post by Kindredgarou on 2007-09-26
ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb3 on /media/disk type ext2 (rw,noexec,nosuid,nodev)
/dev/hdb2 on /media/disk-1 type ext2 (rw,noexec,nosuid,nodev)
/dev/hda1 on /media/disk-3 type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077)
/dev/hda5 on /media/disk-2 type ext2 (rw,noexec,nosuid,nodev)


that is my sudo mount output 

i cant get an output for sudo fdisk -l


and by gnome PE i mean gnome partition editor


i can give the readouts of partition editor if they will help in the stead of fdisk info:

/dev/hda1  fat32  /media/disk-3   9.45gb 1.63gb used  lba
/dev/hda2  extended                   9.45gb
   /dev/hda5  ext2  /media/disk-2  9.45gb 1.93gb used  boot

/dev/hdb1  linux-swap                  572.06 mib
/dev/hdb2  ext2    /media/disk-1    20.0gib 320.88mib used  
/dev/hdb3  ext2    /media/disk       4.28gb  69.20mib used   





hope that helps and ty for all the help

---

### Post by Kindredgarou on 2007-09-26
as an added point i resetup my system to how it was when i installed an it works guess i hit a wrong step in the install

---

### Post by Kindredgarou on 2007-09-26
just as a note and ty once agai, I have reinstalled fiesty without the windows drive in and got it installed now just sorting a grub error 18 but have found that in another post

---

