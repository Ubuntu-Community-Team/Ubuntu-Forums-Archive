---
title: "Mounting a new partition for Linux"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by CalvinChile on 2006-06-03
Hi, this must be easy, but still ](*,) .
I have a dual boot (XP , Dapper)  laptop, and decided to reduce the XP partition and with the   new 10G available I created a new partition ext3 formated. I want to use this space as an extention to my home directory  but every time I try to write something on it I got error, as it is owned by root. What do I have to put in fstab to be able to mount and use the partition?
I created a mounting point on /media/Disk10G and set fstab as:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0
 1
/dev/sda5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /media/Windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0
/dev/sda4 /media/Disk10G ext3 owner,errors=remount-ro,atime,auto,rw,dev,exec,sui
d 0 1

and this is the output from fdisk =>

nhaddad@Inspiron6400:~$ sudo fdisk -l
Password:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            6375        9413    24410767+  83  Linux
/dev/sda3            9414        9546     1068322+   5  Extended
/dev/sda4            5100        6374    10241437+  83  Linux
/dev/sda5            9414        9546     1068291   82  Linux swap / Solaris

Partition table entries are not in disk order


Thanks
Calvin

---

### Post by aysiu on 2006-06-03
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by Sutekh on 2006-06-03
[quote=CalvinChile]
/dev/sda4 /media/Disk10G ext3 owner,errors=remount-ro,atime,auto,rw,dev,exec,sui
d 0 1
[/quote] Because you chose ext3 as the format you have really simplified things.

All you need to do is change the owner of, and the modes of access (permissions) to the mount folder
```
sudo chown  -R nhaddad: nhaddad /media/Disk10G
sudo chmod -R 777 /media/Disk10G
``` 
 Also I'd keep the fstab simple
```
 /dev/sda4 /media/Disk10G ext3 defaults 0 2
```


Edit: Oh you have a mounting Linux link aysiu?  Nice.

---

### Post by aysiu on 2006-06-03
[QUOTE=Sutekh]
Edit: Oh you have a mounting Linux link aysiu?  Nice.[/QUOTE] I do now. After a while, you get tired of typing out the same instructions over and over again.

---

### Post by Sutekh on 2006-06-03
[quote=aysiu]I do now. After a while, you get tired of typing out the same instructions over and over again.[/quote]
True true.  I have a broken collarbone, so I need more links like that.

---

### Post by CalvinChile on 2006-06-03
:) Thanks al lot for your help aysiu and Sutekh!! It worked just fine

Another question: will this partition be mounted at boot time?

Calvin

---

### Post by Sutekh on 2006-06-03
[quote=CalvinChile]:) Thanks al lot for your help aysiu and Sutekh!! It worked just fine

Another question: will this partition be mounted at boot time?

Calvin[/quote]No problem.

If the partition is in the fstab, the system should attempt to mount it at boot time automatically.

---

### Post by CalvinChile on 2006-06-04
A strange thing happened.  When I booted up my  system today, I realized that again /dev/sda4 belongs to root, even though yesterday night I did:

sudo chown  -R nhaddad: nhaddad /media/Disk10G
sudo chmod -R 777 /media/Disk10G

if I issue an ls -l /dev/sda4 I get:
brw-rw---- 1 root disk 8, 4 2006-06-04 11:21 /dev/sda4

Is there any way to make the changes permanent?

Regards,
Calvin

---

### Post by aysiu on 2006-06-04
The change should have been permanent.
That's weird.

---

### Post by CalvinChile on 2006-06-04
:mrgreen:  Sorry, my error.... I had a typo on fstab ("dafaults" instead of defaults)

---

### Post by cyracks on 2006-06-04
[quote=CalvinChile]
/dev/sda1 /media/Windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser[/quote] 
It is more secure to write something like:
```

/dev/sda1 /media/Windows ntfs defaults,nls=utf8,**uid=user,gid=group**       0       0

``` 
Instead of umask 0222.

---

### Post by aysiu on 2006-06-04
[QUOTE=cyracks]It is more secure to write something like:
```

/dev/sda1 /media/Windows ntfs defaults,nls=utf8,**uid=user,gid=group**       0       0

``` 
Instead of umask 0222.[/QUOTE] I'm a newbie when it comes to /etc/fstab. Can you explain a bit why that's more secure than *umask=0222*? Isn't 0222 read-only?

---

### Post by cyracks on 2006-06-04
Sorry my mistake. I assumed 0222 is for read and write.
btw: all options avaliable in fstab are described in *man mount* under -o option.

---

### Post by nanotube on 2006-06-04
[QUOTE=aysiu]I'm a newbie when it comes to /etc/fstab. Can you explain a bit why that's more secure than *umask=0222*? Isn't 0222 read-only?[/QUOTE]

well, it is more secure in that, mounting with uid=youruid and giving umask 0277 (or 0077, if you want to write it), gives just your user access to partition, and not any other users. whereas leaving it as root, with umask 0222 lets everyone read the stuff.

it does not matter for a single-user desktop system, but if that disk is "your data" you wouldn't want to let other users on the system read it, would you? so to my mind, coming from sysadmin background, i'd go with the uid approach, just in case you ever want to give someone else an account on your system. :)

so in the end, it all depends on what you want to do

---

### Post by aysiu on 2006-06-04
Thanks for the explanation, nanotube. Much appreciated.

---

