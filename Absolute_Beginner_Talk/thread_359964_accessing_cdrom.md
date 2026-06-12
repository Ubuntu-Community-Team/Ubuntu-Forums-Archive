---
title: "accessing cdrom"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by shdawson on 2007-02-12
hi,


have ubuntu server installed.  i have a deb file on cd in need to run.

from the root, i can see cdrom in teal text from command line.  what i cannot understand is how to access the cdrom.

#sudo dpkg --install webmin_1.320_all.deb

comes back with "No such file or directory". 


So, what does this mean?  Thanks.....

---

### Post by angkor on 2007-02-12
> **shdawson said:**
> hi,


have ubuntu server installed.  i have a deb file on cd in need to run.

from the root, i can see cdrom in teal text from command line.  what i cannot understand is how to access the cdrom.

#sudo dpkg --install webmin_1.320_all.deb

comes back with "No such file or directory". 


So, what does this mean?  Thanks.....

It means you're in the wrong directory. Go to the directory that contains webmin_1.320_all.deb and try again.

You could also try adding (or uncommenting) the cdrom line in your /etc/apt/sources.list. If you've done that you can use apt to install packages from the cd.

---

### Post by shdawson on 2007-02-12
OK, path issue.

This package is not on a mirror.  I am looking to install webmin.

So, what syntax do I use to hit the cdrom that has the package?  OR......, do you know of a mirror I need to add to the sources.list to get it from there????  That would be the preferable way for this to happen.


THANKS!!!!!

---

### Post by angkor on 2007-02-14
If you have internet access you can try this method:

[http://www.ubuntuforums.org/showthread.php?t=348526](http://www.ubuntuforums.org/showthread.php?t=348526)

---

