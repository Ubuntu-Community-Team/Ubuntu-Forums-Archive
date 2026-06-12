---
title: "Sda1 always mounted..."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by UbunUsr on 2008-02-03
Hello.

I have Ubuntu 7.10,and i have WinXp,the Xp is mounted on sda1 partition and i get this everytime i start Ubuntu.I have just done repair (i deleted,created and formated partitions),and from that time i alwayes get sda1 (WinXp) partition mounted on Ubuntu desktop.I try with right-click>Unmount option but it sais,
Only root can unmount selected volume.

When i setted up dualboot i installed XP first then i installed ubuntu with option to resize and use free space,but i messed something up,and i reinstalled ubuntu and from that point,i get XP partition mounted everytime...Also before reinstallation i could select and browse XP partition from Nautilus...

How do i unmount it so it cannot appear on  desktop,but to appear in nautlus.?

---

### Post by bluewraith on 2008-02-03
Right now its mounting the partition in /media/ which will always show on the desktop. I don't know how to do it myself, but if you dont want it on the desktop but do want it in nautilus then you need to have it mount to /mnt/ instead.
Perhaps someone else can chip in?

---

### Post by jan quark on 2008-02-03
pls

post results of the terminal commands

```
mount
```

```
sudo fdisk -l
```

---

### Post by UbunUsr on 2008-02-03
Here is mount result:


/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda4 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)


Here is fdisk info:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb1adb1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22284   178996198+   7  HPFS/NTFS
/dev/sda2           22285       24108    14651280   83  Linux
/dev/sda3           24109       24351     1951897+  82  Linux swap / Solaris
/dev/sda4           24352       30401    48596625   83  Linux

---

### Post by jan quark on 2008-02-03
run to unmount from media

```
sudo umount /media/sda1
```

create a new mount point
```

sudo mkdir /mnt/windows
```


run to mount in mnt

```
sudo mount /dev/sda1 /mnt/windows -t ntfs -o nls=utf8,umask=000
```

---

### Post by UbunUsr on 2008-02-03
Ok,thanks for this ...but how can i mount/unmount using right click menu.
It still tells me that i dont have permissions.

---

### Post by UbunUsr on 2008-02-03
Heh...weird problem...when i execute those commands,everything is ok..but when i restart computer,and when i enter windows,and when i enter ubuntu again there is sda1 again on desktop...

---

### Post by jan quark on 2008-02-03
here we go that will be fun not only for you

we must create a automount script

run
```
gedit allmount.sh
```

that will create a new empty file with this name
type this into the new empty file

```
#!/bin/sh
```

```
sudo mount /dev/sda1 /mnt/windows -t ntfs -o nls=utf8,umask=000
```

ok now we have to change the file permission to execute this file, nothing in linux can be executed without the right permission set
```

sudo chmod 755 allmount.sh
```

to check if the setting of the permission worked run

```
ls -l
```

and check if your new created allmount.sh has three x

if everything is correct

save the file and double click on it

when prompted you want to run in in terminal
type in your password
that's it

so the next time you reboot and log in you only have to run this script and your partition should be mounted.

---

### Post by UbunUsr on 2008-02-03
No,that script doesn't help...

---

### Post by hyperair on 2008-02-03
Please post the contents of /etc/fstab. 

Also I don't understand the situation here. It seems that you want to be able to browse the partition, but don't want it mounted?

Either way, to clarify the situation please answer a few questions:
1. Do you want it mounted upon start up?
2. Do you want it to appear on your Desktop?
3. Do you want it to appear in Computer?

---

### Post by Kingsley on 2008-02-03
You could probably get what you want by commenting out the /dev/sda1 lines in /etc/fstab and /etc/mtab

---

### Post by hyperair on 2008-02-03
> **Kingsley said:**
> You could probably get what you want by commenting out the /dev/sda1 lines in /etc/fstab and /etc/mtab

/etc/mtab is not a file to be touched manually! It's a 'current mounts' file maintained by mount and umount.

---

### Post by UbunUsr on 2008-02-03
Hi hyperair..

I want to be mounted on startup,but i dont want it on desktop,i want it in Computer...

And,i cannot browse partition if it isn't mounted,right?

sorry i expressed myself badly..


fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8c218103-0da6-472c-9502-a721eb76ea79 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=120d4ca4-bae4-4056-94b0-469f75ace155 /home           ext3    defaults        0       2
# /dev/sda1
UUID=CE1CD9291CD90D79 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=e53bf02c-833f-441b-9d73-0b926324547e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

if i change for sda1 to be in mnt/windows,folder i dont see it anymore on desktop,Computer etc...practically it's unmounted..

---

### Post by hyperair on 2008-02-03
You don't want it on your desktop eh? What about other mounted media? Say thumbdrives and the like? From what I know, you can either have ALL mounted media shown on your desktop, or NONE shown on your desktop. That can be done by checking/unchecking the box in /apps/nautilus/desktop/volumes_visible in gconf-editor. 

If you want only /dev/sda1 to be affected in that manner, try this rather hackish method: 
change the line in /etc/fstab:
```

UUID=CE1CD9291CD90D79 /media/sda1 ntfs defaults,umask=007,gid=46 0 1

```
to
```

UUID=CE1CD9291CD90D79 /media/sda1 ntfs defaults,user,noauto 0 1

```
Then restart and see the effect.

---

### Post by UbunUsr on 2008-02-03
Ok,now sda1 is not visible on desktop and this method works..(cd's,usb flash,etc mounts on desktop as it should)
Also there is sda1 in Computer,but when i click on it it sais that 
i dont have permissions...

what about that..?

---

### Post by hyperair on 2008-02-03
Huh strange. It should work, according to what I've read in the manual for mount. =\ Perhaps I just need some sleep. When I wake up I'll read the manual again and try help.

How about just commenting out the line mentioned earlier?

---

### Post by UbunUsr on 2008-02-04
I used this blog:

[http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/](http://www.joshgerdes.com/blog/2007/10/30/move-mounted-partition-icons-from-the-desktop-in-ubuntu-710/)

and I have permissions now,but i dont see win partition in Computer...

---

### Post by UbunUsr on 2008-02-04
and,btw,commenting etc/fstab,caused Ubuntu to crash...

---

### Post by vanadium on 2008-02-04
This thread has become a great mess with some good but lots of ill advises.

jan quark advised correctly on how to change the mount point manually. However, in order to mount your disk automatically in the new directory (/mnt/windows instead of /media/sda1) you need specify these things in fstab.

In /etc/fstab, change

```

UUID=CE1CD9291CD90D79 /media/sda1 ntfs defaults,umask=007,gid=46 0 1

```

to

```

UUID=CE1CD9291CD90D79 /mnt/windows ntfs defaults,umask=007,gid=46 0 1

```

You see, the only thing you change is the mount point, from /media/sda1 to /mnt/windows. The other options remain the same. Thus, the drive will behave as before, only will you access it browsing to /mnt/windows rather than going to /media/sda1.

---

### Post by hyperair on 2008-02-04
Sorry to rain in on your parade, Vanadium, but the method you've shown is what was shown earlier in the topic, and is the current issue. UbunUsr wants to have the file not shown on the desktop, but at the same time, shown in the Computer. There is only one way to achieve this, and that is to prevent automatic mounting, but enable regular user mounting. That is the method I've tried to achieve by adding "user" and "noauto" to the fstab line. However, there still is the whole permissions denied issue. I'm at a loss of how to continue. For me, I'd just live with the hard disk showing up on the desktop. In fact, I prefer it there.

---

