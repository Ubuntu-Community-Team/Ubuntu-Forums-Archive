---
title: "how to format..... and make it work"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-07-11
********hi all
-I have an external hardisk of 116 GB.
Decided to format it with gparted, to ext3.  (done)

-Problem is that it comes up in desktop as usbdisk, and I can not write on to it. 

-Should I write something in access path in disk manager?
(It is blank, I tried just writing /,did not work)

-Is ext3 a good option, ex2 maybe, what is better?, FAT32, but does it work well with such a big (116gb) partition?

-How do I make it appaer as a normal hardisk in desktop?

:-k hope someone can help me on this.
sam

---

### Post by orb9220 on 2006-07-11
I look around but it is prob a permission thing.

Look in System>adminstration>Users and groups>

Fi9nd your account name select and chose properties on the user priviliges
see that the first one is ticked "Enable access to external storage devices.

In fact make sure they are all ticked.

Hope this helps

---

### Post by DerHesse on 2006-07-11
maybe you wish to mount the device somwhere else?

$ sudo gedit /etc/fstab

/dev/sda1     /some_folder_to_mount_to     ext3    defaults        0       2

or what ever device it is. (could be dev/sdb1 as well)

find out with:
$ mount
and look for your device  you could create an empty folder somwhere else, and replace the above "some_folder_to_mount_to" in the fstab file.

I would not use VFAT FAT32 & Co. as I think you cannot format really big partitions.

---

### Post by wannabesurfer on 2006-07-11
so there is no difference between ext3 and ext2 option.

---

### Post by wannabesurfer on 2006-07-11
I checked my permision, and all are ticked and ok.

-doing the mount in terminal I get this:
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda5 on /windows type vfat (rw,utf8,umask=007,gid=46)
[B]/dev/sda1 on /media/usbdisk type ext3 (rw,nosuid,nodev)
/dev/sda1 on /Gadol type ext3 (rw)[/B]

where I made a folder where I put my external hardisk, I did this in the access path.

trying the command bellow I got this:
~$ /dev/sda /some_folder_to_mount_to ext3 defaults 0 2
bash: /dev/sda: Permission denied

so my problem is still not solved, where should I create a folder for it?
What kind of folder? A folder in Desktop, or home..

I am a beginner so it takes me some time on issues that are proably extremely easy to solve......

sam

---

### Post by DerHesse on 2006-07-13
Maybe your problem derives from not having access rights to the mount point, but how did you create the mountpoint (folder)?


Can you access the device with sudo?

~$**sudo cd** /dev/sda /some_folder_to_mount_to

or 

~$**sudo cd** /media/usbdisk

Is your device properly formated?

---

### Post by wannabesurfer on 2006-07-13
I created the folder in disk manager. You have the option to leave it blank in access path, put it in existing folder, or create new. But they all are root folders.
[I]
can you acess the device with sudo?[/I]
$ sudo cd /dev/sda /some_folder_to_mount_to
sudo: cd: command not found

*sudo cd /media/usbdisk*
 sudo cd /media/usbdisk
sudo: cd: command not found

My device is properly formated.

---

### Post by DerHesse on 2006-07-14
sorry ](*,)  try it that way:

$ sudo su
...
$ cd /some_folder_to_mount_to
$ ls -ld

---

