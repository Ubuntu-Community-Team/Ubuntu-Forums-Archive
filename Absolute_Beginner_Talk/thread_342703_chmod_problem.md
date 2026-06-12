---
title: "chmod problem"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by reza81 on 2007-01-20
hello,

I have an extra USB HD (NTFS) and even when I am logged in as root, I can't change the permitions  of this filesystem of mine 

```

root@reza-desktop:/media# ls -l
total 68
lrwxrwxrwx 1 root root     6 2007-01-09 11:37 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2007-01-09 11:37 cdrom0
lrwxrwxrwx 1 root root     7 2007-01-09 11:37 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2007-01-09 11:37 floppy0
dr-x------ 1 reza reza 61440 2006-12-14 17:12 FoShizzL
root@reza-desktop:/media# chmod 777 FoShizzL/
chmod: changing permissions of `FoShizzL/': Read-only file system

```

can anyone help me with my n00bish problem please???

---

### Post by ragnar_123 on 2007-01-20
Ubuntu can't write to ntfs, without some sort of extra driver. More info search the howto section

---

### Post by taurus on 2007-01-20
You cannot change permissions for ntfs or fat32.  And besides, ntfs is read-only in Linux unless you install ntfs-3g.  Then, you can write to it.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by reza81 on 2007-01-20
I can't delete my 100 GB + music collection, so that I then can formate my drive 

isn't there any outer way ?

---

### Post by taurus on 2007-01-20
Install ntfs-3g from the link that I included above.  Then, you can delete whatever you want on your ntfs drive.

---

### Post by reza81 on 2007-01-20
> **taurus said:**
> Install ntfs-3g from the link that I included above.  Then, you can delete whatever you want on your ntfs drive.

the thing is; I really don't want to loose my music collection on that drive.So I hope I don't loose any data by installing ntfs-3g

PS. thanks for the tip

---

### Post by taurus on 2007-01-20
So your internal harddrive is not big enough for you to just copy all those mp3 files from the USB over!  Then, you can format that USB drive to ext3.

---

### Post by reza81 on 2007-01-20
> **taurus said:**
> So your internal harddrive is not big enough for you to just copy all those mp3 files from the USB over!  Then, you can format that USB drive to ext3.

if my internal HD whas big enough you wouldnt see this post :lolflag:

---

### Post by taurus on 2007-01-20
So you have two options:

1.  Install ntfs-3g so you can write (and delete) to your USB drive.

2.  Connect your USBdrive to a XP machine and delete whatever you want to delete.

---

### Post by reza81 on 2007-01-20
thanks a lot

---

