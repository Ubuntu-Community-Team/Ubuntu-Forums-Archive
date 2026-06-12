---
title: "Mounting Windows hdd in Ubuntu"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-05-08
I have recently set up a dual boot system with Ubuntu on the master hdd, and windows xp on the slave. both systems run fine, but i cannot mount/access the other system's hdd when running either system

As i cannot get my nic working on linux i would like to be able to transfer files between the two so i can email files to school/friends/etc without burning to disk each time

I have tried the *mount* command in the terminal, but do not know how to identify the drive to mount and get it to mount

does any body have any ideas? or have had the same problem theselves and have managed to sort it

---

### Post by KIAaze on 2007-05-08
Use ```
sudo fdisk -l
``` to identify the drive to mount.

---

### Post by taurus on 2007-05-08
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If you want to access Ubuntu from XP, install [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by simon303 on 2007-05-08
i know that the linux hdd is /dev/hda and the windows hdd is /dev/hdb

---

### Post by simon303 on 2007-05-08
> **taurus said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I have had a look through the instructions on this site, but when i open fstab in nano there is no mention at all of hdb or hdb1 and so i cannot edit it

---

### Post by taurus on 2007-05-08
Then can you post the output of these two commands?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by simon303 on 2007-05-08
in a moment i can, just have to save the outputs to floppy, reboot to windows (family pc has no floppy and linux has no internet) and then post the output

---

### Post by simon303 on 2007-05-08
```
simon@simon-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2388    19181578+  83  Linux
/dev/hda2            2389        2480      738990    5  Extended
/dev/hda5            2389        2480      738958+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2490    20000893+   7  HPFS/NTFS
simon@simon-desktop:~$ 

```

```
simon@simon-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0373af2b-ed97-40b6-b7e5-0614cbb7fb5b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=cd35f848-72c8-4216-ac08-fc66fc1049d5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by taurus on 2007-05-08
So you want to mount /dev/hdb1.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by simon303 on 2007-05-09
thanks, it is working now
one last question, do i need to unmount it before i shut down and mount it every time i boot and want to use it?

---

### Post by drowner on 2007-05-09
No you dont, 2 both questions (well, i hope not, i've never unmounted it :eek: 

Now that it is in your fstab it  will mount everytime on startup

---

### Post by simon303 on 2007-05-09
looks like i have found a problem with the mounting
i can access everything on it, but the moment i try to write to it i get an error saying it is read only
can i do anything to mount it so i can write to it, or do i just have to accept i never can?

---

### Post by drowner on 2007-05-09
> **simon303 said:**
> looks like i have found a problem with the mounting
i can access everything on it, but the moment i try to write to it i get an error saying it is read only
can i do anything to mount it so i can write to it, or do i just have to accept i never can?

You are using feisty?

Writing to NTFS from ubuntu requires ntfs-3g

See here: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Because the NTFS-write is still not native, your NTFS was mounted as read-only, so it is not a bug, or a problem as such.

Now, I know very little about ntfs-3g (i dont use it) but you will need to modify your fstab to make reference to ntfs-3g, and change the entry to make it read and write, rather than read-only.

I BELIEVE ntfs-3g can do it automatically, but I'm not sure, and I will ask someone with more experience with it to help you.

---

### Post by simon303 on 2007-05-11
im currently using edgy, but considering upgrading to feisty if i can do it without having to start from scratch again.
does ntfs-3g come as standard with feisty? or do you have to get it as an extra like you do in edgy, if you do i have a problem as my ethernet card does not work in edgy and so i have no internet

---

