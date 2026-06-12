---
title: "what is a Automounter"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-23
I wanted to know what is a automounter ?

---

### Post by az on 2006-12-23
A long time ago, you need to mount usb drives and stuff like that yourself.  It would not mount on its' own.  There were a couple of clumsy implementations of accomplishing this before hotplug and then Udev presented an elegant solution.

automount or autofs was a way to mount a drive so that it would not be mounted at boot time, but when you accessed it.  So youwould plug in your usb drive and then try to access the place where you automounted it.  The kernel would then mount the drive for you.

Supermount was a sloppy and unstable way to accomplish what hotplug and udev do  - that it mount a cd or usb drive when it was inserted/plugged in.

Why do you ask?

---

### Post by tagginannie on 2006-12-23
> **lance_klusener said:**
> I wanted to know what is a automounter ?
Hi Lance 

With out getting to geeky ;-) The auto mount handles mounting of different file systems and disks such as MS floppy and cdrom drives like the way Windows dose and almost eliminates the need to do type in the command when you want to access those file systems. To find out more about it read the Wiki "[AutomaticallyMountPartitons]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")" or you can also find out more about by going to Google and search for Linux automount or autofs.


Merry Christmas

Suzy

---

