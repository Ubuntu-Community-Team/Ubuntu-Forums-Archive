---
title: "NTFS cannot be mounted on /, not a fully-functional Unix file system?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by ChaosTheory on 2007-12-27
I'm installing Ubuntu and I'm running the install in safe graphics mode through the boot screen. I get this when it starts to install files: 

"The file system type NTFS cannot be mounted on /, because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2." It halts the installation as it keeps appearing as I x the message. 

What should I do? I'm installing through Wubi, by the way (is that related)?

---

### Post by Seti on 2007-12-27
yup, you're doing it wrong.

---

### Post by ChaosTheory on 2007-12-27
What should I be doing?

---

### Post by taurus on 2007-12-27
You should format your / as ext3, not ntfs nor vfat since you can't really install Linux on a ntfs/vfat filesystem.

---

### Post by bodhi.zazen on 2007-12-27
Wubi is different , it installs Ubuntu into a virtual disk, Wubi is Beta however and may have bugs ;)

c:\wubi\disks\system.virtual.disk

That virtual disk needs to be formated as ext3

Something sounds wrong as wubi should be automatic.

[http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)

What have you done and have you tried the wubi forums ?

---

