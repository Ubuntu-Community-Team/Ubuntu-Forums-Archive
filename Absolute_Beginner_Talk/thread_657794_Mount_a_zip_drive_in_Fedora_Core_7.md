---
title: "Mount a zip drive in Fedora Core 7"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by roselena on 2008-01-03
I am basically new to unix, and I need to mount a zip drive in a computer that has Fedora Core 7; I looked at some of the posts and it suggested to mount it in /dev/hdb4.  Well, I don't have any hdb devices on the computer.  I have sdb devices.  I don't know if I can use one of those or if I should look for another type of device, and if so which device.  Also, how do I know that the device is available (empty?)for doing this? I know that some of the sdb devices are in use because I used df. Could I assume that if they don't show up when I use df, they are available? I just don't want to guess and then damage the system, as I said  I am new in the unix environment.  If someone can help me with this , it would be great thanks.

R.

---

### Post by bodhi.zazen on 2008-01-04
Yea, it is a bit unusual ....

List your devices with :

/sbin/fdisk -l

Your zip device will have the number 4 in it , /dev/sdb4 perhaps.

1. make a mount point.

```
su -
# enter root password
mkdir /media/zip
```

2. Mount (still as root)

```
mount /dev/sdb4 /media/zip
```

Options re r/w depend on the filesystem on the zip ...

---

### Post by Rocket2DMn on 2008-01-04
edit: Nevermind, b.z has you covered!

---

### Post by roselena on 2008-01-04
Thanks for your answer.  I listed the devises with the command you told me and this was what I got

 /sbin/fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+  83  Linux
/dev/sda2            6375        6629     2048287+  82  Linux swap / Solaris
/dev/sda3            6630       19457   103040910   83  Linux

I am attaching the list of the devices I have in /dev  I checked this with ls.



as you can see I in the list I have some sdb and some sda devices, but none with the number 4.  

I checked also with df to see which are in use and the following list is the one that shows up
/dev/sda1             
/dev/sda3            
/dev/sdb1            
tmpfs     

Do I need to create a device called sdb4 and if so how do I do that? and if not what should I do to mount the zip drive?  Thanks so much for your help.

R.    :confused:

---

### Post by PinkFloyd102489 on 2008-01-04
Quick hijack. I have a zip drive in my Ubuntu server. Anyway I can get it working like this?

---

### Post by bodhi.zazen on 2008-01-04
@roselena : I do not see your zip drive listed.

Just to be sure, plug the drive in (check the cables), power it up, and put a disk in the device.

Here is what my zip drive looks like (fdisk -l)

> Disk /dev/sde: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0e78014e

   Device Boot      Start         End      Blocks   Id  System
/dev/**sde4**   *           1          96       98288    6  FAT16

Note : /dev/sde4

Your /dev/sdb looks like a CDROM

==========

@PinkFloyd102489 ~ Yea, should work just the same. In Ubuntu use sudo (of course)

```
sudo fdisk -l
```

and on ...

---

### Post by roselena on 2008-01-05
Thank you so much for your help.  Of course I had forgotten to put the disk on the zip drive before looking for the device.  I put the disk, and then I saw the device listed.  My device is sdc4, and sdc1 depending on the disk I use (250 MB and 100 MB respectively).  I have a 250 internal zip drive on the computer.  I have one more question though, do I have to mount the zip drive every time I will use it?  After I ejected the disk, I put it again, and tried to read it but it didn't worked until I used the mount command again.  Is this the way it works?  I don't have any problem using it that way, but I just want to know.  Again thanks so much for your help, I will save a lot of time just by having the zip drive on this computer.

R.  :) :) :) :) :) :) :)

---

### Post by roselena on 2008-01-05
Never mind my question about ejecting the disk and mounting every time.   

R.

---

