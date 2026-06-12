---
title: "Help with getting 7.04 to write to my NTFS partition"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Sky Shark on 2007-04-21
Yesterday I installed Ubuntu 7.04 on my Dell laptop and partitioned my hard drive so I had both that and my windows XP on the same internal hard drive.  Now I've been told that Ubuntu 7.04 supports the writing to NTFS along with reading it which it does fine.  However on the Ubuntu IRC chat room they told me to install the NTFS configuration Tool which I did however that only let me enable writing to an external NTFS device.  I was wondering if anyone could tell me how to safely enable writing to my Windows partition so I can edit word docs and other things that are on my widows partition while on Ubuntu.  I would appreciate any help.

---

### Post by eyelessfade on 2007-04-21
ntfs-3g will do this for you.
Just mount up your ntfs partition to an empty directory. And you will be able to access all your files the same way you access linux files.

---

### Post by leibowitz on 2007-04-21
They provided the good way of doing it. But from what I know ntfs-config (the configuration tool) will not show your already mounted partitions.

So you have to umount your NTFS partition(s) you want to read/write to. Then, start the ntfs configuration tool again and set the mount point and all that.

Go the the Applications menu > Accessories > Terminal, and paste thos commands

Step 1: **mount **
This will list all of your mounted partitions. Check something like ntfs in it ( **mount | grep ntfs** could be useful) You need to get the mount point and the device for that partition. The output is formated like this:
```
device on /my/windows/ntfs/partition type ntfs (options,goes,here)
```

Identify the "device" and mount point which is /my/windows/ntfs/partition in this example.

Step 2: **sudo umount /my/windows/ntfs/partition** (Please remove /my/windows/ntfs/partition and replace it with your mount point)
Step 3: **ntfs-config**
This will set the mount point for the "detected" partition.

Please post any issue you face during this process

---

### Post by Sky Shark on 2007-04-21
> **leibowitz said:**
> They provided the good way of doing it. But from what I know ntfs-config (the configuration tool) will not show your already mounted partitions.

So you have to umount your NTFS partition(s) you want to read/write to. Then, start the ntfs configuration tool again and set the mount point and all that.

Go the the Applications menu > Accessories > Terminal, and paste thos commands

Step 1: **mount **
This will list all of your mounted partitions. Check something like ntfs in it ( **mount | grep ntfs** could be useful) You need to get the mount point and the device for that partition. The output is formated like this:
```
device on /my/windows/ntfs/partition type ntfs (options,goes,here)
```

Identify the "device" and mount point which is /my/windows/ntfs/partition in this example.

Step 2: **sudo umount /my/windows/ntfs/partition** (Please remove /my/windows/ntfs/partition and replace it with your mount point)
Step 3: **ntfs-config**
This will set the mount point for the "detected" partition.

Please post any issue you face during this process

A quick question before I do this, I will still be able to boot up to Windows XP after I do this right?  I just want to be sure I have access and can run XP.

---

### Post by leibowitz on 2007-04-21
Sure. This will not affect the boot process in any way. Now it's your choice to activate the read/write on your NTFS partition. Because you will be able to delete files on your NTFS partition, and this is what you need to be cautious for.

---

### Post by Sky Shark on 2007-04-21
okay thanks

---

### Post by Sky Shark on 2007-04-21
I just tried this out and i got this error

```
/dev/sda1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
charles@Sky-Shark:~$ sudo unmount/dev/sda1 on /media/disk type ntfs (rw nosuid, nodev, umask=222, utf8)
bash: syntax error near unexpected token `('
charles@Sky-Shark:~$ sudo unmount/media/disk type ntfs (rw nosuid, nodev, umask=222, utf8)
bash: syntax error near unexpected token `('
charles@Sky-Shark:~$ 

``` 
can you please tell me what I am doing wrong here?  I would appreciate it.

---

### Post by BaffledMollusc on 2007-04-21
> **Sky Shark said:**
> I just tried this out and i got this error

```
/dev/sda1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
charles@Sky-Shark:~$ sudo unmount/dev/sda1 on /media/disk type ntfs (rw nosuid, nodev, umask=222, utf8)
bash: syntax error near unexpected token `('
charles@Sky-Shark:~$ sudo unmount/media/disk type ntfs (rw nosuid, nodev, umask=222, utf8)
bash: syntax error near unexpected token `('
charles@Sky-Shark:~$ 

``` 
can you please tell me what I am doing wrong here?  I would appreciate it.

I presume the command is 
```

sudo umount /dev/sda1

```
Also note there is a space between "umount" and "/dev/sda1"

Edit: it's "umount", not "unmount"!

---

### Post by Sky Shark on 2007-04-21
tried it and it gave me a "sudo: unmount/dev/sda1: command not found" error

---

### Post by leibowitz on 2007-04-21
you need to put a blank character (commonly called space) between umount and /dev/sda1 as BaffledMollusc said.

---

### Post by BaffledMollusc on 2007-04-21
> **Sky Shark said:**
> tried it and it gave me a "sudo: unmount/dev/sda1: command not found" error

It's "umount" not "unmount", and there should be a space between  "umount" and "/dev/sda1"

---

### Post by Sky Shark on 2007-04-21
okay I finally got that done thanks to your help and now I have one last thing what mount point would I put in when I open up NTFS-Config and it asks for a mount point after the device on the add list?

---

### Post by leibowitz on 2007-04-21
That's a name of a directory that will be accessible in /media 

You were using "disk" before, so maybe keeping it would be cool.

---

### Post by Sky Shark on 2007-04-21
Got it working perfectly thanks for all your help guys. =)

---

### Post by leibowitz on 2007-04-21
no prob.

Have a nice Ubuntu experience.

---

### Post by Sky Shark on 2007-04-22
Thank's I'm sure I will, all I have to do now is get WINE up and running so I can run window apps in Ubuntu if I don't feel like rebooting when I want to.

---

