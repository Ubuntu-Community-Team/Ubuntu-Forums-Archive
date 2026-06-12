---
title: "filesystem on usb pendrive"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2007-02-27
Hi,
I successfully created a bootable pendrive by following the steps mentioned here:
[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/]("http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/")
I was also able to boot from it and could see the entire directory structure as it would appear on harddisk( / /home /media /etc /tmp etc..).  But when I boot from the harddisk and mount the pendrive, I cannot see those directories on the pendrive.

Is there anyway I see those folders?  I want to copy a file from my harddisk to /home folder on the pendrive.

Thanks.

---

### Post by annda on 2007-02-27
how did you mount the pendrive? any special options?

---

### Post by bernied on 2007-02-27
If you have followed those instructions you will have two partitions on the pendrive - one will be a FAT filesystem, and the other will be ext2. So look for them...
To see what devices are already mounted on your root filesystem (do this after booting from the hard-drive)
```
df -hT
```df is display filesystems, the -h option means (human-readable), the -T option gives you the filesystem type. On the right hand side is the place in your root filesystem where the files are mounted. Can you find one of the two partitions? Can you find both?

If one is missing, you can mount it. For this, you need: 
1 - a mount point - this is an empty folder on your filesystem where the files will appear. Use the mkdir command to make an empty folder
2 - to know the filesystem type (either vfat or ext2 in your case)
3 - to know the location of the device (this will be something like sdb1, or sdb2 or sda1 or sdf1), if you have found one of the devices, then the other will be a very similar name
Then, to mount:
```
mount -t <type> <location> <mountpoint>
```
replace anything like <this> with the information in 2, 3 and 1

Depending on where you try to make  the mountpoint, and how you have permissions set on your devices, you may need to use sudo for one or more of those commands.

Does this help?

---

### Post by vijayanand_sodadasi on 2007-02-27
Thanks for your replies.
Yes, as you said, I have two partitions on the pendrive one with FAT(/dev/sda1) and other with ext2(/dev/sda2).
I mounted the FAT filesystem which is on usb pendrive using the command:
```
sudo mount /dev/sda1 /media/edgy -t ntfs -o nls=utf8,umask=0222
```
But I was unable to mount the ext2 filesystem. I tried the command
```
sudo mount /dev/sda2 /media/usbdisk-1 -t ext2 -o default
```

When I booted from the pendrive, everything is fine (I mean the filesystem with the directory structure / , /home /etc /tmp /media etc... are visible).  But when I boot from the harddisk (which is also Ubuntu Edgy) and insert pendrive, it shows folders such as casper, pool, disctree etc... on the pendrive but not the other folders like  /home. I tried to look for folders /home/user /tmp etc on the pendrive to copy a file which was on hard disk onto the pendrive.  I could have copied the file to one of the folders which are visible, but I wonder whether they will be visible if I boot with the pendrive next time.

I will try this again and see if I can access those.

---

### Post by bernied on 2007-02-27
It sounds like there is something a bit clever about that install - it is possibly keeping all those files and folders in a compressed form, or else a little bit hidden somewhere in that file structure. 
The answer will be somewhere in the magic of google

---

### Post by vijayanand_sodadasi on 2007-02-27
> **bernied said:**
> It sounds like there is something a bit clever about that install - it is possibly keeping all those files and folders in a compressed form, or else a little bit hidden somewhere in that file structure. 
The answer will be somewhere in the magic of google

I think its true, because there is a 700 MB file called filesystem."something" (I dont remember exactly) in one of the folders.  I guess that must be the file system.

Btw, 
Thanks for your replies.

---

### Post by bernied on 2007-02-28
You could try the 'df -hT' command when booted from the pendrive - it may tell you the filesystem type of the root directory. Then, when booted to the hard-drive, you could mount that file as a loop device with that filesystem, the same way as you can mount a cd-image file. In fact, it looks like you don't need to know the filesystem in order to mount it. Something like this:
```
mount -o loop <filename> <mountpoint>
```Any luck?

You would need to have support for that filesystem built into your kernel, or available as a module, but it may already be there. If it's not, it's probably only an 'apt-get' away.

The filesystem might be unionfs - this is what slax (one of the usb distros that is listed with the ubuntu one, [here](http://pendrivelinux.com/)) uses.

---

