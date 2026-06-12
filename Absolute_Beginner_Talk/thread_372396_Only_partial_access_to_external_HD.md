---
title: "Only partial access to external HD"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-02-28
Hello everyone,
For some reason I can access *(via terminal)* only 2 of the 3 partions of my external HD.
> /dev/sda2             35823504   2445072  33378432   7% _/media/usbdisk_
**/dev/sda3             26967968   4253904  22714064  16% /media/LOCAL DISK**
/dev/sda1             15343104   7897480   7445624  52% _/media/usbdisk-1_

Also:
> /dev/hda2 on / type ext3 (rw,noatime,errors=remount-ro,commit=600)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-686/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type fuse (rw,nosuid,nodev,noatime,allow_other)
/dev/hda3 on /media/hda3 type vfat (rw,iocharset=utf8,umask=000)
/dev/sda2 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)
**/dev/sda3 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)**
/dev/sda1 on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)

I can get into _/media/usbdisk_ and _/media/usbdisk-1_ but not **/media/LOCAL DISK**.
```
root@luser:~# cd /media/LOCAL DISK
bash: cd: /media/LOCAL: No such file or directory

```
Permissions are OK!

What could be wrong here? Thank you for reading.

---

### Post by Kateikyoushi on 2007-02-28
Do you have such directory ?

ls /media

---

### Post by xyz on 2007-02-28
> **Kateikyoushi said:**
> Do you have such directory ?

ls /media

Thanks for your reply.
```
root@luser:~# ls /media
cdrom  cdrom0  hda1  hda3  LOCAL DISK  usb  usbdisk  usbdisk-1

```

---

### Post by xyz on 2007-02-28
Wild guess here...but the only difference I see between my 3-external-HD partitions
>  LOCAL DISK  usbdisk  usbdisk-1

is that there's a space between LOCAL and DISK! I'm guessing this is not good! Am I getting any warmer?

---

### Post by Kateikyoushi on 2007-02-28
Indeed that is why I asked, I think in fstab it should be LOCAL\ DISK.
But the safest would be to rename to without a space.

---

### Post by anaconda on 2007-02-28
yep.. Kateikyoushi is right..

And if you are in terminal you can use the Tabulator to finish the names for you.. then it will become automatically right.

eg. cd /media/LOC -tab-
becames
cd /media/LOCAL\ DISK
or you could just type manually:
cd /media/LOCAL\ DISK
but space must be preceded with "\"  or you could use "":s if you prefer.

And you dont have to do anything to your fstab, because external USB-disks dont need to be in fstab..

Another way is to use nautilus (File browser)..

---

### Post by xyz on 2007-02-28
I think I gor it:
```
mount
```
> /dev/sda3 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)

That's what I need to change....the partion name 'LOCAL DISK' and did this:
[RenameUSBDrive]("RenameUSBDrive")
```
th@luser:~$ sudo mlabel -i /dev/sda3 -s ::
 Volume label is LOCAL DISK
th@luser:~$ sudo mlabel -i /dev/sda3 ::localdisk
th@luser:~$ sudo mlabel -i /dev/sda3 ::
 Volume label is LOCALDISK
Enter the new volume label : usbdisk-0

```
So now running:
```
ls /media
```
> cdrom  cdrom0  hda1  hda3  usbdisk  USBDISK-0  usbdisk-1


then:
```
th@luser:~$ cd /media/USBDISK-0
th@luser:/media/USBDISK-0$


```
...and I'm in there!
Thank you

---

### Post by xyz on 2007-02-28
Thanks all of you...now we have a couple of ways of doing it!

---

