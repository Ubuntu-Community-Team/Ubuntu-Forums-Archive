---
title: "Hi all im new and have problems"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by thehybridpyro on 2006-02-21
Hey guys i love UBUNTU

so I got my DUAL boot working
its fine

except I can access the files on my windows partition:
"i dont have acces"

since im not running as root I cant change the drive permissions
I didnt set a root password in setup and I dont know what it is

I use MY password that I log on with as the root password when running root apps but
I cant change drive permissions

and I cant move files and folders in my Filesystem folder wither
HELP GUYS!!

---

### Post by thehybridpyro on 2006-02-21
bump

---

### Post by Mustard on 2006-02-21
To speed things up, it might be helpful if you could post the output of these commands..

```
cat /etc/fstab
#this will show which partitions are being mounted on startup and how they are being mounted
```

```
sudo fdisk -l
#this will list all available partitions whether they are mounted or not
```

To make it all look neat, you can enclose the output in these forum codes... [noparse]```
..your code in  here...
```[/noparse]

---

### Post by thehybridpyro on 2006-02-21
where do  Ifind the command line?

---

### Post by senning on 2006-02-21
Applications->Accessories->Terminal

You might also find the second half of [this]("http://www.redhat.com/archives/fedora-selinux-list/2005-February/msg00144.html") helpful if you feel courageous.

---

### Post by gw90se on 2006-02-21
Have you tried this? [https://wiki.ubuntu.com/MountingWindowsPartitions]("https://wiki.ubuntu.com/MountingWindowsPartitions")

You can mount a Windows partition to read, but if you are using XP, you can't write to it.

---

### Post by thehybridpyro on 2006-02-21
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
eric@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2189    17583111    7  HPFS/NTFS
/dev/hda2            2190        3585    11213370   83  Linux
/dev/hda3            3586        3649      514080    5  Extended
/dev/hda5            3586        3649      514048+  82  Linux swap / Solaris
eric@ubuntu:~$

```

---

### Post by thehybridpyro on 2006-02-21
i know the windows partition is active because its says it is in the
System>Administration>Disks it says the NTFS partition is accessable
the error when I click on hda1 is
*"You do not have the permissions necessary to view the contents of "hda1"."*

---

### Post by thehybridpyro on 2006-02-21
bump

---

### Post by AudioBookDiety on 2006-02-21
I'm thinking it is a permissions issue. 
 You try to acces your files and it won't let you, says maybe "you do not have permisson to access this file"??

 simple fix

 open a terminal/console

 and type 
 sudo chown -R yourusername /thedirectory

 so for example 
 sudo chown -R ABDiety /media/hda1
   
 chown changes ownership of a directory
 the -R tells chown to change ownership of everything in that directory or more technically change ownership recursivley.
  
    [Shecky's Debian Asylum]("http://drshecky.org")

---

### Post by aysiu on 2006-02-21
Do this exactly (if you're running Gnome): ```
sudo umount /dev/hda1
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

Do this exactly (if you're running KDE): ```
sudo umount /dev/hda1
sudo cp /etc/fstab /etc/fstab_backup
sudo kwrite /etc/fstab
``` **Replace your entire /etc/fstab file with the following**: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
``` Then save and close Gedit or KWrite. Finally ```
sudo mount -a
```

---

### Post by jimrz on 2006-02-21
Look [[COLOR="DarkRed"]**here**[/COLOR]]("http://www.ubuntuguide.org/#automountntfs") for  how to get at your windows drive(s). Be sure to scroll down the page to the part about auto-mounting so that they will be available each time you boot.

---

### Post by senning on 2006-02-21
I seem to remember that not working, so just in case:

the lazy way (for a while) is to run gksudo nautilus from <alt>+<F2>.

The less lazy way is to add parameters in fstab.  Your group id can be found in System->Administration->Users and Groups.  Click on the Groups tab.  It may or may not probably be 1000.

the appropriate line in /etc/fstab should now look like this:
```
 /dev/hda1    /win98    vfat  defaults,gid=YOURGROUPID,umask=007   0  0 
```

---

