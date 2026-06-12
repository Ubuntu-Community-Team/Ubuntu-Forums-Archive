---
title: "reinstalling mac on imac g4 problem"
date: 2008-10-24
forum: Apple Hardware Users
---

### Post by krazykeith250 on 2008-10-24
I am reinstallin mac os 10.4.6 on a imac g4 that I had ubuntu 7.04 on.  I am doing this because the desktop effects.  The only problem is that in the istallation it asks you where you want to install mac. Normally it would have a picture of your hard drive and you click it and you can install it on the computer.  The thing is that there is no hard drive to choose from, so I don't know how to install it.  Can anyone help me?

---

### Post by tiresia on 2008-10-24
Most probably you need to format the HD with HFS+ before installing MACOSX. From the installation Disk format the HD with the Apple Disk Utility

---

### Post by cyberdork33 on 2008-10-24
> **tiresia said:**
> most probably you need to format the hd with hfs+ before installing macosx. From the installation disk format the hd with the apple disk utility

+1

---

### Post by Frak on 2008-10-25
Press C on bootup (you know that)

Utilities -> Disk utility
Select disk
Use "Erase" since Partition might not be recognized by the installer
Give it a name and a scheme (such as Macintosh HFS Extended (Journaled))
Exit and continue with the installer.

happy times :)

---

