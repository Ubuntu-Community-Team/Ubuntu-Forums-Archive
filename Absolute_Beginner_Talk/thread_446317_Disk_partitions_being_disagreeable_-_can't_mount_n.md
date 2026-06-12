---
title: "Disk partitions being disagreeable - can't mount new ext2 partition"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by esprit on 2007-05-16
So, I used to use Windows, but now I'm dual-booting Windows and Ubuntu.  Unfortunately, this means that all of the CDs I rip now are on my Linux ext3 partition, but all of the CDs I ripped before I used Linux primarily are on my NTFS partitions (yes, partitions.  That's due to another, now-resolved problem that had to do with Windows being screwy, but now it's fixed.)  I've got 3 NTFS partitions, an ext3 partition and a swap partition.  However, I recently read about a driver that lets Windows deal with ext2!  This miraculous "ext2fsd" would allow me to copy all the music on my NTFS partitions to a mutually agreeable ext2 one.  (Yes, I know I could have just copied them to my ext3 partition because ext3 is backwards compatible to ext2, but I know there's something funny about ext3 to ext2 and I didn't want to test this new driver on my Linux boot partition.)

So I move everything important off of one of my NTFS partitions (Ubuntu calls it /dev/hda3) and format it as ext2 with Ubuntu's Disks app.  Seems to work fine, though I don't actually move things to and from the partition itself yet.  I boot up Windows and move my music to the ext2 partition; seems to work fine.  Finally, I boot Linux again and see what's what.  And what's what is that Disks reports the partition as "disabled."  I hit the enable button, and... nothing happens.    (The "access file" portion says "none," by the way; I tried changing it to something like /hd2/, but it still didn't work.)  Uh-oh.  I look up the stickied READ THIS FIRST, which tells me I should try mount.

```
esprit@esprit-ubuntu:/$ mount
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/hda2 on /tmp/disks-conf-hda2 type ntfs (rw)
/dev/hda4 on /tmp/disks-conf-hda4 type ntfs (rw)
```

Okay.  So it's not mounted; I don't see /dev/hda3 in there.  I then try fdisk.

Note that at the beginning of this all, I had 3 NTFS partitions, 1 ext3 partition, one swap partition, and a bit of free space.  Now, I should have 2 NTFS partitions, 1 ext3 partition, 1 ext2 partition (I don't know if they would show up differently or the same, so I'll just mention both), one swap partition, and a bit of free space.

```
esprit@esprit-ubuntu:/$ sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           11641       14593    23719972+   5  Extended
/dev/hda2   *        1289        2563    10241437+   7  HPFS/NTFS
/dev/hda3            2564        5113    20482875    7  HPFS/NTFS
/dev/hda4            5114       11640    52428127+   7  HPFS/NTFS
/dev/hda5   *       11641       14469    22723911   83  Linux
/dev/hda6           14470       14593      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Erm... so Disks thinks /dev/hda3 is ext2, but fdisk thinks it's HPFS/NTFS.  This... could be a problem.

Just for the heck of it, here's cat /etc/fstab.  /dev/hda3 doesn't show up there, but hey, just in case it could be useful...

```
esprit@esprit-ubuntu:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

So, anyone know how I can get /dev/hda3 to mount successfully?

(One other thing.  How can I mess around with the default GNOME Ubuntu launcher?  This is a really stupid question, but I can't figure out how.  Mainly I want to launch the basic Text Editor with sudo so I can actually edit Important Files if I need to, but I don't know what Text Editor's file name is, and I can't figure it out unless I can mess with the launcher.)

---

### Post by poohbear1616 on 2007-05-16
Unless I am wrong, Ubuntu does not support ext 2.
Someone correct me if I am wrong.

---

### Post by yabbadabbadont on 2007-05-16
OK, your second question first.  "gksudo gedit"  (without the quotes)

Now for your first question.  In a terminal window run "sudo fdisk /dev/hda".  At the prompt, enter "t" for type.  When prompted, select partition 3.  When prompted for new type, enter 83.  (linux)  At the prompt, enter "w" for write and exit.  You will now have to reboot before the change will take effect.  Once you have rebooted, try recreating the ext2 filesystem again as you did before.  Hopefully, it will do everything correctly this time now that the partition type for hda3 is 83 (linux).  If not, post back here and we'll help you manually create it and add it to /etc/fstab.

---

### Post by yabbadabbadont on 2007-05-16
> **poohbear1616 said:**
> Unless I am wrong, Ubuntu does not support ext 2.
Someone correct me if I am wrong.

You're wrong.  :D  (there, you're corrected)

---

### Post by esprit on 2007-05-16
On one hand, yabba, your command did what it should have done - fstab now includes /dev/hda3 as type 83 (Linux).  However, mounting still fails, as ```
mount: can't find /dev/hda3 in /etc/fstab or /etc/mtab
```

So I looked up what /etc/mtab looked like:
```
esprit@esprit-ubuntu:~$ cat /etc/mtab
/dev/hda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-28-386/volatile tmpfs rw 0 0
/dev/hda2 /tmp/disks-conf-hda2 ntfs rw 0 0
/dev/hda4 /tmp/disks-conf-hda4 ntfs rw 0 0
```

Yep, no hda3.  So could I just add this line:
```
/dev/hda3 /hda3 ext2 rw 0 0
```
to mtab and it would be alright?  Or is it more complicated than that?

---

### Post by yabbadabbadont on 2007-05-17
Don't mess with /etc/mtab.  It is updated automagically and baaad things can happen if you mess with it.  ;)

Add a new entry to /etc/fstab for /dev/hda3 instead.  You will probably want something like this:
```
/dev/hda3       /media/music    ext2        defaults                       1       2
```
You will need to create whichever directory you decide to use for the mount point.  (/media/music in my example)  Also, since it is an ext2 filesystem, it should probably be dumped in case of a kernel panic and you definitely want it to be checked during boot.  (the "1  2" at the end of the example)  If you don't want it to be automatically mounted at boot, change "defaults" to "user,noauto".  (without the quotes of course)

---

