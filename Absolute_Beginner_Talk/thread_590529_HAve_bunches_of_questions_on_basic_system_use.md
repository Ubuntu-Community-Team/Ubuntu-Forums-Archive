---
title: "HAve bunches of questions on basic system use"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by maskeeper on 2007-10-24
So this is kind of embarrassing, I'm a long time windows user with tons of professional admin experience, but I'm somehow managed to avoid linux by working in windows centric offices.  I finally decided to start playing with ubuntu with the eventual goal of using it as a media fileserver-- and here I am.  I used unix back in the mid 90's on systems, but usually just as a c++ development ievironment/compiler- and I remember like 3 commands...

So first things:

I have 3 drives in this machine.  I managed to get them formatted and partitioned.  They mount (and show up on the desktop): sdb1  sdc6 (although I dunno what the labels mean).

I want to create directories and copy files to these- but:

The make folder command is greyed out in gnome (right click).
I cannot figure out how to use terminal to navigate to these drives to make the directory that way.

The drives show a folder called Lost+found... but ti seems these drives aren't mounted correctly or initialized or something, as they appear but as not able to be written to,..

Any tips?  Even links on basic linux drive usage would be appreciated!

Thanks

---

### Post by taurus on 2007-10-24
Sounds like they are formatted to ext3 (Lost+found directory).  All you need is to change the ownership of those partitions/mount points from root to your login name and you can write to them anytime you want.  

Do you know where those three partitions are mounted--mount points?

Post the output of these commands from a terminal here.

```
mount
sudo fdisk -l
```
That is a lower case letter l, not 1.

---

### Post by ofb on 2007-10-24
> **maskeeper said:**
> I remember like 3 commands...
Good news: those still work.

Perhaps to start, enter 'cat /etc/fstab' in terminal to show us how things are mounted.

EDIT: Whups - taurus is already on it. Carry on.

---

### Post by maskeeper on 2007-10-24
I am able to navigate to these via command line as if they are mounted in "media".

cd /media/sdb1
cd /media/sdc6


With **MOUNT** command I get
```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw)
/dev/sdc6 on /media/sdc6 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

With **sudo fdisk -l** command I get
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9349    75095811   83  Linux
/dev/sda2            9350        9726     3028252+   5  Extended
/dev/sda5            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d2e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9726    78124063+  83  Linux

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005641a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc3               1       48641   390708801    5  Extended
/dev/sdc5           48265       48641     3028221   82  Linux swap / Solaris
/dev/sdc6               1       48264   387680485+  83  Linux

Partition table entries are not in disk order

```

with **cat /etc/fstab** command I get:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=daea86bf-136a-4a2f-8283-a38232becf3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=3c18a6a8-7527-4602-bfbc-dc6759658fec /media/sdb1     ext3    defaults        0       2
# /dev/sdc6
UUID=53d9bf9f-d074-4f34-a392-0832f6f07b5c /media/sdc6     ext3    defaults        0       2
# /dev/sda5
UUID=0405ebc5-86c2-474f-8c4a-3667428a7708 none            swap    sw              0       0
# /dev/sdc5
UUID=3399cfde-6b4e-49e1-9268-9b5cb7df0946 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```


I did manage to navigate to the mount points and use mkdir to create directories.  Of course it won't let me write anything to them, nor delete them...

You're right, when using gparted I set it to ext3, because this was the default... I wasn't sure the advanatges/disadvatages of the 2 versions of ext file system.

---

### Post by taurus on 2007-10-24
_Assuming_ your login name is **maskeeper** (replace it with the right one), do

```
sudo chown -R **maskeeper**:**maskeeper** /media/sdb1 /media/sdc6
ls -la /media
```
Now, you should be able to write to both /media/sdb1 & /media/sdc6 anytime you want.

---

### Post by Paul133 on 2007-10-24
Not entirely sure how drives work, but I believe UNIX views everything as a file, right? So maybe you can change the permissions or ownership.

edit: Ah, you seem to have gotten some great advice. Good luck.

---

### Post by maskeeper on 2007-10-24
Thanks so much for taking the time to hang out here to help newbies.  I much appreciate...

So I assume the chown command is 'change ownership.'  If I want to see all the switches of a given command - how do I do that? (Like in DOS chown /?).

When i list, it shows me as the owner:
```
total 20
drwxr-xr-x  5 root  root  4096 2007-10-15 16:17 .
drwxr-xr-x 21 root  root  4096 2007-10-23 21:06 ..
lrwxrwxrwx  1 root  root     6 2007-10-23 01:26 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2007-10-23 01:26 cdrom0
drwxr-xr-x  4 vince vince 4096 2007-10-24 19:14 sdb1
drwxr-xr-x  4 vince vince 4096 2007-10-24 19:15 sdc6

```

However in Gnome, the CREATE FOLDER command is still greyed out... and the folder i created via command line will not let me move it to trash (also greyed out).

Some additional stupid questions:

For media/drives/directories- do you have to specify permissions/ownership individually all the time- or is there an equivalent to "everyone?"

I eventually want to set up this machine to serve media files (CD rips and DVD rips) to media machines in my apt.  Is there a specific type of server that would be the best way to serve this material (with primarily windows clients)?  I see NFS is widly discussed, but didn't know if there was some advanatge over just a samba share in terms of performance or anything else I would need be concerned with.

---

### Post by taurus on 2007-10-24
If you have nautilus open, close it and then open it again.  Otherwise, what is the error message of the second command when you run these from a terminal?

```
cd /media/sdb1
touch testfile
ls -la
```

---

### Post by maskeeper on 2007-10-25
Yep, refreshing the explorer fixed that...

Thanks!!

---

