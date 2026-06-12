---
title: "Navigating XP files in Gutsy Gibbon"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by mbslrm on 2008-04-11
My installation of XP got corrupted, so I got a copy of Gutsy Gibbon so that I could get my files from the XP partition and put them on a USB drive using the LiveCD. I got the LiveCD to work, but now I don't know which folders I have to navigate through to get the XP partition. 

Can someone post up screenshots or a detailed, amateur-oriented instruction on how I can find the XP partition?

---

### Post by wormser on 2008-04-11
Your Windows and USB drives are going to mount under /media.  Just browse to the folder with nautilus and you should be fine.

---

### Post by twist2b on 2008-04-11
goto "places" up at the top and choose "Computer"

select the partition that is the XP (you can tell by the GIG size)

make sure to goto USR or USERS I cant remmember which
then select your name and your good.

---

### Post by mbslrm on 2008-04-11
I already went to those folders. They have many more folders inside.

And the LiveCD isn't showing a taskbar at the top. How can I enable it?

---

### Post by JoshuaRL on 2008-04-11
If you want to browse files in a hard drive on the Live CD, you'll need to mount the drive.  The Live CD doesn't mount hard drives normally because it can't install with the hard drive mounted.

Go [here and look at the second post.](http://ubuntuforums.org/showthread.php?t=316580)  That will explain how to mount your drive.  Then you want to go to the right place in your Media directory within the / (root) directory.  Your hard drive should be in there.

To get the USB stick to mount, make sure it isn't plugged in when you start up the computer.  Plug it in and it should be auto-recognised and mounted in a little bit.  It may take a while depending on how fast your computer is and how much RAM you have.

Hope that helps.

---

### Post by mbslrm on 2008-04-11
> **JoshuaRL said:**
> If you want to browse files in a hard drive on the Live CD, you'll need to mount the drive.  The Live CD doesn't mount hard drives normally because it can't install with the hard drive mounted.

Go [here and look at the second post.](http://ubuntuforums.org/showthread.php?t=316580)  That will explain how to mount your drive.  Then you want to go to the right place in your Media directory within the / (root) directory.  Your hard drive should be in there.

To get the USB stick to mount, make sure it isn't plugged in when you start up the computer.  Plug it in and it should be auto-recognised and mounted in a little bit.  It may take a while depending on how fast your computer is and how much RAM you have.

Hope that helps.

So running the two commands listed on the second post on that link should mount it? And for some reason, the LiveCD doesn't seem to have a taskbar. Last time I used Ubuntu 6.04, there was a taskbar in the LiveCD. (I haven't touced any Linux in about a year).

Should 512 MB of RAM and a P4 1.7 Ghz be good enough to move files from the XP partition to a USB stick?

---

### Post by JoshuaRL on 2008-04-11
That should be enough, but it may be slow depending on how much you want to transfer.

Yes, the Live CD should have task bars.  Try the Xubuntu if you want it to run a little faster.

---

### Post by mbslrm on 2008-04-12
> **JoshuaRL said:**
> That should be enough, but it may be slow depending on how much you want to transfer.

Yes, the Live CD should have task bars.  Try the Xubuntu if you want it to run a little faster.

For whatever reason, no taskbar is showing. All it's showing is the Install and Examples icons.

What's the keyboard shortcut for the command line?

---

### Post by sharks on 2008-04-12
Press alt + F2 to open the run dialog. If u want to nautilus type nautilus in the run dialog.

---

### Post by mbslrm on 2008-04-12
> **sharks said:**
> Press alt + F2 to open the run dialog. If u want to nautilus type nautilus in the run dialog.

I tried that to no avail.

I tried some other shortcut (Ctrl + Alt + F2) and the whole screen became a command line.

I tried to get it to list all partitions with the following command:

```
sudo fdisk -1
```

It just said not recognized and posted up some other generic crap.

I also tried:

```
sudo fdisk
```

---

