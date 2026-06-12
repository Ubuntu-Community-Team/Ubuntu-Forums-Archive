---
title: "xserver failed to start"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by gmcm1979 on 2006-09-14
i got the error with xserver failing to start before but read the thread about this error and upgraded to version 10.4 and everything was working fine until an update today, i rebooted and get the same error message again, i have posted about this in the other thread but hav had no reply

---

### Post by steve.horsley on 2006-09-14
It's difficult without knowing more detail. But things you could perhaps do are:

1) login and run the command **start**x, and tell us what the error message is.

2) make a backup of xorg.conf with this command:
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
and then try to reconfigure with this command:
**sudo dpkg-reconfigure xserver-xorg**
You can just hit enter for any questions you don't know the answer to, to take the default.
then **startx** and see if it starts.

---

