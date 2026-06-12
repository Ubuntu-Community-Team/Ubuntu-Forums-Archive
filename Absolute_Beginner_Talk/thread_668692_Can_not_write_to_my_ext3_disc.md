---
title: "Can not write to my ext3 disc"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2008-01-15
Hi, I have a Western Digital MyBook and I just converted it from fat32 to ext3 with the partition editor. I wanted to be able to save all of my multimedia on it and put a shortcut to those folders on the drive onto the desktop. I noticed that there was a "lost+and found" folder on the drive after the formating and that I did not have the permissions to view it. I also can not add folders or files to the drive even though I clicked properties and saw that the root has the ability to create and delete files.

Any clue how to fix this? Thanks.

---

### Post by bodhi.zazen on 2008-01-15
```
sudo chown root.users /mount/point
sudo chmod 770 /mount/point
```

Where /mount/point is where you mounted the disk

---

### Post by amtnbiker16 on 2008-01-15
did you try running the sudo command to view the drive?

---

### Post by kevindubrow on 2008-01-15
After I ran the codes I get an error that says I do not have the permissions to view the drive when I open the drive, I can no longer see the "lost+found" folder.

How exactly would I use the sudo command to view the disk? sudo cd: media/disk? 

Also, when I go to properties it says:

Contents: unreadable

Thanks for the help.

---

### Post by bodhi.zazen on 2008-01-15
can you giev us the output of :

```
ls -l /media
```

and 

```
groups
```

---

### Post by kevindubrow on 2008-01-15
ls -l /media
total 8
lrwxrwxrwx 1 root root     6 2007-11-24 14:55 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-11-24 14:55 cdrom0
drwxrwx--- 3 root users 4096 2008-01-15 17:03 disk

~$ groups
stephen adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev

---

### Post by bodhi.zazen on 2008-01-15
Ah ...

You can either add yourself to the users group or :

```
sudo chown root.stephen /media/disk
```

---

### Post by kevindubrow on 2008-01-15
What is the users group?

---

### Post by bodhi.zazen on 2008-01-15
It is a generic group that most users are added to. Can be used for sharing data.

---

### Post by kevindubrow on 2008-01-15
Thats weird, why wouldn't I be in it seeing as that I am the only user? How do I join it? Thanks so much.

---

### Post by kevindubrow on 2008-01-15
Also, I see that after I use that code I still have to use it again each time I plug in the drive, is there a way to make it so that I don't have to use the code? Also, this "lost+found" folder still can not be accessed.

---

### Post by bodhi.zazen on 2008-01-15
"lost + found" is a system file and you do not need access to it.

If you do not want to always manually mount the device, add an entry to fstab

```
gksu gedit /etc/fstab
```

Add a line like

/dev/sdb1 /media/disk auto defaults 0 2

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

