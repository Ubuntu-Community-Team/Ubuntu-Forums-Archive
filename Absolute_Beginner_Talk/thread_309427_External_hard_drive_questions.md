---
title: "External hard drive questions"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by bguy on 2006-11-29
Hi,
I have an external usb hard drive formatted using the ntfs file system that contains data accumulated when i was an xp user. Now that i'm using 6.1 full-time i would like to erase all the data there and then switch to a ubuntu friendly format that allows me to read and write. 

I have 3 questions relating to this.

1.The external hard drive is read only in 6.1 so do i have to reinstall xp in order to erase and format the hard drive?
2.What file system would allow me to read and write?
3.Using 6.1, how do i change to this file system?

Lot's of questions i know but this is really the last step i need to take in my conversion from windows to Ubuntu.
I would appreciate any help,
Thanks a  lot,
Take care,
B

---

### Post by taurus on 2006-11-29
You can format your USB harddrive to ext3 with the "mke2fs -j" command!  Assuming it is /dev/sda1, then you would run something like this from a terminal.

```
sudo mke2fs -j /dev/sda1
```
Then, edit /etc/fstab and add an entry for it so it would be mounted automatically each time you boot Ubuntu...

---

### Post by nandasunu on 2006-11-29
You should be able to format the drive with gParted or any partion tool. Make sure you have the drive powered on and plugged in when you run the program. Select your usb drive and choose to format in either ext3 or fat32. Both formats will allow read/write with ubuntu, but fat32 will also work with windows/mac etc. but ext3 won't (unless you install a special windows driver on any windows machine you may use).

I have heard that you may experience problems with very large files and fat32 (4gb+), but I haven't personally had this problem. I have a 250gb usb drive which is 70% full, formatted to fat32 and works fine in linux & windows.

So, if you don't need to access anything apart from ubuntu/linux, go with ext3, otherwise fat32 is what you need.


> **bguy said:**
> Hi,
I have an external usb hard drive formatted using the ntfs file system that contains data accumulated when i was an xp user. Now that i'm using 6.1 full-time i would like to erase all the data there and then switch to a ubuntu friendly format that allows me to read and write. 

I have 3 questions relating to this.

1.The external hard drive is read only in 6.1 so do i have to reinstall xp in order to erase and format the hard drive?
2.What file system would allow me to read and write?
3.Using 6.1, how do i change to this file system?

Lot's of questions i know but this is really the last step i need to take in my conversion from windows to Ubuntu.
I would appreciate any help,
Thanks a  lot,
Take care,
B

---

### Post by zekopeko on 2006-11-29
or you could download gparted liveCD , burn it and boot from it.

gparted is the same thing you used during the installation of ubuntu from the liveCD to format and partition your drive.

you can get it here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

a good file system is ext3 used as a default in ubuntu

P.S. 

the liveCD is a newer version then the one in the repos. in the repos is 2.5 and the liveCD is something like 3.1+

---

### Post by styven on 2006-11-29
Hi there,

In response to your questions........

1. I think you should get access to a windows pc and save all your data to that pc. Go back onto a linux pc and use "gparted" (you may have to install this first) to format the drive to fat32. Then you can copy your data back to the hdd, with read and wrtite capability.

2. Fat32, then you can read/write on both windows and linux pc.

3. As mentioned above you need to use gparted, if you do not have it installed, then get back to us and we can talk you through (if you need us to:) )

Steve.

---

### Post by bguy on 2006-11-29
Thanks everyone
How do i find out what location its at? ie. /dev/sda1

---

### Post by Xappe on 2006-11-29
> **bguy said:**
> Thanks everyone
How do i find out what location its at? ie. /dev/sda1

```
fdisk -l
```

perhaps?

---

### Post by taurus on 2006-11-29
```
sudo fdisk -l
```

---

### Post by bguy on 2006-11-29
thanks,
this is what came up after i hit fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS


so i would type sudo mke2fs -j /dev/sda1 to format my drive in ext3?

The only thing that i'm a little unsure of is this last part now.

"Then, edit /etc/fstab and add an entry for it so it would be mounted automatically each time you boot Ubuntu.."

I just went to filesystem/etc but there isn't an fstab file.  Can you tell me where i can find it and can you also tell me exactly what i need to  type to add the entry?

Thanks again,
B

---

### Post by bguy on 2006-11-29
oops i just looked again and found the fstab file.  I hadn't scrolled down far enough. I'm still stuck on what to add and where though.
thanks

---

### Post by bguy on 2006-11-29
this is what's contained in the fstab file presently


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1379f249-85be-4908-8a38-df5dfd4718f1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d60d83ef-6a53-406e-a66d-621c754964a7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2006-11-29
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Then add this line to the end of it.

```
/dev/sda1   /media/share   ext3   defaults   0   1
```
Now, create a mount point and mount it.

```
sudo mkdir /media/share
sudo mount -a
df -h
```

---

### Post by bguy on 2006-11-29
Perfect, thanks a lot!

:D

---

### Post by taurus on 2006-11-29
So everything is all good now, eh!

---

### Post by zekopeko on 2006-11-29
well now i have a question.

we are talking about an external drive hear.

so isn't editing fstab only for internal drives?
what is the drive isn't connected? 

won't there be errors when trying to mount a drive that isn't there?

aslo if i'm wrong on the above is it possible to mount external drives in a specific folder every time?

---

### Post by bguy on 2006-11-29
It's all good Taurus.
Thanks again!
:-D

---

### Post by nandasunu on 2006-11-30
> **zekopeko said:**
> well now i have a question.

we are talking about an external drive hear.

so isn't editing fstab only for internal drives?
what is the drive isn't connected? 

won't there be errors when trying to mount a drive that isn't there?

aslo if i'm wrong on the above is it possible to mount external drives in a specific folder every time?

yeah, it shouldn't actually be necessary to edit the fstab settings for a plug and play usb drive. I never did this for mine and ubuntu mounts it fine when ever I plug it in.

---

