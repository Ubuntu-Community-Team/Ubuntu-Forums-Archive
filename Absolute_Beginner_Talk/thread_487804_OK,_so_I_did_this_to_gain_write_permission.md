---
title: "OK, so I did this to gain write permission"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by dhar2112 on 2007-06-29
on my external drive:


[B][B][I]Open a terminal, go to that drive and create a new directory and make yourself the owner:

Code:

cd <whatever_the_mountpoint_is>
sudo mkdir mystuff
sudo chown yourlogin:yourlogin mystuff

Now you can put anything under the mystuff directory.
[/I][/B][/B]
Seemed to work fine.  I copied and pasted an mp3 into the "mystuff" folder.  Then, I exited out, came back in and it's telling me that the "mystuff" folder is  write protected again and I cannot copy any mp3s into it.  

Argggh!!!!

---

### Post by buuntuu! on 2007-06-29
read up [here]("http://www.linuxcommand.org/lts0070.php")
on permissions. 

if you need some help please postback  the output of
```
ls -l -d /path/to/your/directory
```
so we can see who has become the ownerof the folder...

---

### Post by dhar2112 on 2007-06-29
Here ya' go!:

drwxr-xr-x 2 david david 4096 2007-06-29 10:47 /media/disk/mystuff

---

### Post by dhar2112 on 2007-06-29
This is the owner of the drive:

drwxr-xr-x 4 root root 4096 2007-06-29 10:45 /media/disk

Do I need to change the "root:root" to "david:david?"

---

### Post by pistcivet on 2007-06-29
> **dhar2112 said:**
> Here ya' go!:

drwxr-xr-x 2 david david 4096 2007-06-29 10:47 /media/disk/mystuff

Of course this is correct (if your username is david)

Just for completeness, could you post output from:
```
ls -la /media/disk/mystuff/
cat /etc/fstab
sudo fdisk -l     <----(that is a lowercase L)
```
That should be enough to tell what is wrong.

No. you do not need to be the owner of /media/disk/
just owner of /media/disk/mystuff/

---

### Post by buuntuu! on 2007-06-29
this makes more sense ;)
(was a little stunned by post#3)

as root is the owner (cause you created the folder using "sudo" and the file permissions say that only the owner may write to it), you'll need to become owner of the file:
```
 chown david /media/disk 
```
and david will be the owner!

it's good to doublecheck the commandline-help you get. if you don't know what you are doing you can really get stuck easily!

EDIT: sorry for the typo!, see why doublechecking is so important?

---

### Post by dhar2112 on 2007-06-29
david@david-laptop:~$ ls -la /media/disk/mystuff/
total 8
drwxr-xr-x 2 david david 4096 2007-06-29 10:47 .
drwxr-xr-x 4 root  root  4096 2007-06-29 10:45 ..
david@david-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=b1086bd1-a42c-4398-817b-66796965646f / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=abc87073-c7d0-401a-883d-ea30891369e7 none swap sw 0 0
/dev/scd0 /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0
david@david-laptop:~$ sudo fdisk -l 
Password:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1788    14362078+   7  HPFS/NTFS
/dev/sda2            1789        3564    14265720   83  Linux
/dev/sda3            3565        3648      674730    5  Extended
/dev/sda5            3565        3648      674698+  82  Linux swap / Solaris

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19929   160079661    c  W95 FAT32 (LBA)
david@david-laptop:~$

---

### Post by pistcivet on 2007-06-29
Whoa! this is getting really confusing.
If this external drive is formatted to FAT32, permissions are meaningless.
FAT32 doesn't know anything about them.
Whats the output of```
mount
```
Maybe you should forget about all this and post a new thread.
Make sure people know you're having problems with an external FAT32 drive.

Edit: from the output of your previous post
I can see there are no files at all in /media/disk/mystuff/
But the permissions are correct - for anything except FAT32 or NTFS.

---

### Post by buuntuu! on 2007-06-29
of course there is always the gui approach
```
 gksudo nautilus
```
to open nautilus as root.
rightclick the folder in question (i'm a bit confused now, are we talking about /media/disk or /media/disk/mystuff)
> properties > file permissions
make yourself owner and group of the file and select all the permissions for the owner of the file.

seems easier than the command line, but cl helps to understand what's going on!

---

