---
title: "[SOLVED] problem with pure boot partitioning"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by iris-n on 2007-12-05
After 1 month of smooth Ubuntu use, I decided to wipe out XP, to save disk space and gain elegance. I formated it through gparted (now it doesn't seem very wise), and made a new ext3 partition in that space. Then my problems were:

1-Denied permission to read/write. I used chown and all gone well, but

2-then the partition stoped mounting at bootup. It works fine, but I have to mount it every time, and it doesn't seem quite healthy.

3-Not a problem, just a matter of elegance. Can I remove the Windows XP option from the boot screen?

Currently it mounts at /media/disk, and my machine is a Dell laptop.

I'd be glad if anyone could give me advice.

---

### Post by iris-n on 2007-12-06
I tried fstab, and found
/media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46
even though I had formated it as ext3.
Kinda weird. Browsing through some sites I found out that what defines if the system mounts or not the disk is the auto/noauto, that seems absent from here
Does anyone know what this umask is? man couldn't tell me.
Please?

---

### Post by uidb4056 on 2007-12-06
Can you run in a terminal the command blkid and post what retuns

---

### Post by iris-n on 2007-12-06
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-031D" TYPE="vfat" 
/dev/sda3: UUID="22f9d397-896b-435b-bcef-4686cebffb83" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="65d9dce4-726a-4ffa-b686-7120c28deb5a" 
/dev/sda2: UUID="38858cb5-b2d9-48ce-ad9f-8ff99e6b1d34" SEC_TYPE="ext2" TYPE="ext3" 

the rogue partition is the sda2

---

### Post by uidb4056 on 2007-12-06
I thin there is something mismatch in your /etc/fstab file, before I can suggest how to edit it, can you please port the result of cat /etc/fstab

---

### Post by iris-n on 2007-12-06
there is a mismatch, but I'm not secure on where to correct it.
anyway, the complete fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=22f9d397-896b-435b-bcef-4686cebffb83 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-031D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=0890166D9016620C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=65d9dce4-726a-4ffa-b686-7120c28deb5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by uidb4056 on 2007-12-06
Yes, /etc/fstab is not matching with your current value for /dev/sda2.

First I suggest to make a copy of your current /etc/fstab for security

sudo cp /etc/fstab /etc/fstab.org

now edit with

sudo gedit /etc/fstab

And change the line under # /dev/sda2

with

UUID=38858cb5-b2d9-48ce-ad9f-8ff99e6b1d34 /media/sda2 ext3 defaults,errors=remount-ro 0 1

Save it and reboot.

---

### Post by iris-n on 2007-12-06
Thanks for the help!

But I like to know what I'm doing. Why delete nls=utf8,umask=007,gid=46 ? what are these options?

---

### Post by shadow-of-sin on 2007-12-06
To remove the Windows XP option from GRUB:
-Open up the /boot/grub/menu.lst file:
```
sudo nano /boot/grub/menu.lst
```
-Scroll down to "title           Microsoft Windows XP Professional" and delete the following text:
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
-Save and exit

Now the Windows XP option wont appear on the menu (BTW you might want to make a backup of your menu.lst file before editing it just in case)

---

### Post by uidb4056 on 2007-12-06
The contents in fstab below line # /dev/sda2 is the old content of your old windows partition (note that blkid is showing for /dev/sda2 a different UUID than you have in fstab) what comes after the UUID is the mount point for /dev/sda2 and the rest are the same options you have for your root partition of Ubuntu

---

### Post by rsambuca on 2007-12-06
> **uidb4056 said:**
> Yes, /etc/fstab is not matching with your current value for /dev/sda2.

First I suggest to make a copy of your current /etc/fstab for security

sudo cp /etc/fstab /etc/fstab.org

now edit with

sudo gedit /etc/fstab

And change the line under # /dev/sda2

with

UUID=38858cb5-b2d9-48ce-ad9f-8ff99e6b1d34 /media/sda2 ext3 defaults,errors=remount-ro 0 1

Save it and reboot.

I really don't thing those are the best settings.  I recommend the last part look like this:

defaults 0 2

The errors=remount... command is only necessary for bootup of the root directory.

---

### Post by iris-n on 2007-12-06
Worked!
Backed all up, and reboot.

Now I have a cute clean boot screen.

And my partition is mounting alright, with rw access.

Very grateful to you all.

Now I would have two more questions:

1- It is possible (desirable) to mount the partition to a regular directory?

2- In chown'ing blindly, I think I messed up things a bit. Which would be the recommendable permissions/ownerships for the directorys?

3- There is no question nº 3.

---

### Post by shadow-of-sin on 2007-12-06
> **iris-n said:**
> Worked!
1- It is possible (desirable) to mount the partition to a regular directory?
.
Yeah just edit the /etc/fstab file and change the mount point to the directory name you want (note: you will have to make the directory first if it doesn't exist)

---

### Post by iris-n on 2007-12-06
Gee, smooth and quick, thanks again.

---

