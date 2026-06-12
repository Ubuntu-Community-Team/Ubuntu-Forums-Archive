---
title: "Mounting an internal hard drive"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Redfro on 2006-10-18
Hoping one of yall can help me out here, im really new to Ubuntu. I have 2 hard drives on my computer. However i cannot access them or mount them. I try to 'mount volume' but i get an error....

error: device /dev/hdb1 is not removable

error: could not execute pmount

i saw a similar thread for this issue but it didnt really help me. Any clues? i understand that there is a pmount command in terminal. Im not afraid to use terminal, but i dont know how to use the command or what not......

---

### Post by jordanmthomas on 2006-10-18
Try using mount instead of pmount
i.e.
```
sudo mount /dev/hdb1 /path/to/mount/in
```
Where /path/to/mount/in is where you want it mounted.

---

### Post by Redfro on 2006-10-18
Pardon the noob-ity here, but cant i mount it in the same home folder that its already in? I think im completely missing the purpose of the 'mounting'

---

### Post by jordanmthomas on 2006-10-18
You are kind of missing it.
In Linux, everything is a file...including your drives.  Accessing /dev/hdb does not give you access to the drive's contents, but the drive itself.  To get to the contents, you must specify a location that it should be mounted to.

[http://www.ubuntuguide.org/wiki/Dapper](http://www.ubuntuguide.org/wiki/Dapper)

If your drive isn't formatted for linux (ie NTFS) look here for how to mount it.

If it is Linux-compatibile, just mount it like this:
```
sudo mkdir /media/NAME
sudo mount /dev/hdb /media/NAME

```
change NAME to something suitable.
Then, in the file manager, you should be able to browse to /media/NAME and see the contents of the drive.

You can make it permanent by adding a line to /etc/fstab  
Read up on it at the link I provided.  You should be able to understand, but if not...people are here to help.

---

### Post by Redfro on 2006-10-19
Thanks i got it. But now when i try to open the contents in the dir i specified, it says that i do not have the right permissions...im trying to figure this out on my own, honestly but i cant. Ive gone into the Properties for the folder but ti wont let me change the permissions there. Anything i can do?

---

### Post by bodhi.zazen on 2006-10-19
> **Redfro said:**
> Thanks i got it. But now when i try to open the contents in the dir i specified, it says that i do not have the right permissions...im trying to figure this out on my own, honestly but i cant. Ive gone into the Properties for the folder but ti wont let me change the permissions there. Anything i can do?

[list=number][*]Add options to your mount command.[*]Edit fstab.[/list]

Assuming your drive/partition is /dev/hdb1 and your mount point is /media/NAME (modify accordingly, I would use a mount point of /mnt/NAME):

```
sudo umount /media/NAME
sudo mount /dev/hdb1 /media/NAME -o user,rw
```

Edit fstab:```
sudo gedit /etc/fstab
```Add this line:> /dev/hdb1  /media/NAME  auto  auto,user,rw  0  0The drive will now mount on boot and you should have rw access.

---

### Post by Redfro on 2006-10-20
It didt seem to do anything. I tried using su and trying to change the permissions there but i kept getting the message that it was a read-only drive. I know this cant be as difficult as im making it.

---

### Post by tonyr1988 on 2006-10-20
To change the permissions of an individual folder, do:

> sudo chmod ### -R /path/to/dir

Where the ### represents the permissions. 777 basically gives everyone all rights. As to which one you should use, it depends what you need to use it for.

If you're just reading (not changing / adding anything), 744
If you're reading / writing, 766
If you're reading / writing / executing (programs), 777

The -R stands for "recursive", which basically means "change the permissions for this folder and everything inside of it."

But look to earlier posts on how to do this every time you reboot. If nothing else, you now know a little about chmod (if my post made any sense) :)

---

### Post by aysiu on 2006-10-20
The procedure for mounting Windows drives (FAT32, NTFS) is entirely different from the procedure for mounting Linux drives (Ext3, ReiserFS).

If you are using Windows drives/partitions, *chmod* and *chown* will not work.

Please follow these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Quintu on 2006-10-20
This is a problem for persons new to linux, and persons migrating to linux.  Any ub2 ubuntu users have an answer?

If an answer has been posted...  :)

---

### Post by bodhi.zazen on 2006-10-20
> **Quintu said:**
> This is a problem for persons new to linux, and persons migrating to linux.  Any ub2 ubuntu users have an answer?

If an answer has been posted...  :)

Interesting you should ask....

At any rate I believe the question was answered by aysiu and my revious post.

Settting the permissions of the mount point will not help as ownership and permissions (of the directory) will change at the time of the mount.

My guess would be one of two problems:

1. The drive in question must be umounted first, and then re-mounted.
2. The proper syntax was not used.

If you would like assistance please post the output of```
sudo fdisk -l
```and the contents of /etc/fstab:```
 gedit /etc/fstab
```Be sure to identify which partition you are having problems with and your mount point.

---

### Post by dmber on 2007-11-02
this is infuriating.  i have a 120 GB hdd in my tower that is giving me fits.  i should be able to mount and change permissions without having to go to the terminal.  i'm sorry if that rubs someone the wrong way, but this is truly one of the things holding Ubuntu back from the mainstream.  

here is my fdisk -l list:

emachine@emachine-tower:~$ sudo fdisk -l

Disk /dev/sda: 15.3 GB, 15382241280 bytes
255 heads, 63 sectors/track, 1870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1786    14346013+  83  Linux
/dev/sda2            1787        1870      674730    5  Extended
/dev/sda5            1787        1870      674698+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bdeaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux


here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=314a1122-dd69-4df2-9f53-f1facd689be2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=82aa738a-1b13-428c-8348-224cfa48f841 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1	/media/Dump	auto auto	user,rw	0	0

they probably both look funny or are wrong, but i just tried following the directions on the first page of this thread.  

the HDD i am trying to auto-mount on login with read/write permission is the 120GB hdd.

it is in a headless tower that i VNC into from my laptop.

thanks for the help.

---

### Post by dmber on 2007-11-02
awesome, i restarted after making the changes to fstab and now it doesn't even show up.  this is just super.

---

