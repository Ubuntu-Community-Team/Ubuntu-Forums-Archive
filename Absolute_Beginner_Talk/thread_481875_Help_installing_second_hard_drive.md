---
title: "Help installing second hard drive"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Ryan8720 on 2007-06-23
I searched, but I couldn't find anything that worked.

I have a desktop with a 40GB hard drive with a clean install of Fiesty (no other OS).  I just added a 500GB hard drive that i plan to network and store media on.

I used gparted to format the disk with FAT32. But I can't get it to mount.

Here are some output that other treads asked for.

Output of [FONT="Courier New"]**sudo fdisk -l**[/FONT]
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4775    38355156   83  Linux
/dev/sda2            4776        4865      722925    5  Extended
/dev/sda5            4776        4865      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32
```

Output of [FONT="Courier New"]**cat /etc/fstab**[/FONT]
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=99382ed0-7406-4a21-8612-ba25c58091ab /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f4561d36-7b9f-41ed-81b3-82297e51b41d none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by Inxsible on 2007-06-23
Since its an external drive you should use pmount to mount it. I am not sure if pmount is installed by default.. If not, you can install it like so

```
sudo aptitude install pmount
``` Once you install it you can use it to mount your drive

```
sudo pmount /dev/sdX* Mount_Point
```
where X = a, b, c etc * is the partition number that you are trying to mount. Mount_Point is the name of the folder you want to mount on. It couls be anything like Seagate, WD500 or mydrive. This will create a folder under /media. Make sure you do not already have a folder by that name under /media since pmount creates one for you.

Since you want to mount the GB drive which is listed as sdb1 for you:
```
sudo pmount /dev/sdb1 My500GBDrive
```

---

### Post by confused57 on 2007-06-23
This guide should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Inxsible on 2007-06-23
> **confused57 said:**
> This guide should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Using mount works too, but having an automount entry in fstab leads to a problem wherein, if the external drive is not connected during bootup, it gives you a bunch of errors.

pmount keeps your external drives away from fstab and mounts them the moment you connect them which is what you want with externals.

---

### Post by confused57 on 2007-06-23
> **Inxsible said:**
> Using mount works too, but having an automount entry in fstab leads to a problem wherein, if the external drive is not connected during bootup, it gives you a bunch of errors.

pmount keeps your external drives away from fstab and mounts them the moment you connect them which is what you want with externals.

I didn't notice that it was an external hard drive, which should automount anyway when it's plugged in.

---

### Post by Inxsible on 2007-06-23
> **confused57 said:**
> I didn't notice that it was an external hard drive, which should automount anyway when it's plugged in.

Whoops !! You are right ! 

The OP doesnt mention whether its an external drive or not. I just assumed it was since I have a 500 GB external. :rolleyes:


My bad !!!#-o

---

### Post by confused57 on 2007-06-23
> **Inxsible said:**
> Whoops !! You are right ! 

The OP doesnt mention whether its an external drive or not. I just assumed it was since I have a 500 GB external. :rolleyes:


My bad !!!#-o

Who knows, it might very well be an external drive...at least the OP has instructions or a link, whether it's internal or external.   I learned something myself for mounting an external drive.

---

### Post by Ryan8720 on 2007-06-23
I'm sorry if I wasn't clear.  The 500 GB is an internal drive.  I have another 80GB drive that is external and I sometimes connect to the Ubuntu computer.

---

### Post by confused57 on 2007-06-23
> **Ryan8720 said:**
> I'm sorry if I wasn't clear.  The 500 GB is an internal drive.  I have another 80GB drive that is external and I sometimes connect to the Ubuntu computer.
Your initial post was quite clear, we just didn't want to make any "read between the lines" assumptions...the link I gave you in my first reply should be what you want.

Here's another filesystem mounting link:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Ryan8720 on 2007-06-23
I mounted it to /media/storage.  However, it doesn't show up on the desktop like the external drive does when it's mounted.  I also want it to be permanately mounted, so that it doesn't unmount after a reboot.

The first guide says I need to edit the fstab, but it shows how to do it for versions before Edgy.  I'm not sure what I need to use for the UUID.

---

### Post by confused57 on 2007-06-23
> **Ryan8720 said:**
> I mounted it to /media/storage.  However, it doesn't show up on the desktop like the external drive does when it's mounted.  I also want it to be permanately mounted, so that it doesn't unmount after a reboot.

The first guide says I need to edit the fstab, but it shows how to do it for versions before Edgy.  I'm not sure what I need to use for the UUID.
See the link I gave you in my last reply for setting up fstab with UUID...you can open a terminal & run:
```
blkid
```
this will give you the UUID's for your partition filesystems.

---

### Post by Inxsible on 2007-06-23
In Fesity you can use the UUIDs or the LABELs or the device name itself in the fstab. Personally I feel device name is the best since its human readable and you know what device you are dealing with.

---

### Post by Ryan8720 on 2007-06-23
The UUID didn't show when I did [FONT="Courier New"]**blkid**[/FONT].

I'm not sure what the label is either.

This is what i put in fstab.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=99382ed0-7406-4a21-8612-ba25c58091ab /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f4561d36-7b9f-41ed-81b3-82297e51b41d none            swap    sw              0       0
# /dev/sdb1
UUID=storage /media/storage vfat iocharset=utf8,umask=000 0 0/
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Here is [FONT="Courier New"]**sudo fdisk -l**[/FONT]

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4775    38355156   83  Linux
/dev/sda2            4776        4865      722925    5  Extended
/dev/sda5            4776        4865      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32
```

And

---

### Post by Ryan8720 on 2007-06-23
After I added "# /dev/sdb1
UUID=storage /media/storage vfat iocharset=utf8,umask=000 0 0/" and then did blkid again, it showed a UUID.  Then I switched the UUID numbers for the storage, restarted, and it mounted.

Thanks for all the help.

---

### Post by Inxsible on 2007-06-23
> **Ryan8720 said:**
> After I added "# /dev/sdb1
UUID=storage /media/storage vfat iocharset=utf8,umask=000 0 0/" and then did blkid again, it showed a UUID.  Then I switched the UUID numbers for the storage, restarted, and it mounted.

Thanks for all the help.

I hope you no longer have UUID=storage now. UUIDs are some long alphanumeric number. Alternatively, you can use the device name directly.

```
/dev/sdb1 /media/storage  vfat iocharset=utf8,umask=000 0 0
```

---

### Post by Ryan8720 on 2007-06-23
After I put in the UUID=storage, then blkid showed a UUID. Now I have:
```
# /dev/sdb1
UUID=467C-A181    /media/storage  vfat iocharset=utf8,umask=000 0 0
```

---

### Post by szac9 on 2008-07-20
Hello,
I recently updated my ubuntu and now it cannot even detect my external hard drive. Nothing comes up when I sudo fdisk -l except for the laptop's hard drive. Before the upgrade it was sdb1. Does anyone have any suggestions?

---

