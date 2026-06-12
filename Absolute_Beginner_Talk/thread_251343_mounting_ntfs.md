---
title: "mounting ntfs"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-09-05
following all the different threads and how to's. still cannot mount ntfs even when in file system.....
sailor@sailor-desktop:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
sailor@sailor-desktop:~$ sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,unmask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

sailor@sailor-desktop:~$

---

### Post by taurus on 2006-09-05
Edit /etc/fstab and add the following line to it...

```

gksudo gedit /etc/fstab <--  edit /etc/fstab...)

```

```

/dev/hda2  /media/windows  ntfs   nls=utf8,umask=0222  0  0

```
Save the change and at the prompt, mount it with

```

sudo mount -a
df -h <-- you will see your XP in /media/windows...

```

---

### Post by sailor2001 on 2006-09-05
sailor@sailor-desktop:~$ sudo /etc/fstab
Password:
sudo: /etc/fstab: command not found
sailor@sailor-desktop:~$ etc/fstab
bash: etc/fstab: No such file or directory
sailor@sailor-desktop:~$

---

### Post by taurus on 2006-09-05
> **sailor2001 said:**
> sailor@sailor-desktop:~$ sudo /etc/fstab
Password:
sudo: /etc/fstab: command not found
sailor@sailor-desktop:~$ etc/fstab
bash: etc/fstab: No such file or directory
sailor@sailor-desktop:~$
Where do you get the "sudo /etc/fstab" from anyway???  If you look at my post, I have

```
gksudo gedit /etc/fstab
```
](*,)

---

### Post by btdown on 2006-09-05
Isnt is '**umask**' instead of unmask?

---

### Post by taurus on 2006-09-05
> **btdown said:**
> Isnt is '**umask**' instead of unmask?
Yes, it is.  I just copied 'n paste without even looking at the syntax!  My bad on that part...

---

### Post by sailor2001 on 2006-09-05
starting all over again...........
sailor@sailor-desktop:~$ /etc/fstab
bash: /etc/fstab: Permission denied
sailor@sailor-desktop:~$

---

### Post by Jukey on 2006-09-05
```
gksudo gedit /etc/fstab
```

---

### Post by taurus on 2006-09-05
> **sailor2001 said:**
> starting all over again...........
sailor@sailor-desktop:~$ /etc/fstab
bash: /etc/fstab: Permission denied
sailor@sailor-desktop:~$
Okay, I will repeat this whole thing over again...  If you want to edit your /etc/fstab, you need to run

```
gksudo gedit /etc/fstab
```
Then, add this line to the end of your /etc/fstab.

```

/dev/hda2  /media/windows  ntfs   nls=utf8,umask=0222  0  0

```
Save it and at the prompt, do

```

sudo mount -a

```

---

### Post by sailor2001 on 2006-09-05
sailor@sailor-desktop:~$ sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: special device dev/hda1 does not exist
mount: mount point /fat_files does not exist
sailor@sailor-desktop:~$

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto   /dev/hda2  /media/windows  ntfs   nls=utf8,umask=0222  0  0  0       0

---

### Post by sailor2001 on 2006-09-05
sailor@sailor-desktop:~$ gksudo gedit /etc/fstab

(gedit:14343): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
sailor@sailor-desktop:~$

---

### Post by taurus on 2006-09-05
> **sailor2001 said:**
> sailor@sailor-desktop:~$ sudo mount -a
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: special device dev/hda1 does not exist
mount: mount point /fat_files does not exist
sailor@sailor-desktop:~$

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto   /dev/hda2  /media/windows  ntfs   nls=utf8,umask=0222  0  0  0       0

The /dev/hda2 should be on a new line and you have way too many 0s at the end.  You only need two, 0 0, NOT four, 0 0 0 0...

---

### Post by taurus on 2006-09-05
> **sailor2001 said:**
> sailor@sailor-desktop:~$ gksudo gedit /etc/fstab

(gedit:14343): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
sailor@sailor-desktop:~$
That is just a warning, not an error so won't worry about the warning thing...

---

### Post by sailor2001 on 2006-09-05
getting that on a new line did the trick.... thanks taurus

---

### Post by taurus on 2006-09-05
So everything is working fine now!  =D>

---

