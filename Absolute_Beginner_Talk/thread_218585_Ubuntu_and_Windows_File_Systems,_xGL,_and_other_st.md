---
title: "Ubuntu and Windows File Systems, xGL, and other stuff"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by tromik on 2006-07-18
I've used Ubuntu before, always as a secondary OS to Windows. The biggest problem I always had was that I couldn't write to my NTFS drives.

I'm thinking about using Ubuntu as a primary OS now, as this machine is getting very old, but again, I'd still like to be able to use Windows. Is there any file system that both Ubuntu and Windows can write to that allows for files over four gigabytes? I know Fat32 can't handle large files.

Also, I'm curious about xGL. Does Ubuntu sopport it, and is it easy to install?

Finally, can anyone direct me to a site that lists the differences between Gnome and KDE, besides the way they look? I think I'd rather use Ubuntu than Kubuntu just for the sopport, but is the support for one the support for the other when it comes to installing things from the repositories?

Thanks.

---

### Post by Jagot on 2006-07-18
With regards to a file system both Ubuntu and Windows can write to, you can use this driver with Windows to enable it to read/write ext3 partitions:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Comparison with GNOME/KDE:

[http://bdmorrison.com/ubuntu/kdegnome.html](http://bdmorrison.com/ubuntu/kdegnome.html)

XGL is pretty easy.  You can find tutorials here:

[http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)

---

### Post by tromik on 2006-07-18
Thanks. Could I used Gparted to convert my NTFS drives to Ext2 without losing all my data?

---

### Post by Jagot on 2006-07-18
> **tromik said:**
> Thanks. Could I used Gparted to convert my NTFS drives to Ext2 without losing all my data?

No - the partition would be reformatted in the process so you'd have to back up first.  Just found this which came up on Digg today  - haven't tried it myself but you may want to have a look if you can't back up your stuff:

[http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)

---

### Post by givré on 2006-07-18
My got this guy is using my HowTo. Things go really fast in the linux world 8) 
For the full HowTo, go there : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
In the first page you will have a link to my test. Good luke 8)

---

### Post by tromik on 2006-07-18
> **givré said:**
> My got this guy is using my HowTo. Things go really fast in the linux world 8) 
For the full HowTo, go there : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
In the first page you will have a link to my test. Good luke 8)

Thanks, I'll try this out. Sounds like a good solution, for now anyway.

At some point I'd like all my drives to be something Ubuntu can natively read and write to, and just have my NTFS drive for Windows.

---

