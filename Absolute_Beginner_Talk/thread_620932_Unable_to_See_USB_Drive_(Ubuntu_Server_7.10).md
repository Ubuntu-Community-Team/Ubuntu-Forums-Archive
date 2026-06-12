---
title: "Unable to See USB Drive (Ubuntu Server 7.10)"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Juice777 on 2007-11-23
When I plug in a USB Flash Drive into my Server I am unable to mount the device.

I have run "sudo fdisk -L (lowercase)" and it shows the device present under /dev/sda, but when I attempt to mount the drive, I get message "can't find /dev/sda in /etc/fstab or /etc/mtab

I've also tried using "sudo mount -t vfat /dev/sda /mnt" as the drive is FAT16, just goes to another command prompt.. and I don't know how to connect to it..

Anyone else come across this problem?

---

### Post by anaconda on 2007-11-23
sudo mount -t vfat /dev/sda /mnt
have you tried:
sudo mount -t vfat /dev/sda1 /mnt  

since usually there is a number after the sda.. the first partition can be  1 or 5 (if the only partition is logical)
so try both ways.. 1 and 5

---

### Post by Zack McCool on 2007-11-23
> **Juice777 said:**
> When I plug in a USB Flash Drive into my Server I am unable to mount the device.

I have run "sudo fdisk -L (lowercase)" and it shows the device present under /dev/sda, but when I attempt to mount the drive, I get message "can't find /dev/sda in /etc/fstab or /etc/mtab

I've also tried using "sudo mount -t vfat /dev/sda /mnt" as the drive is FAT16, just goes to another command prompt.. and I don't know how to connect to it..

Anyone else come across this problem?

/dev/sda is the drive, you want to mount the partition.

sudo mount -t vfat /dev/sda1 /mnt/removeable

I wouldn't mount directly to /mnt, as this is a place for mounted driveS.  You may want more than one there, so create sub-directories (like the above mentioned "removeable")

---

### Post by ukripper on 2007-11-23
can you also post output of following command after trying above provided solutions:
```
mount
```

---

### Post by Juice777 on 2007-11-23
Still no joy. Heres the output of mount:

/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/fd0 on /media/floppy0 type vfat (rw,nosuid,nodev,user=jon)
/dev/sda1 on /mnt type vfat (rw)

---

### Post by ukripper on 2007-11-23
try this:


 run following commands:
```
# sudo mkdir -p /media/usbdrive
# sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sda1 /media/usbdrive
```

---

### Post by Juice777 on 2007-11-23
Still no joy. I get error:

mount: special device /dev/sda1 does not exist

Any ideas?

---

### Post by ukripper on 2007-11-23
Can you post output of following :```
lsusb
```

---

### Post by Juice777 on 2007-11-23
Hope this helps..

Bus 003 Device 006: ID 0951:1601 Kingston Technology 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

