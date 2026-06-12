---
title: "lost ubuntu upon windows install"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by strokeboy on 2007-06-10
Hello

I was dual booting in windows and ubuntu when I discovered that the windows didin't boot anymore.  (probably after I resized it with gparted)  So, I reinstalled windows to it's respective partition and now that is the only thing that shows up when I boot.  I lost the boot screen that offers the choice of ubuntu or windows.  I am pretty sure my ubuntu is still in there but I need to know how to access it to boot it.  Should I reinstall it?  Any ideas?  Thanks. jd

---

### Post by durrell on 2007-06-10
You need to reinstall the GRUB boot loader. The Windows installer rewrites your master boot record and makes Windows the only OS you can boot into.

[http://ubuntuforums.org/showthread.php?t=469018&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=469018&highlight=reinstall+grub)

That should tell you how to do it.

---

