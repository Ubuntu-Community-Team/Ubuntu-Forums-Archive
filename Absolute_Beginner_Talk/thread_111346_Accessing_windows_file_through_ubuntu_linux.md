---
title: "Accessing windows file through ubuntu linux?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by tomcoa on 2006-01-02
Hi, I am new to linux and I was wondering if it's possible to access your files saved in Windows though linux? I am running Windows XP and Ubuntu Linux.

Help would be appreciated.

 Thanks :D

---

### Post by sharke on 2006-01-02
[QUOTE=tomcoa]Hi, I am new to linux and I was wondering if it's possible to access your files saved in Windows though linux? I am running Windows XP and Ubuntu Linux.

Help would be appreciated.

 Thanks :D[/QUOTE]
Yes it is but you need to set it up .
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

Regards
Sharke

---

### Post by Madpilot on 2006-01-02
Better than the ubuntuguide:
[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

Note that NTFS is read-only for Linux; blame Microsoft for that one...

---

### Post by kenweill on 2006-01-02
[QUOTE=tomcoa]Hi, I am new to linux and I was wondering if it's possible to access your files saved in Windows though linux? I am running Windows XP and Ubuntu Linux.

Help would be appreciated.

 Thanks :D[/QUOTE]

Yes. What file? Excel file? Word? Powerpoint? 

You have to mount the windows partition first before you can access those files.

First, type this in your command prompt/terminal:

sudo fdisk -l

Then post your output here.

---

