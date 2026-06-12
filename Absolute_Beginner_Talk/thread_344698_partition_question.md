---
title: "partition question"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by jshurak on 2007-01-23
I have an external HD that I back up my windows music and pics.  Can I partition this drive to install a distro on it and still retain the other partition for windows use?  Thanks for your help in advance.

---

### Post by Pobega on 2007-01-23
Yes, you can do that. If the drive is FAT though, you might want to defragment it first.

From the Ubuntu 6.10 LiveCD you can hit Alt+f2, type "*gksudo gparted*" and partition from there. You may have to switch devices, though, because by default it uses your internal HDD.

Also, make sure your external HDD is not mounted when you try to partition it. You can't partition a mounted drive.

---

### Post by jshurak on 2007-01-23
Thanks for your speedy reply!!  I'm not sure about the mounting.  When I access the drive through windows, its its own drive.  its connected to the computer through a USB port and can easily be taken to a different computer.   Does the Ubuntu install include a boot option when starting the PC?

---

