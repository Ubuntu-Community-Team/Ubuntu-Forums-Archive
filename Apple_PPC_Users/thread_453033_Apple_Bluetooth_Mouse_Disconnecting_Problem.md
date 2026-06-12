---
title: "Apple Bluetooth Mouse Disconnecting Problem"
date: 2007-05-23
forum: Apple PPC Users
---

### Post by gamgee911 on 2007-05-23
I followed [the guide]("http://ubuntuforums.org/showthread.php?t=227057") for using a bluetooth mouse with Ubuntu.  The mouse connects but only until I log in, then it stops sycning.  Am I missing sometime?  Thanks :(

---

### Post by stmiller on 2007-05-23
Check this out:

[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

I made an addition to the PPCFAQs linking to this guide.

---

### Post by gamgee911 on 2007-05-24
Hey, thanks!  It seems to be working now.

---

### Post by gamgee911 on 2007-05-25
No, I am still expirencing it unsync when I shut down.  I have to run the sudo hidd --connect command to get it to synch and sometimes that doesn't work.

---

### Post by happiness on 2007-05-25
in your /etc/default/bluetooth file, you should have something like this:

HIDD_ENABLED=1
HIDD_OPTIONS="--connect XX:XX:XX:XX:XX:XX --server"

where XX:XX:XX:XX:XX:XX  is the mac address for your mouse.

---

