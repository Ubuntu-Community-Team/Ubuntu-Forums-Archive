---
title: "Trouble Mounting External Harddrive"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by BuffaloBeagle on 2007-08-10
I know there are a lot of threads about this already but none seem to have the issue that I am having.  Basically, I have a 250GB external Hard Drive from Western Digital,  it is formatted in NTFS,  I am running Xubuntu, I have NTFS-3G installed, when I plug it in and turn it on nothing happens, nothing shows up nothing changes.  So obviously auto mount does not seem to notice it.  My attempts at mounting it manually have been futile.  I have very important information on that drive and Linux is the only OS that will read it now since I accidentally had it plugged in when i booted Ubuntu one time, so now Windows thinks it is corrupted.

Is there anyway to get into the drive in Xubuntu or is there a program that can just pull all the files off of the drive and recompile them somewhere else?  There is about 90 Gigs of stuff on the drive right now about 75 of which I need.  Please someone help me out here.  This forum has been extremely helpful so far and I hope that you guys can help me out with this problem.

Thank you,
BuffaloBeagle

---

### Post by overdrank on 2007-08-11
> **BuffaloBeagle said:**
> I know there are a lot of threads about this already but none seem to have the issue that I am having.  Basically, I have a 250GB external Hard Drive from Western Digital,  it is formatted in NTFS,  I am running Xubuntu, I have NTFS-3G installed, when I plug it in and turn it on nothing happens, nothing shows up nothing changes.  So obviously auto mount does not seem to notice it.  My attempts at mounting it manually have been futile.  I have very important information on that drive and Linux is the only OS that will read it now since I accidentally had it plugged in when i booted Ubuntu one time, so now Windows thinks it is corrupted.

Is there anyway to get into the drive in Xubuntu or is there a program that can just pull all the files off of the drive and recompile them somewhere else?  There is about 90 Gigs of stuff on the drive right now about 75 of which I need.  Please someone help me out here.  This forum has been extremely helpful so far and I hope that you guys can help me out with this problem.

Thank you,
BuffaloBeagle


Hi I just check to make sure mine mounted in xfce and it did but it is Fat 32. So does it show in your fstab? You can verify with the command in the terminal
```
sudo fdisk -l
```

If you have tried that and do then maybe you can post some of your errors that you get while trying to mount the drive,

---

### Post by ravenwere on 2007-08-11
Assuming you have a usb external hdd similar to my iomega 320MB:

In the console:
lsusb
(see whether the usb device is listed)

fdisk -l
(see whether the partition is seen. Mine appears as /dev/sda1, yours may be some other. Leaving the sudo off the beginning means it only lists the plugin device not all the hdd)

sudo mkdir /mnt/usbhdd
(to create the directory you will mount to. You can choose a different directory.)

sudo mount -t ntfs-3g /dev/sda1 /mnt/usbhdd
(this is where I mount the device to. You can choose a different mount point. eg. /home/username/usbhdd. Just make sure the directory(folder) exists and as you mount it as root you will also have to give your username permissions to read/write. I get around this by adding a line to my /etc/fstab config file.)

UUID=05F4DDFB6E870581 /mnt/usbhdd ntfs-3g users,atime,noauto,rw,dev,exec,suid 0 0

then i just use the console command sudo mount /dev/sda1 and it mounts the drive according to the fstab entry above.

I use kubuntu but I can't see why this shouldn't work in xubuntu. More experienced users could correct me.

Hope this helps
r

---

### Post by BuffaloBeagle on 2007-08-11
Thank you so far.  My drive shows up in both of those commands, in the first as western digital external hard drive,  and in the second as dev/sda1 but when I tried to mount it a few times i kept getting some errors.  This is the code for the few times I tried to mount it,  I tried a few different things but only the last one in the list had different results.

```

god@Xubuntu-Box:~$ sudo mount /dev/sda1 /mnt/usbhdd
Password:
mount: mount point /mnt/usbhdd does not exist
god@Xubuntu-Box:~$ 
god@Xubuntu-Box:~$ sudo mount /dev/sda1 /usb
mount: mount point /usb does not exist
god@Xubuntu-Box:~$ sudo mount /dev/sda1 /mnt/usbhdd
mount: mount point /mnt/usbhdd does not exist
god@Xubuntu-Box:~$ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type

```

Also this happens

```

god@Xubuntu-Box:~$ sudo mount /dev/sda1 /mnt-NTFS
mount: mount point /mnt-NTFS does not exist

```

I'm not sure if that is how you specify the filesystem or not but its what i tried and i got a different result so idk what to do at all now.

What should I do from here?

---

### Post by ravenwere on 2007-08-11
The error message seems to indicate that the directory /mnt/usbhdd does not exist.
Create the directory before mounting the media - you only have to do that once.


