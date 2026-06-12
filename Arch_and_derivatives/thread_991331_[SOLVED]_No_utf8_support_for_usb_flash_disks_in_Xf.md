---
title: "[SOLVED] No utf8 support for usb flash disks in Xfce/Arch"
date: 2008-11-23
forum: Arch and derivatives
---

### Post by medic2000 on 2008-11-23
How can i add this support to auto mounted drives.In Gnome we can do it with gconf editor. In XFCE i don't know the solution.

---

### Post by handy on 2008-11-24
You may be able to do some good with this:

***_[http://ubuntuforums.org/showpost.php?p=6216911&postcount=8](http://ubuntuforums.org/showpost.php?p=6216911&postcount=8)_***

Perhaps [***_Worker_***]("http://www.boomerangsworld.de/cms/worker/index?lang=en") could do it for you, though they won't be auto mounted you will have to select them & click the mount button, as I do for optical drives in the Worker I love. :-D:

***_[http://ubuntuforums.org/showthread.php?t=985706](http://ubuntuforums.org/showthread.php?t=985706)_***

---

### Post by medic2000 on 2008-11-24
> **handy said:**
> You may be able to do some good with this:

***_[http://ubuntuforums.org/showpost.php?p=6216911&postcount=8](http://ubuntuforums.org/showpost.php?p=6216911&postcount=8)_***

Perhaps [***_Worker_***]("http://www.boomerangsworld.de/cms/worker/index?lang=en") could do it for you, though they won't be auto mounted you will have to select them & click the mount button, as I do for optical drives in the Worker I love. :-D:

***_[http://ubuntuforums.org/showthread.php?t=985706](http://ubuntuforums.org/showthread.php?t=985706)_***

Thats not exactly what i want. Does'nt Xfce has native support or config file for this?

---

### Post by handy on 2008-11-25
Are you running the HAL daemon?

---

### Post by medic2000 on 2008-11-25
Yes i am running HAL daemon.

Note: By the way it doesn't have problems with extenal hard drives. They are mounting automatically with UTF8 support.

---

### Post by medic2000 on 2008-11-28
Bump!

---

### Post by medic2000 on 2008-11-28
Problem solved in the ArchLinux forums! I have installed the exo-dev(patched exo with utf8 support) package from AUR. Now i am happy so much ! :)

---

