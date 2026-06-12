---
title: "Can't read my windows partitions :("
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Nordoelum on 2006-04-03
Greetings,

Since I installed Ubuntu last friday, I could have viewed whats in my disks, but suddenly now it won't let me. Caliming I don't have the permission :(

I have tryed the guided on the Wiki. But is there someway I might remove in and start from the beginning?

---

### Post by frodon on 2006-04-03
Could you post your fstab file to see if the line is correct ? : ```
sudo gedit /etc/fstab
```It should look like that : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by taurus on 2006-04-03
Is that NTFS filesystem?  Maybe you want to use "umask=0222" to your /etc/fstab that would look something like
```

/dev/hda1  /media/windows  ntfs  defaults,umask=0222  0  0

```

---

### Post by Nordoelum on 2006-04-03
[quote=frodon]Could you post your fstab file to see if the line is correct ? : ```
sudo gedit /etc/fstab
```It should look like that : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")[/quote]

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

---

### Post by frodon on 2006-04-03
Well, your fstab line is the problem, just follow the link i gave you or modify your lines like taurus told you, it's the same.
the **umask=0222** option is missing and it's why you get permission problems.

---

### Post by Nordoelum on 2006-04-03
Should I remove the old ones then?

```
 /dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
```

---

### Post by meborc on 2006-04-03
just edit them, don't delete...

make your file look like this:> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /media/hda5     ntfs    nls=utf8,umask=0222        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

BUT be sure to make a backup so if something goes wrong you can 'fall back'

---

### Post by Nordoelum on 2006-04-03
[quote=meborc]just edit them, don't delete...[/quote]

Like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /media/hda5     ntfs    nls=utf8,umask=0222        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

---

### Post by frodon on 2006-04-03
exactly, and run these commands to unmout and remount all : ```
sudo umount -a
sudo mount -a
```

---

### Post by Nordoelum on 2006-04-03
[quote=frodon]exactly, and run these commands to unmout and remount all : ```
sudo umount -a
sudo mount -a
```[/quote]

It does work now :D Thank you all :D:D

---

