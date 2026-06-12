---
title: "save winxp data"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by benl on 2007-11-12
Hi, 

My compaq laptop runs winxp professional. Today, when I pressed the power button, the winxp screen loads until the bar where 3 lights go across and remains. I tried safe mode, etc but it doesn't load. Don't know why cos I haven't modified registry / installed any new software.

I also have a Ubuntu livecd and I put the livecd in and under Computer - File Browser it shows CD-ROM drive, 27.96 GB volume, and Filesystem. I right click the 27.96 GB volume and double to clicked to open but it had an error message. Same error message appears when I right click to mount. Error: unable to mount the selected volume; device /dev/hda1 is not removable; could not execute pmount.

:confused: I'm a newbie to Ubuntu, so pls forgive the stupid questions.
I just wanna copy all my documents to my pendrive and then  probably reformat. Any ideas on how to copy the documents?

---

### Post by kyphi on 2007-11-12
To repair your XP installation you can use your XP disc - it has a repair facility built in.  Then you can save all your files to a USB stick.

There is no point in inserting the Ubuntu disc while you are in XP, except if you are going to reboot.

---

### Post by benl on 2007-11-12
Thanks. Unfortunately Compaq only gave OEM winxp cds which do NOT have a function to recover - it just formats the hard disk! Any ideas on how to access the hard disk data while using the Ubuntu livecd?

---

### Post by taurus on 2007-11-12
You first need to mount it first before you can access it.  Assuming your windows is on /dev/sda1, open a terminal and run

```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
ls -la /media/windows
```
You can now access your files on windows under /media/windows.

---

### Post by benl on 2007-11-13
:KS finally,  i managed to 'see' my files. I went to another post and tried
sudo -s
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows
ls -la /media/windows
gksudio nautilus

So then File Browser was opened and I managed to locate the folders under mydocuments. 
However, I right clicked on a few folders and then right clicked to paste into my pendrive, but nothing was copied :confused:
Pls can you help me how to copy the folders to pendrive?

thank you.

---

### Post by kyphi on 2007-11-14
Can you drag and drop ?

---

### Post by benl on 2007-11-15
Thanks mate. Yes, I tried drag n drop and it worked!! alleluia it feels like raining!:)

---

### Post by kyphi on 2007-11-15
Glad that you are up and running again, benl.

Rain? -  We could do with some of that in 'the land down under'.:)

Now you can close this thread.

---

