---
title: "insmod problem"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by extasy on 2007-12-18
Hello!

I'm trying to make a script to run things during startup. I created a file called startup.sh in /etc/init.d and have made it +x. I also update-rc :ed it with default 80 so it would run only on startup. Now in this file I would among other tings have a insmod to a /home/mythtv/sasc-ng/trunk/dvbloopback.ko.

I can load it manually by entering the folder and run a insmod, but I cant from root run a insmod ./home/mythtv/..../dvbloopback.ko, says that the file is missing.

Please help a newbie.

Regards
Henrik

---

### Post by red_Marvin on 2007-12-18
The dot at the path means that the path begins in the current directory, are you sure you want that? From the looks of the path it like it should start at the root directory, if that's what you want then just remove the dot.

---

### Post by chippy99 on 2007-12-18
Firstly modprobe is preferred over insmod. If you read the man pages on modprobe it tells you were it searches for modules and how to configure /etc/modules so that a module gets load at start up.

---

