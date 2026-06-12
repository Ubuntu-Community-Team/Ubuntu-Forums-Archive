---
title: "[SOLVED] mount drives to folders"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by bardic on 2007-10-26
Hey,
I actually have  two problems by they are both related to mounted NTFS drives.
The first problem is this: Ubuntu is mounting two of my 3 NTFS drives at startup and won't let me unmount them. It tells me that:

umount: only root can unmount UUID=1AF897DDF897B58B from /media/hda1

And two: I would like to change the point at where they mount. I would like to mount them in my home folder. 

Thanks for the help ^^

---

### Post by taurus on 2007-10-26
1.  To unmount it, just run

```
sudo umount /media/hda1
```

2.  To change the mount point, edit /etc/fstab

```
gksudo gedit /etc/fstab
```

---

### Post by Pumalite on 2007-10-26
sudo

---

### Post by bardic on 2007-10-26
thanks for the replies. 
I have one more question. I have a drive that doesn't mount on start up and I want to make it do so. I assume I need to add it to fstab, but I don't know how to get the UUID for it.

---

### Post by taurus on 2007-10-26
You can just use the device name like /dev/hdb1 if you wish.  Works just as well.

---

### Post by bardic on 2007-10-26
Sorry for asking all the n00bish questions, but...
I tried to add this to fstab:

/dev/disk /home/bardic/Music ntfs-3g defaults,locale=en_CA.UTF-8 0 1

And it said that /dev/disk is a directory, which makes sense i guess...But I dunno to make it think it's the drive or if i'm doing it totally wrong.

---

### Post by taurus on 2007-10-26
What partition do you want to mount?  It's definitely _not_ **/dev/disk** because it should look something like /dev/hda1, /dev/hda2, /dev/hda3, /dev/hda4, /dev/hdb1, /dev/hdb2, /dev/hdb3, /dev/hdb4, etc.

If you not sure what it's called, look at the output of this command from a terminal.

```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

### Post by bardic on 2007-10-26
Dude, you're my hero! Thanks a lot. 

It was /dev/sdb5/ I was looking to mount ^^

---

