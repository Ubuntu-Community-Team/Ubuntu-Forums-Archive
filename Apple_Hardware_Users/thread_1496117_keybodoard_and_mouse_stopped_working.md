---
title: "keybodoard and mouse stopped working"
date: 2010-05-28
forum: Apple Hardware Users
---

### Post by nikitchm on 2010-05-28
Hi,

I have Ubuntu 10.04 installed in dual boot with Mac OS X and it did work properly for a while. But after installation of ssh, gdesklets and perhaps some other general software, the mouse and keyboard stopped working.

As I restart the computer and start ubuntu normally it proceeds to the login screen, but the mouse and keyboard are not working there. Pressing Power-off button on the computer box brings up the count-down menu and it switches off in 60 seconds.

An attempt to use the rescue mode or the older release (from 2.6.32-22 to 2.6.32-21 - the only ones I have) leads to the same results (in the rescue mode the power button does nothing though).

Mac OS works alright (I'm using rEFIt boot manager).

Would somebody have an idea what's going on and what could be a remedy?

Thank you

---

### Post by abeltenny0210 on 2010-05-28
Have you right installed the drivers?

---

### Post by nikitchm on 2010-05-28
Well, the whole system had been working just fine and I didn't do anything to the drivers.

One more thing which I installed in addition to what I wrote above was VNC server. But I doubt it could cause any problems. Any software I installed through the synaptic package manager in any case.

---

### Post by linuxopjemac on 2010-05-29
Maybe stupid advise but cannot you remove those packages again and see if your mouse starts working again ? If you find out what's causing the trouble you can file a bug report.

I would chroot into your system from a liveCD if you can't type anything after booting.

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

---

### Post by nikitchm on 2010-05-29
Thank you for the suggestion.

I would try it, but first of all, I doubt that it's any of the packages I listed and thus would wait until time when I'll be ready to reinstall ubuntu, and second, how do I physically remove the package which has been installed? It's not just one file/folder...

---

### Post by linuxopjemac on 2010-05-29
to remove a package:

```
sudo apt-get remove package_name
```

---

### Post by nikitchm on 2010-05-29
Right, but for that, I presume, I need the operating system and I cannot type anything even in the rescue regime. If I chroot into the system, I will get an access to the files, but not apt-get command, right?

---

### Post by linuxopjemac on 2010-05-29
if you chroot into it you can do everything you normally can

---

### Post by nikitchm on 2010-05-29
That's interesting. Thank you for the advise. I believe I also should be able to get the list of the installed packages by date: [http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html](http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html) . I'll try it.

---

### Post by nikitchm on 2010-05-31
Well, I tried to remove some of the packages, in particular libgksu2-o (in my case, I removed package ending with 0), which was implicated in similar problems earlier ([http://ubuntuforums.org/archive/index.php/t-414724.html](http://ubuntuforums.org/archive/index.php/t-414724.html)) and some packages with "key" in their names, but couldn't find the one. There are just too many of them. So, I decided to reinstall the system and by installing the same packages, step by step, distill the one responsible for the bug. If I find it, I'll certainly file the bug report.

Thank you

---

