---
title: "NTFS mounting"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Sherlock Holmboy on 2006-03-19
when i try to mount an NTFS drive in the GNOME GUI, it says it's unformatted. when i take a look at the drive with fdisk it says that it's SFS (my googling came up with secure file system). how do i get my system to recognize it as NTFS?

---

### Post by aysiu on 2006-03-19
How do you know it's NTFS?

---

### Post by Sherlock Holmboy on 2006-03-19
because i was using it in windows,

---

### Post by aysiu on 2006-03-19
Try these directions (abbreviated):
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

or these directions (more explanations):
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

The terminal is Applications > Accessories > Terminal in Gnome or KMenu > System > Konsole in KDE.

---

### Post by Sherlock Holmboy on 2006-03-19
well, as per those instructions when i "fdisk -l" it shows up as SFS as well as in cfdisk. i installed gparted for kicks and it sees as NTFS. i know for a fact that this drive is NTFS. i pasted ```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
``` into my fstab and the disk mounter GUI recognized it as NTFS but still wouldn't mount. im not sure if it matters to anything besides the hda v. sda label, but this is a 200GB SATA drive

---

