---
title: "Formatting 2nd internal NTFS hard drive."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-04-24
In gparted it looks like this [locked]

[img]http://img455.imageshack.us/img455/2320/screenshotyi0.png[/img]

---

### Post by LaRoza on 2007-04-24
In the upper right there is a selector for the devices. Select what you want to format and it will give  you a similar screen for that drive.

---

### Post by sailor2001 on 2007-04-24
looks like you have scant little drive left to format...unless you don't want windows anymore

---

### Post by psusi on 2007-04-24
The partition is mounted, so you can't manipulate it.  I am confused though, why you are asking about formatting it, when it is already formatted and mounted.

---

### Post by FiggyG on 2007-04-24
Looks like the partition is mounted. Do a ```
sudo umount /media/disk
``` then relaunch gparted.

---

### Post by auraithx on 2007-04-24
Oh sorry, didn't realize it had to be unmounted for me to format it. Cheers!

---

### Post by auraithx on 2007-04-24
I've mounted the formatted drive successfully to /media/backup but it appears as a folder, not a drive?

Also, It won't let me write to it

---

### Post by psusi on 2007-04-24
You need to use the uid= mount option to specify a user ( other than root ) that the files on the volume will be owned by.  You probably want to specify your own user name.

---

### Post by FiggyG on 2007-04-24
Ahh, that becomes the fun part. You'll need the ntfs 3g stuff. It's easy to get.
```
sudo apt-get install ntfs-3g ntfs-config
```
After you get that installed... well, this guide will help with the pics.

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Assuming everything goes well, you now have your mount point, and a writable NTFS partition... for a root user. Fix that by opening your fstab
```
sudo gedit /etc/fstab
```
Mine looks like ```
/dev/sdb1 /media/windows ntfs-3g _**user**_,locale=en_US.UTF-8 0 0
```
Set to to user, use the umount command I posted earlier, remount with ```
sudo mount -a
``` And everything should be working. If you have any issues with mount points, PM me or reply to this thread, I'll be on here as much as possible.

---

### Post by auraithx on 2007-04-24
^ I formatted it as an ext3 drive though? :confused:

it looks like this right now

```
/dev/sdb1       /media/Backup     ext3    defaults        0       2
```

---

### Post by FiggyG on 2007-04-24
Ahh, I see, thought you were sticking with NTFS :lol:

As for that, I'll have to do research to get that working right. You could swap "default" for "user" however, that would allow anyone with user access... (say you setup SSH for me) to get into the drive and have full permissions. I doesn't sit too tight with that from a security stand point.

---

### Post by auraithx on 2007-04-25
Shouldn't using a second internal ex3 hard disk be pretty standard stuff? I thought it was the *preferred* file system type? :confused:

---

### Post by psusi on 2007-04-25
The user mount option just allows users to mount it when it isn't already mounted.  It has nothing to do with the permissions once it is mounted.

---

