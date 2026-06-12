---
title: "Help Please"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-13
Hey! I'm new to this, i'm trying to install ubuntu, but when I get to the point where it asked how do i want to partition the disk, i chose the first option, to resize and use freed space, so i chose that option, then after new partition size, theres a horizantal line where i can move the thing and the size changes... so i didnt really know what to do, so i took the smaller size... then after like 2 mins, the forward icon was not white anymore, so i pressed it, and theres nothing happening now... the forward button is white again... and the round cursor (that tells me i have to wait) is there. It's been a long time now... i've done this now 3 times.. always does the same thing, what am I doing wrong? I've been trying windows vista for a while, a trial, now they want me to activate (i'm broke) and I CAN'T access ANYTHING on my computer! So I can't go defrag my drive, or go in tools... anything... I really don't know what to do, I think most of my important stuff is on my external drive, but I would still want to keep my stuff, I still have stuff I wouldn't mind to keep. But if my only option is to erase everything... i'll do it, but not if there's an answer to my problem. Is it normal that nothing is happening?

This is what I tried from an other post to find my stuff on my drive:

sudo mkdir /media/windows 

and got this:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 14592 117210208+ 7 HPFS/NTFS

Now the guy in the other post say after paste this: 

sudo mkdir /media/windows
sudo mount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,umask=0222

I got this:

ubuntu@ubuntu:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,umask=0222
mount: special device /dev/hdb1 does not exist
ubuntu@ubuntu:~$ 

HELP! It seems there is a way to get my files, but how?

---

### Post by taurus on 2007-03-13
Try

```
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```

---

### Post by dstew on 2007-03-13
Your mount command should be

ubuntu@ubuntu:~$ sudo mount /dev/**hda1** /media/windows -t ntfs -o nls=utf8,umask=0222

---

### Post by julie_lebou on 2007-03-13
I don't understand, I whent to try it again, but when I pasted this: sudo mkdir /media/windows, it told me this: 

mkdir: cannot create directory `/media/windows': File exists

I don't get it... it was working before...

---

### Post by taurus on 2007-03-13
> **julie_lebou said:**
> I don't understand, I whent to try it again, but when I pasted this: sudo mkdir /media/windows, it told me this: 

mkdir: cannot create directory `/media/windows': File exists

I don't get it... it was working before...

It's because you already created /media/windows.  You don't need to run that command again.  If you don't believe me, look at the output of this command and you will see a windows directory on the list.

```
ls -la /media
```
So, just mount your harddrive then.

```
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```

---

### Post by julie_lebou on 2007-03-13
ok, so i did this 

sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222

and nothing happened on terminal, was it suppose to show up something?

---

### Post by taurus on 2007-03-13
Nothing shows up is good because there is no error message.  Now, your /dev/hda1 is mounted to /media/windows.

```
ls -la /media/windows
```

---

### Post by julie_lebou on 2007-03-13
Where are they located? I want to put them on my external drive! I hope this works!!!

---

### Post by taurus on 2007-03-13
Your first harddrive is now located in /media/windows.  So, you can view the content of your /dev/hda1 with nautilus if you want.  Just navigate to /media/windows and everything will be under that.

---

### Post by julie_lebou on 2007-03-13
what is nautilus?

---

### Post by taurus on 2007-03-13
Nautilus is a filemanager for Gnome.

---

### Post by julie_lebou on 2007-03-13
OMG i found all my stuff! It's all there! Thank you my hero! :) Now i guess i should put that on my external drive, then install ubuntu by erasing all my drive?

---

