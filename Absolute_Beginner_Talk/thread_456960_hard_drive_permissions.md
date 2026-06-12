---
title: "hard drive permissions"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by sdbkr on 2007-05-28
hi have formatted a second hard drive but don't know how to change the permissions so i can write to it. followed some other advice but the only thing that has changed is that i get an odd message at start up which says /dev /hda1 has been mounted 35 times without being checked, check forced. anyone know what i should do ?

---

### Post by taurus on 2007-05-28
What's the filesystem on that second harddrive?  Post this output of a terminal if you're not sure.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by sdbkr on 2007-05-28
i formatted it with gparted and used ext3 

sudo fdisk -l 
gives 

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4834    38829073+  83  Linux
/dev/hda2            4835        4998     1317330    5  Extended
/dev/hda5            4835        4998     1317298+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2480    19920568+  83  Linux

---

### Post by taurus on 2007-05-28
And where do you mount /dev/hdb1?  All you need to do is to change the ownership of the mount point for /dev/hdb1 from root to your login name.  Then, you can write to it anytime you want.  _Assuming_ /dev/hdb1 is mounted to /media/hdb1 and your login name is **john**, do

```
sudo chown -R **john**:**john** /media/hdb1
ls -la /media
```

---

### Post by sdbkr on 2007-05-28
ok 

sudo chown -R stephen:stephen /media/hdb1
ls -la /media 

gives 

chown: cannot access `/media/hdb1': No such file or directory

---

### Post by taurus on 2007-05-28
> **sdbkr said:**
> ok 

sudo chown -R stephen:stephen /media/hdb1
ls -la /media 

gives 

chown: cannot access `/media/hdb1': No such file or directory

If you look at my previous post, last sentence, I **_assume_** you mount /dev/hdb1 to /media/hdb1.  Where do you mount /dev/hdb1?

```
cat /etc/fstab
-or-
df -h
```

---

### Post by sdbkr on 2007-05-28
i haven't a clue where i mount it. i wish i'd known ubuntu was for programmers only. typed 
 cat /etc/fstab
into the terminal and got 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=45bac8f5-9e05-41ce-9d7d-14368ce706a8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=734b7eef-904d-424a-8608-bcad4db72e51 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1/storage ext3 defaults 0 0


does that clarify things ?

---

### Post by taurus on 2007-05-28
> **sdbkr said:**
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=45bac8f5-9e05-41ce-9d7d-14368ce706a8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=734b7eef-904d-424a-8608-bcad4db72e51 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**[COLOR="Blue"]/dev/hdb1/storage ext3 defaults 0 0[/COLOR]**


You mount it to /storage.

```
sudo chown -R stephen:stephen /storage
```

---

