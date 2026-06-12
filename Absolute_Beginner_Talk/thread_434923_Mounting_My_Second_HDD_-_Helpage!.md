---
title: "Mounting My Second HDD - Helpage!"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Tarquin on 2007-05-06
Hi there. Im new to Linux, and recently decided to ditch my Vista for Ubuntu 7.04!

I got help from a friend to access my 2nd HDD, as it was showing on the desktop (mounted?) but I could not write anything to the disk!
He also informaed me it would be best to format my drive using Linux as obviously it was still set as NTFS for windows. I did this and changed it to ext3.

But now, even though I can get to my 2nd HDD through the file system, and in terminal it says hdb1 is already mounted, it will not appear on the desktop or Places>Computer. Now of course I dont want to put any of my stuff back onto it incase I lose it! Also in ect/fstab (When I can get it to open, sometimes it opens a blank edit window) the line I had to add at the bottom to make it work before still has ntfs-3g in, I have changed this but last time I looked it went back to ntfs-3g!

Anyways, many thanks in advance if someone can help me get running again, so annoying and my first HDD is a bit full now cos to format the 2nd I moved all my stuff onto the 1st!

Tarq

---

### Post by taurus on 2007-05-06
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Sc0rp10n on 2007-05-06
Subscribing to thread.  I'm a complete newbie to Ubuntu and installed yesterday.  Great experience and even got my widescreen resolution going (1680x1050).  Very polished.

I have 2 HD's in my system and can't get the 2nd HD working correctly.  It was NTFS, but I used Gparted to blow the NTFS partition away and create a new ext3 partition and formatted it.  It put an icon on the desktop for the drive, but when I try to save data to it, it says that it is read only.  Any way to get this drive to not be read only?  

So far, this is my only problem.  I'm really impressed with how polished the OS is but I have alot to learn.

---

### Post by taurus on 2007-05-06
> **Sc0rp10n said:**
> Subscribing to thread.  I'm a complete newbie to Ubuntu and installed yesterday.  Great experience and even got my widescreen resolution going (1680x1050).  Very polished.

I have 2 HD's in my system and can't get the 2nd HD working correctly.  It was NTFS, but I used Gparted to blow the NTFS partition away and create a new ext3 partition and formatted it.  It put an icon on the desktop for the drive, but when I try to save data to it, it says that it is read only.  Any way to get this drive to not be read only?  

So far, this is my only problem.  I'm really impressed with how polished the OS is but I have alot to learn.

You just need to change the ownership of that mount point from root to your username.  What is the mount point of that partition in /media and what is your username?

```
id
df -h
```

---

### Post by Sc0rp10n on 2007-05-06
My mount point is "/media/disk" and my username is "michael".  How should I go about changing it?

---

### Post by Sc0rp10n on 2007-05-06
Also, how can I remove the icon from the desktop?

---

### Post by hyper_ch on 2007-05-06
open a terminal (I like the terminal... it's just so efficient) and enter:

```

sudo chown -R michael:michael /media/disk

```

That will change the owner ship to michael and als the groupownership to michael (if you have a default install then your username and groupname are identical). The -R will also make sure that all files located inside /media/disk will be changed in the ownership :)

That should do the trick :)

---

### Post by Sc0rp10n on 2007-05-06
I think that worked.  Is there any way to do that with the graphical tools, either "Computer" in Places or with Gparted?

I also figured out that the desktop icon shows up when the volume is mounted and disappears when it is unmounted, so no big deal there.

---

### Post by taurus on 2007-05-06
If you don't want to have an icon on your desktop for that partition, mount it to /mnt/disk.

Therefore, modify your /etc/fstab and then create a new mount point for it.

---

### Post by Tarquin on 2007-05-06
**@ Taurus** - Results for the 2 commands:
sudo fdisk -l:
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9683    77778666   83  Linux
/dev/hda2            9684        9964     2257132+   5  Extended
/dev/hda5            9684        9964     2257101   82  Linux swap / Solaris

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7476    60050938+  83  Linux

cat /ect/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3d3115bb-c3ca-4915-b770-8b364edf6648 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=54733691-24f2-428c-bf3e-0b2eba6df422 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1 /storage ext3 defaults 0 0


**@ Sc0rp10n** - Thanks for hijacking my thread! Get your own! [-X

---

### Post by Tarquin on 2007-05-06
Bump!

---

### Post by taurus on 2007-05-06
> **Tarquin said:**
> **@ Taurus** - Results for the 2 commands:
sudo fdisk -l:
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9683    77778666   83  Linux
/dev/hda2            9684        9964     2257132+   5  Extended
/dev/hda5            9684        9964     2257101   82  Linux swap / Solaris

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7476    60050938+  83  Linux

cat /ect/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3d3115bb-c3ca-4915-b770-8b364edf6648 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=54733691-24f2-428c-bf3e-0b2eba6df422 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1 /storage ext3 defaults 0 0


Because you mount /dev/hdb1 to /storage, there won't be an icon on your desktop.  Therefore, you need to mount it to /media/storage.  So, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and change the last line to look like this.

```
/dev/hdb1   /media/storage   ext3   defaults   0   0
```
Save it and then create a new mount point for it.

```
sudo mkdir /media/storage
```
Then, reboot.

Now, if you want to be able to write to /media/storage, you need to change the ownership of /media/storage from root to your login name.  _Assuming_ your login name is **tarquin**, do

```
sudo chown -R **tarquin**:**tarquin** /media/storage
ls -la /media/
```

---

