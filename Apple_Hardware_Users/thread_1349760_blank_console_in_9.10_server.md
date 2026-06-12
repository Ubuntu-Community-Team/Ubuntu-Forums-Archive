---
title: "blank console in 9.10 server"
date: 2009-12-08
forum: Apple Hardware Users
---

### Post by jason0 on 2009-12-08
Hello,

My company just purchased a new series 3 mac mini, and asked me to install ubuntu 9.10 server on it.  I solved the problem of rebooting by building and installing the 2.6.32-7-server from lucid.lynx.  The system looked fine, and works well.

My current problem is that the display has gone blank.  It did this when I went to install the server in our colocation facility, and plugged the crash-cart monitor in.

During bootup, the last thing I see on the screen is refit.  There is no screen during the grub2 countdown, nor is there any screen after booting is complete.  I CAN remotely login to the system so I know the system is running.  I can login at the console (verified by running ps in the ssh session).  It's clear that the problem is one of getting output to the monitor.

It appears that some graphics mode was set during grub that remained once the system booted up.  The monitor does not claim that its being driven out of bounds: in fact, the monitor goes into power save mode.

Xwindows is NOT installed.  

One solution appears to force plain text mode on the system.  I don't want splash screens, or graphics upon bootup.

Can anyone help?

--jaso

---

### Post by PacketCollision on 2010-01-24
Try adding "blacklist i915" to /etc/modprobe.d/blacklist.conf -- that finally fixed it for me.

---

