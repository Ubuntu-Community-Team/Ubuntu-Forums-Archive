---
title: "Cannot get second HDD to mount in 6.06"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-09-01
I made a headless ubuntu 6.06 tower for downloading.  I'm trying to get my 120 gig HDD formatted to be able to work with Ubuntu and to be able to mount it over my home network on OS X.  I used Disk Utility on my macbook and formatted the drive to MS-DOS format.  I put it in the ubuntu box and booted up.  I logged into ubuntu with VNC Viewer and I can see the HDD when I go to Places/Computer but when I try to mount it, it says:

error: device /dev/hdb1 is not removable
error: could not execute pmount

I don't know what those mean (newb.)  Can anyone help me fix this?  Thanks.

Russ

---

### Post by wolfen69 on 2007-09-01
try formatting it in ntfs. then:
```
sudo apt-get install ntfs-config
```
then ntfs-config will show up in applications>system tools

---

### Post by dmber on 2007-09-01
> **wolfen69 said:**
> try formatting it in ntfs. then:
```
sudo apt-get install ntfs-config
```
then ntfs-config will show up in applications>system tools

thanks.  can i format it with ubuntu?  (it's a pain moving it from my tower to my external enclosure)

---

### Post by dmber on 2007-09-01
i opened up Gnome Partition Editor to reformat the HDD to NTFS, but NTFS is grayed out.  NTFS and HFS+ are the only two that are grayed out.

What can I do about that?

---

### Post by wolfen69 on 2007-09-01
try ultimate boot cd  [http://www.ubcd4win.com/index.htm](http://www.ubcd4win.com/index.htm) it's a very handy free utility disk.

---

### Post by dmber on 2007-09-01
the problem with booting to something is that my ubuntu tower is headless.  afaik (which isn't very far) i can't control a boot disc remotely...


i'm ready to reformat the hard drive using Gparted, but NTFS is grayed out as a choice.  any ideas how to fix that?

---

### Post by dmber on 2007-09-01
ok, i'm sorry if i'm being impatient, but really, this doesn't seem like it should be this hard.  it took me 30 seconds to format this hard drive on OS X.  why is NTFS blurred out?  is there a different format I can use that will work between os X and Ubuntu?  JFS for instance?

---

