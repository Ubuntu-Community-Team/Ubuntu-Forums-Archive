---
title: "changing disk owner"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by metalsam on 2006-11-12
I have a second harddrive in my computer I keep music on, however, I cannot rip CDs straight to it using desktop programs.

I added my user to the 'disk' group, but that  hasnt worked. How do I change the owner of the disk from root to user ?

thanks.

---

### Post by taurus on 2006-11-12
Is it fat32/vfat or ext3?

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by bodhi.zazen on 2006-11-12
> **metalsam said:**
> I have a second harddrive in my computer I keep music on, however, I cannot rip CDs straight to it using desktop programs.

I added my user to the 'disk' group, but that  hasnt worked. How do I change the owner of the disk from root to user ?

thanks.

You need to have the proper entry in [fstab](http://ubuntuforums.org/showthread.php?t=283131).

Setting permissions depends on what type of FS is on the partitions (ntfs, fat, ext3, etc...).

If you are having troubble please post more information (partition and FS type).

---

### Post by metalsam on 2006-11-12
its a fat32 partition taking up the whole secondary hard drive (hdb5).

my fstab entry:
```

/dev/hdb5       /mnt/storage    vfat    defaults        0       1

```

EDIT: I tried kdesu konqueror and when editing the permissions on the moount point /mnt/storage i was told i had insufficient permissions :s

---

### Post by bodhi.zazen on 2006-11-12
> **metalsam said:**
> its a fat32 partition taking up the whole secondary hard drive (hdb5).

my fstab entry:
```

/dev/hdb5       /mnt/storage    vfat    defaults        0       1

```

Modify fstab and add an entry like this(sudo gedit /etc/fstab):

> /dev/hdb5  /mnt/storage  vfat  users,auto,umask=000  0  0     

Unmount and re-mount the partition:```
sudo umount /mnt/storage
mount /mnt/storage
```_Note_: No sudo on that re-mount !

---

### Post by bodhi.zazen on 2006-11-12
Edit: Wrong thread :(

---

### Post by metalsam on 2006-11-12
thank you !

It works ! woopee !

---

### Post by bodhi.zazen on 2006-11-12
> **metalsam said:**
> thank you !

It works ! woopee !

8)

---

### Post by myradio on 2008-05-01
I can't make it work, i show you ehat i'm doing:


that's what i have found in my /etc/fstab:

> # /dev/sda1
UUID=4460FBB960FBB032 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1      1000

and i've replaced by the following line:

> UUID=4460FBB960FBB032 /media/sda1     ntfs users,auto,umask=000 0 0


so, i've tried:

> nico@ubuntu:~$ sudo umount /media/sda1
nico@ubuntu:~$ mount /media/sda1
Error opening partition device: Permission denied
Failed to mount '/dev/sda1': Permission denied


i've also tried leaving both lines 
> UUID=4460FBB960FBB032 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1      1000
UUID=4460FBB960FBB032 /media/sda1     ntfs users,auto,umask=000 0 0

but it doesn't work 
> nico@ubuntu:~$ sudo umount /media/sda1
nico@ubuntu:~$ mount /media/sda1
mount: only root can mount /dev/sda1 on /media/sda1


thanks in advice




VIKOOOO

---

### Post by bodhi.zazen on 2008-05-01
If you want read-write access you need ntfs-3g (rather then ntfs)

Second, only list your partition once in fstab. If you want to preserve a record of changes use # to comment out a line.

```
UUID=4460FBB960FBB032 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1      1000
UUID=4460FBB960FBB032 /media/sda1     ntfs users,auto,umask=000 0 0
```

So, try this :

```
UUID=4460FBB960FBB032 /media/sda1     ntfs-3g user,auto,uid=1000,gid=100,umask=007 0 0
```

---

### Post by mgranet on 2008-05-01
Thanks, **Bodhi.zazen**. You just saved me a bunch of time!:)

---

### Post by myradio on 2008-05-01
sorry guys, but it didn't work for me.

actually, i'm worse now, since  i need to be root not only to mounting but also to read that from disk.

trying to mount as user
> nico@ubuntu:~$ mount /media/sda1
Error opening partition device: Permission denied
Failed to mount '/dev/sda1': Permission denied

i can only do it with sudo
> nico@ubuntu:~$ sudo mount /media/sda1

but i still cannot access
> nico@ubuntu:~$ cd  /media/sda1
-bash: cd: /media/sda1: Permission denied

the only way is being root
> nico@ubuntu:~$ sudo su
root@ubuntu:/home/nico# cd /media/sda1
root@ubuntu:/media/sda1#

---

### Post by bodhi.zazen on 2008-05-01
What is in your /etc/fstab ?

---

### Post by myradio on 2008-05-01
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a69b6d92-99f5-4adb-a041-82137ec67010 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=CC9406C19406ADD0 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=4460FBB960FBB032 /media/sda1     ntfs-3g user,auto,uid=1000,gid=100,umask=007 0 0
# /dev/hda2
UUID=86497be5-76e7-4957-97f4-f0c3498dfd8e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


what i don't know if have i to make ubuntu reload that file (/etc/fstab) or something

---