### Post by GrueTamer on 2007-05-28
Makre sure that the directory exists before you mount it.  It looks like it might be mounted in /storage, so in the terminal, type ```
cd /storage
```.  If it works, try ```
sudo chown -R stephen:stephen /storage
```, and then tell me the ls -la /storage output.  If it doesn't work, then do a ```
mkdir /storage
```, and then try.

---

### Post by ugm6hr on 2007-05-28
For everyone helping here - I've just seen this, and thought I should admit responsibility for where sdbkr is at the moment:

> **ugm6hr said:**
> This should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Just substitute "/dev/hda5" with "/dev/hdb1" and "marie:marie" with "*yourusername:yourusername*"

Then it should appear in nautilus as /storage (or if you want it somewhere else - just sustitute "/storage" with "/*whatever_directory_i_want*" 


And looking at the /etc/fstab entry he's supplied, I think there's a SPACE missing before "/storage":
/dev/hdb1/storage ext3 defaults 0 0

Could this be the problem?

---

### Post by sdbkr on 2007-05-28
thanks 
tried that but no change 
when i type 
sudo chown -R stephen:stephen /storage
it just reverts to the cursor 
second hard drive has stopped appearing in /media again 
although it still shows up on the panel and can be opened from the panel. 
incidentally what is the lost + found folder ?

---

### Post by sdbkr on 2007-05-28
when i said no change i mean i still can't write to it because it gives a message saying i don't have permission

---

### Post by taurus on 2007-05-28
The reason it doesn't appear on your desktop because you mount it to /storage instead of /media/storage.  What's the output of this command from a terminal?

```
ls -la /
```
Perhaps you need to reboot.

---

### Post by sdbkr on 2007-05-28
hi 

now i've got 

stephen@stephen-desktop:~$ sudo chown -R stephen:stephen /storage
stephen@stephen-desktop:~$ cd /storage

is that right ?

---

### Post by sdbkr on 2007-05-28
hi 

the result of 

ls -la / 

is : 

stephen@stephen-desktop:~$ ls -la /
total 88
drwxr-xr-x  22 root    root     4096 2007-05-28 11:20 .
drwxr-xr-x  22 root    root     4096 2007-05-28 11:20 ..
drwxr-xr-x   2 root    root     4096 2007-05-04 11:53 bin
drwxr-xr-x   3 root    root     4096 2007-05-28 11:07 boot
lrwxrwxrwx   1 root    root       11 2007-05-04 11:38 cdrom -> media/cdrom
drwxr-xr-x  12 root    root    14040 2007-05-28 13:26 dev
drwxr-xr-x 110 root    root     4096 2007-05-28 15:09 etc
drwxr-xr-x   3 root    root     4096 2007-05-04 11:50 home
drwxr-xr-x   2 root    root     4096 2007-04-15 12:48 initrd
lrwxrwxrwx   1 root    root       33 2007-05-28 11:08 initrd.img -> boot/initrd.img-2.6.20-16-generic
lrwxrwxrwx   1 root    root       33 2007-05-04 11:52 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  16 root    root     4096 2007-05-04 11:53 lib
drwx------   2 root    root    16384 2007-05-04 11:38 lost+found
drwxr-xr-x   6 root    root     4096 2007-05-28 15:09 media
drwxr-xr-x   2 root    root     4096 2007-04-12 10:11 mnt
drwxr-xr-x   2 root    root     4096 2007-04-15 12:48 opt
dr-xr-xr-x 123 root    root        0 2007-05-28 13:24 proc
drwxr-xr-x  11 root    root     4096 2007-05-27 19:45 root
drwxr-xr-x   2 root    root     4096 2007-05-28 11:06 sbin
drwxr-xr-x   2 root    root     4096 2007-04-15 12:48 srv
drwxr-xr-x   2 stephen stephen  4096 2007-05-28 11:20 storage
drwxr-xr-x  11 root    root        0 2007-05-28 13:24 sys
drwxrwxrwt  16 root    root     4096 2007-05-28 15:21 tmp
drwxr-xr-x  11 root    root     4096 2007-04-15 12:50 usr
drwxr-xr-x  15 root    root     4096 2007-04-15 13:01 var
lrwxrwxrwx   1 root    root       30 2007-05-28 11:08 vmlinuz -> boot/vmlinuz-2.6.20-16-generic
lrwxrwxrwx   1 root    root       30 2007-05-04 11:52 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic

---

### Post by taurus on 2007-05-28
> **sdbkr said:**
> hi 

now i've got 

stephen@stephen-desktop:~$ sudo chown -R stephen:stephen /storage
stephen@stephen-desktop:~$ cd /storage

is that right ?

Yip.  The first comment changes ownership of /storage from root to stephen (with stephen group) and the second command changes directory to /storage.  See what happens when you run this command after you've done the "cd /storage" one?

```
touch text
ls -la 
```

---

### Post by sdbkr on 2007-05-28
when i do what you suggest i get 

stephen@stephen-desktop:~$ cd /storage
stephen@stephen-desktop:/storage$ touch text
stephen@stephen-desktop:/storage$ ls -la
total 8
drwxr-xr-x  2 stephen stephen 4096 2007-05-28 15:50 .
drwxr-xr-x 22 root    root    4096 2007-05-28 11:20 ..
-rw-r--r--  1 stephen stephen    0 2007-05-28 15:50 text
stephen@stephen-desktop:/storage$ 


still can't write to it but it does show up in /media now

---

### Post by taurus on 2007-05-28
> **sdbkr said:**
> when i do what you suggest i get 

stephen@stephen-desktop:~$ cd /storage
stephen@stephen-desktop:/storage$ touch text
stephen@stephen-desktop:/storage$ ls -la
total 8
drwxr-xr-x  2 stephen stephen 4096 2007-05-28 15:50 .
drwxr-xr-x 22 root    root    4096 2007-05-28 11:20 ..
[COLOR="Blue"]-rw-r--r--  1 stephen stephen    0 2007-05-28 15:50 text[/COLOR]
stephen@stephen-desktop:/storage$ 

still can't write to it but it does show up in /media now

You just created a file in /storage so you can write to it now.

If you want to remove text, run

```
cd /storage
rm text
```

---

### Post by sdbkr on 2007-05-28
not sure what you mean, remove text. the second hard drive appears in /media as disk. permissions are restricted to root. i wanted to be able to back up to an archive in the second hard drive because linux doesn't always recognise the flash card that i used to use as a back up when i used windows. also ubuntu doesn't recognise my usb hub. or let me write to cd.

---

### Post by BennyHill on 2007-05-30
sorry to butt in, but these posts have helped a fellow 'Linux newb' Ubuntu user, a great deal, so thanks all, now off to keep enjoying Ubuntu :)

---

