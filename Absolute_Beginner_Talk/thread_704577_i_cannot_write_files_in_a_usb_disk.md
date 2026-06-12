---
title: "i cannot write files in a usb disk"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by hlekat on 2008-02-22
i have a problem with my usb disk. i cannot write files to it. i copy a file but the paste option does not activate in the usb folder.

i also try to use cp with sudo but i am not sure if a type the command correct.

:~/Desktop$ sudo cp filename '/media/USB DISK'

---

### Post by taurus on 2008-02-22
What filesystem is "/media/USB DISK"?

```
sudo fdisk -l
mount
```

---

### Post by bodhi.zazen on 2008-02-22
Sounds like a permissions problem. Run that command with sudo.

If that works, it is permissions. We need to know the file system to fix it.

---

### Post by hlekat on 2008-02-22
Disk /dev/sdc: 8119 MB, 8119648256 bytes
200 heads, 32 sectors/track, 2477 cylinders
Units = cylinders of 6400 * 512 = 3276800 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2478     7929328    c  W95 FAT32 (LBA)


what should i do with the mount command ?

---

### Post by hlekat on 2008-02-22
yes it is a permision problem . in properties i change the file access with has no option by default i close the window but it does not change, but i have folder access.

is this command correct > : 

sudo cp UPHClean-Setup.msi '/home/jp/Desktop/UPHClean-Setup.msi'  '/media/USB DISK' 
cp: cannot stat `UPHClean-Setup.msi': No such file or directory
cp: cannot create regular file `/media/USB DISK/UPHClean-Setup.msi': Read-only file system

---

### Post by bodhi.zazen on 2008-02-22
You have to set permissions on a FAT drive at the time of mount. I am surprised it did not happen automatically.

At any rate :

```
sudo umount "/media/USB DISK"
sudo mount -t vfat /dev/sdc1 "/media/USB DISK" -o uid=1000,gid=100,umask=007
```

---

### Post by hlekat on 2008-02-22
jp@jp-desktop:~$ sudo mount -t vfat /dev/sdc1 "/media/USB DISK" -o uid=1000,gid=100,umask=007
mount: mount point /media/USB DISK does not exist

---

### Post by bodhi.zazen on 2008-02-22
sudo mkdir "/media/USB DISK", then re-mount

---

### Post by hlekat on 2008-02-22
sudo umount "/media/USB DISK"
sudo mkdir "/media/USB DISK"
sudo mount -t vfat /dev/sdc1 "/media/USB DISK" -o uid=1000,gid=100,umask=007

still i have permission problems (canot copy).

also now i canot unmount it :

The volume 'USB DISK' was probably mounted manually on the command line.
details : device to unmount is not in /media/.hal-mtab so it is not mounted by HAL

---

### Post by bodhi.zazen on 2008-02-22
sudo umount "/media/USB DISK" 

should unmount the device.

Can you post the output of :

```
ls -l /media
```

That is a smalll "L" and not the number 1

---

### Post by hlekat on 2008-02-22
first i unmount it and then i typed the ls -l /media

drwxr-xr-x 2 root root 4096 2008-02-22 22:19 USB DISK

---

### Post by hlekat on 2008-02-22
jp@jp-desktop:/media$ ls
cdrom  cdrom0  floppy  floppy0  USB DISK  USB DISK_

usb disk_ did not exist. maybe something go wrong.

---

### Post by bodhi.zazen on 2008-02-22
Something seems amiss, trying to find out what.

First Linux is case sensitive so usb_ is not the same as USB_

Can you post the output of these two commands:

```
ls -l /media

mount
```

---

### Post by hlekat on 2008-02-24
jp@jp-desktop:~$ ls -l /media
total 16
lrwxrwxrwx 1 root root    6 2002-01-01 02:14 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2002-01-01 02:14 cdrom0
lrwxrwxrwx 1 root root    7 2002-01-01 02:14 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2002-01-01 02:14 floppy0
drwxr-xr-x 2 root root 4096 2008-02-22 22:19 USB DISK
drwx------ 5 jp   root 4096 1970-01-01 02:00 USB DISK_
jp@jp-desktop:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdd1 on /media/USB DISK_ type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

---

### Post by bodhi.zazen on 2008-02-24
Looks like your device is not /dev/sdd1 and is mounted at /media/USB DISK_

You are the owner and have rw access.

> /dev/sdd1 on /media/USB DISK_ type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma sk=077,usefree) 

drwx------ 5 jp root 4096 1970-01-01 02:00 USB DISK_

---

### Post by hlekat on 2008-02-25
i made format to the stick from windows.

now it's working fine. also the date is now fixed. in previous post it was appearing 1970-1-1 but now everything works fine. 

thanks !

---