```
sudo mkdir /mnt/usbhdd
```

---

### Post by ravenwere on 2007-08-11
Once you've created the directory that you want to mount your hdd to you can then use the mount command to mount that drive.

```
sudo mount -t ntfs-3g /dev/sda1 /mnt/usbhdd
```

At this stage though you only have read permissions.

---

### Post by BuffaloBeagle on 2007-08-11
It still says that I need to specify a file system type

```

god@Xubuntu-Box:~$ sudo mkdir /mnt/usbhdd
Password:
god@Xubuntu-Box:~$ sudo mount /dev/sda1 /mnt/usbhdd
mount: you must specify the filesystem type

```

---

### Post by ravenwere on 2007-08-11
Once we have mounted the usb hdd then to simplify the process and create read/write privileges for that drive we have to edit the /etc/fstab file.

First back up the file - just to be on the safe side.

```
sudo cp /etc/fstab /etc/fstab.bak
```


Below is a copy of my fstab file (for comparison only):

> # /etc/fstab: static file system information.
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=9d3d6bf0-ef08-4a14-8c14-a4d73c4274e9 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/hda5 :
UUID=92fc12e9-9bc1-4233-9f53-4eb81f553f97 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
# Entry for /dev/sda1:
UUID=05F4DDFB6E870581 /mnt/usbhdd ntfs-3g users,atime,noauto,rw,dev,exec,suid 0 0

You will notice the last two lines these will be the lines we need to add to your /etc/fstab.

To edit this file (once you have created a backup copy):

```
sudo nano /etc/fstab
```

Then copy in the following lines:
#Entry for /dev/sda1 USB HDD
/dev/sda1 /mnt/usbhdd ntfs-3g users,atime,noauto,rw,dev,exec,suid 0 0

This tells mount how you want this drive mounted manually and it has ntfs-3g file system read write execute access and the created folders are to have the same permissions as the parent folders.

You will notice that my fstab uses the unique device ID rather than the generic /dev/sda1. This is so if you are mounting differing usb devices there is no confusion over where they are mounted.

Once you have saved your changes to the fstab file you can then mount your usbhdd using the shortened command:
```
sudo mount /dev/sda1
```

---

### Post by ravenwere on 2007-08-11
Just goes to show you gotta check everything:

With regard to post #7:

```
sudo mount -t ntfs-3g /dev/sda1 /mnt/usbhdd
```

is the correction.

Apologies

---

### Post by ravenwere on 2007-08-11
For further information and fine tuning always check the:

mount --help,  or

man mount

Using ??? --help or man ??? gives information and syntax about all commands under linux/unix.

Well this is as far as I can take you - We need more experienced users from here on if you have further troubles.

Why mount the disk manually? Because in my experience Linux still has troubles automounting an NTFS file system and although ext 3 is a better file system some of us still have to plug these hdd's into windows PC's.

And importantly to protect data, as we manually mounted the drive we should manually unmount it with the following:

```
sudo umount /dev/sda1
```

All the best,
r

---

### Post by BuffaloBeagle on 2007-08-11
Ok now i am really confused, I'm getting this error

```

god@Xubuntu-Box:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt/usbhdd
Password:
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

Please dont tell me that the drive is corrupted i have a lot of info on there that i need, some of the files i do have a second backup of but that drive is the backup of other very important files which i have recently lost.

---

### Post by BuffaloBeagle on 2007-08-11
are there any programs that i can download that just pulls files from a disk weather it is corrupted or not and like tries to pull as many uncorrupted files as possible?

---

### Post by ravenwere on 2007-08-12
Hi B,


> NTFS signature is missing.


The news is not good. The disk isn't corrupted but the partition signature file is.

Read this post:
[http://forum.linux-ntfs.org/viewtopic.php?p=2304&sid=a47ef6e7143dd6be4335f52863d5ccec](http://forum.linux-ntfs.org/viewtopic.php?p=2304&sid=a47ef6e7143dd6be4335f52863d5ccec)

I don't have the time to research this error message now but will stick with you on this. It seems that the way to solve this is to recreate the partition on your usb hdd using exactly the same start point as before. The end result of the post above solved the problem but its not an area where I have any experience and rather than risk your data.

Start a new thread using your second last post with the NTFS error message and a new title such as: Need to recreate NTFS partition in order to recover data.

Ask for somebody to step you through the process of determining where the partition started and recreating it.

If your data is important let's take the time to get it right. We will also learn a lot. I will be back in about 6 hours. If you solve the problem in the meantime pls send a private message to let me know how you went and what the solution was. Prob be quite simple in the end.
r

---

### Post by meierfra on 2007-08-12
Are you sure that sda1 is  your external harddrive?  Please  post the output of

```
sudo fdisk -l
```

---

