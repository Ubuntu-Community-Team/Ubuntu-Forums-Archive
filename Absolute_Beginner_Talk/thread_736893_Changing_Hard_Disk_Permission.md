---
title: "Changing Hard Disk Permission"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by J0hnnySick0 on 2008-03-27
Ok, I know you will all tell me to search and I have.
I have tried all of those things even logging into root.
i cant change the owner because its a read only drive and when I try to chmod it I can't because it's read only.
Does anyone have an idea of what to do?
and just a quick off topic question, If I click on the upgrade button in the update manager, will I loose my data?

---

### Post by wormser on 2008-03-27
You did not really explain what the issue is.   What type of drive is this?  Did you try putting **sudo** in front of the chmod?  Post the permissions of the drive.  Use **ls -la /path/to/drive**.  Upgrading will not lose your data.

---

### Post by hyper_ch on 2008-03-27
as long as the drive is mounted as read-only you can't change permissions...

---

### Post by stefangr1 on 2008-03-27
What you could try is this:

go to the run dialog by pressing Alt+F2

type in: 

sudo konqueror /media

Then go right click on the folder the partition is mounted in, choose options, go to the permissions tabblad, change User and Group to your username, and enable "Apply changes to all subfolders and their content".

---

### Post by stefangr1 on 2008-03-27
If that doesn't help, you should make sure that the options in your /etc/fstab are correct. Maybe you can post what's in that so we can see if the mount options are set right.

---

### Post by Tomatz on 2008-03-27
Are you sure its not an NTFS file system (windows)?

---

### Post by J0hnnySick0 on 2008-03-27
> jordan@jordan-desktop:~$ ls -la /media/disk
total 416028
dr-xr-xr-x 1 root root      8192 2008-01-16 21:27 .
drwxrwxrwx 5 root root      4096 2008-03-27 19:01 ..
-r-xr-xr-x 2 root root    302152 2007-09-27 18:29 180px-Loooooooooooooooooooooooooooooooooooooooooongcat.JPG
-r-xr-xr-x 2 root root  75257886 2007-07-30 20:21 Aio_FolderFile_Hide_Lock_Encrypt_Tools_40in1.exe
dr-xr-xr-x 1 root root         0 2008-01-09 21:49 atilla
dr-xr-xr-x 1 root root         0 2007-08-04 14:36 clones
-r-xr-xr-x 2 root root    258111 2007-09-11 07:30 diveintogreasemonkey-html-2005-05-09.zip
dr-xr-xr-x 1 root root      4096 2007-08-19 13:06 GamerXP
-r-xr-xr-x 2 root root 253817159 2007-08-12 03:13 gtavcmovie.zip
-r-xr-xr-x 2 root root   3084594 2007-08-11 17:58 Image_Grabber_II.NET.rar
dr-xr-xr-x 1 root root      4096 2007-09-27 18:08 keaton music
-r-xr-xr-x 1 root root    448668 2007-08-04 18:31 Kristen2.rar
dr-xr-xr-x 1 root root         0 2007-07-29 12:05 rainbow6
dr-xr-xr-x 1 root root         0 2007-08-04 12:47 RECYCLER
-r-xr-xr-x 1 root root  92769058 2007-08-02 02:04 SS-US.zip
dr-xr-xr-x 1 root root      4096 2007-07-16 13:16 System Volume Information
dr-xr-xr-x 1 root root     32768 2007-08-02 17:03 trans
dr-xr-xr-x 1 root root         0 2007-08-04 12:47 Youtube Clone


Yes i've tried using sudo, but to no avail.

> as long as the drive is mounted as read-only you can't change permissions...
How do I change this?

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=9676d1f0-0202-4c96-98b4-0fd83a8468bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=b01c0279-6c45-49f8-b04a-29fa25a41dd0 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

There is my fstab.

> Are you sure its not an NTFS file system (windows)?
It could be, is this bad?

---

### Post by akimatsu123 on 2008-03-27
i don't quite fully understand your question. are you saying you can't access a hard drive from a user account because you don't have the right privilages for some reason? or are you saying that your drive just won't mount. 

if you don't have the privilages and you are an administrator you can just navigate to /media and "sudo chmod u+rx <drive name>" that gives you permission to read and execute anything on it

i'm not an expert on this issue i only know how to change permissions but im thinking maybe you can boot it on a LiveCD and change the permissions from there? i'm not sure if that would stay after you reboot though...

---

### Post by J0hnnySick0 on 2008-03-27
@akimatsu123
The problem is that the drive is set to read only and it wont let me change it no matter what I try.
I'll try what you said though.

edit:
After trying I get the same result as before
> jordan@jordan-desktop:/media$ sudo chmod u+rx disk
chmod: changing permissions of `disk': Read-only file system
jordan@jordan-desktop:/media$ 


---

### Post by J0hnnySick0 on 2008-03-27
> **hyper_ch said:**
> as long as the drive is mounted as read-only you can't change permissions...

Does this mean i could right click and unmount the drive then chmod it?

---

### Post by J0hnnySick0 on 2008-03-27
Sorry for the tripple post but un mounting it did nothing.

---

### Post by J0hnnySick0 on 2008-03-27
Ok I have found out that it is ntfs (3.1)
Now what?

---

### Post by wormser on 2008-03-27
Try this.  Applications> Accessories> Terminal

```
sudo apt-get install ntfs-config
```

Applications> System Tools> NTFS Configuration Tool> Enable write support for external device.

---

### Post by J0hnnySick0 on 2008-03-28
That found a partition I didn't know I had, but now i cant find the disk i want access to in the first place

---

### Post by J0hnnySick0 on 2008-03-28
I cant find the hard drive i wanted access to.

---

### Post by J0hnnySick0 on 2008-04-06
Blatant bump.

---

### Post by vanadium on 2008-04-06
It may help to get help if your problem were clearer. It is not clear to me whether this concerns an external USB drive or an internal drive, or what Ubuntu version you have. At that point, we just can do wild guesses. That's all.

For a new start, first post some information on your system: tell us what Ubuntu version you are using and then post the output here of the following commands:

sudo fdisk -l
mount

The first command tells what drives and what partitions your system recognises, the second one what is currently mounted. Then we need to identify which of the drives is your problem drive and what the problem is.

---

