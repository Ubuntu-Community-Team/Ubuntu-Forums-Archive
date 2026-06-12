---
title: "[SOLVED] Running sudo command during startup"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2008-03-04
Simple question. I need to execute "sudo /etc/init.d/samba start" at startup. How can I write a command to execute a sudo command, and where do I put it? Or is there a better way to start a samba share anytime Ubuntu starts up?

---

### Post by dca on 2008-03-04
If you installed samba server (samba) package it should start automatically when booting...

---

### Post by jordanmthomas on 2008-03-04
Also, if you don't want to get into learning how to edit services and how / when they start up (it's sort of complicated), you can just put 
```
/etc/init.d/samba start
```
in the file /etc/rc.local and it will be run as root on startup.

However, like dca said, it should start itself on boot unless you've specifically disabled it.

---

### Post by TekMuzik on 2008-03-04
Sorry. Haven't disabled it on anything. Just last time I had to restart my Ubuntu box, none of my other computers could connect to my Samba share until I ran the start command again. Maybe just a fluke coincidence though?

---

