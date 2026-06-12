---
title: "Installed KDE, now trying to uninstall [resolved]"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-17
Well I was trying out a bunch of Window Managers only to find out that I still like GNOME the best. After uninstalling them all I noticed that KDE left behind a handful of KDE programs. 

Is there any easy way to uninstall these? Because I like to have my HDD as clean as possible, and this is really a pet-peeve.

*Sorry about all of the help threads, I'm running into wall after wall on Ubuntu!*

---

### Post by ThrobbingBrain66 on 2006-12-17
Check out this link, I think it'll help.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

The whole site is very good, I would bookmark it if you haven't already.

---

### Post by aysiu on 2006-12-17
If you used *apt-get* to install it, you would do ```
sudo apt-get autoremove kubuntu-desktop
``` If you used *aptitude* to install it, you would do ```
sudo aptitude remove kubuntu-desktop
``` Otherwise, if those aren't enough, you can try this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Pobega on 2006-12-17
Thanks, that was very helpful!

---

### Post by redpotty on 2006-12-19
I installed KDE on my desktop PC running Ubuntu 6.06 using the psychocat step-by-step instructions.  It hung three times during the setup and installation which I resumed using "dpkg --reconfigure -a".  Finally, I had it installed.  However, my wired internet connection completely fails to connect to anything.  My webserver still serves pages with no problem but I can't get to read the Ubuntu forums. Our laptop (running WinME) is also refusing to connect to the internet through its wireless connection.  Any ideas what installing KDE has done?
The router setup is all OK.

---

### Post by Pobega on 2006-12-19
If two computers aren't working, it would most likely be a problem with your ISP and not KDE. I highly doubt KDE could adversly affect your router, so I would call up your ISP and tell them what's happening and ask them if something is going on with their service.

---

