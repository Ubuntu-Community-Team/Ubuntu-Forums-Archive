---
title: "can't eject cd!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by princeofchildren on 2008-01-15
hello, I am having difficulties with my dvd drive, it will not allow me to eject, I've tried playing with the code, but I have no idea what I'm doing as I am completely new to this. I would greatly appreciate any help. here is the fstab file, the cd would not mount before, and a user told me to remove the # in front of the code, and to remove the "uuid" stuff, so now cd mounts, but cannot eject: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1/media/EXTERNAL ntfs-3g defaults,force 0 0
              ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
         swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec 0       0

thanks,
-d

---

### Post by Tenken on 2008-01-15
If you use Gnome and can see the CD/DVD on the desktop, try right-clicking it and select "Eject", or from the command line

```
sudo umount /media/cdrom0
```

---

### Post by MrFSL on 2008-01-15
When you can't eject run this:
```
mount
```
And post the output.

---

### Post by RomeReactor on 2008-01-15
Hi. Sometimes when a CD is dirty/scratched, the system has problems reading it and Nautilus (the file browser in Gnome) may hang. On other occasions it may be that you tried to play media on the disc--either audio or video--and the player is unable to read the source. Try opening System Monitor (System->Administration->System Monitor), find Nautilus, right-click on it and select "Kill Process"; then try to eject the CD. To do it from the terminal:
```
eject /media/cdrom
```
Or your CD drive's correct designation in the **/media** directory.

---

### Post by mali2297 on 2008-01-15
> **princeofchildren said:**
> hello, I am having difficulties with my dvd drive, it will not allow me to eject, I've tried playing with the code, but I have no idea what I'm doing as I am completely new to this. I would greatly appreciate any help. here is the fstab file, the cd would not mount before, and a user told me to remove the # in front of the code, and to remove the "uuid" stuff, so now cd mounts, but cannot eject: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1/media/EXTERNAL ntfs-3g defaults,force 0 0
              ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
         swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec 0       0

thanks,
-d

I hope that you did a backup of the fstab file. If so, revert to the backup file. Otherwise, you might get trouble when booting the system.

Several lines above are missing the first entry, the *uuid stuff* should be replaced with stuff like /dev/sda1, /dev/sda2 et cetera. This guide might help (if you really want to mess with fstab):
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by princeofchildren on 2008-01-15
ok, with this configuration:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1/media/EXTERNAL ntfs-3g defaults,force 0 0
UUID=916a3b3e-fdbb-4b60-9c67-ecc795cef2a5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1976375f-4fc6-4a2f-bc67-bbed4dfa6de9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec 0       0

I can eject, but only through  the terminal, then when I insert another cd, it doesn't show up on the desktop. also dvd will not play. does anyone know where I could go to look at other people's fstab files, to get an Idea of what they're supposed to look like?

thanks,
-D

---

### Post by mali2297 on 2008-01-15
Well, I have this line
```

/dev/hdc  /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by princeofchildren on 2008-01-15
does it matter that it's a dvd-r drive? is there different code used for dvd drives?

---

### Post by Cypher on 2008-01-15
Linux doesn't differentiate between DVD/CD/Blu-Ray/HD-DVD or anything else..it's just a device..:)

Please send us the output of
```

mount

```

---

### Post by Het Irv on 2008-01-15
If nothing else works try the paperclip trick.  
Bend a paperclip so that about an inch (2cm) is straight.
There should be a small hole in or around your DVD drive's faceplate.
Stick the straight end of the paperclip straight into the hole
You should feel a small button on the other side, press it with the paperclip and the DVD Drive will pop out about an eighth of an inch (.25cm).
 This is only to be used as a last resort (or if you forgot to take the Disk out of a computer you just turned off and don't feel like turning it back on.

---

### Post by princeofchildren on 2008-01-15
ok, so I changed the fstab file to this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1/media/EXTERNAL ntfs-3g defaults,force 0 0
UUID=916a3b3e-fdbb-4b60-9c67-ecc795cef2a5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1976375f-4fc6-4a2f-bc67-bbed4dfa6de9 none            swap    sw              0       0
/dev/hdc  /media/cdrom0   udf,iso9660 user,noauto     0       0


I can now eject cd, but cannot play dvd. now it shows two discs, I assume this is because I changed "scd0" to "hdc"
and here are the mount results:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/EXTERNAL type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

thanks,
-D

---

