---
title: "[SOLVED] sessions/startup programs question"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-09-05
Problem:  I need to run ```
sudo modprobe bcm43xx
``` on startup.  I have it listed as a code to run on startup in under Sessions/start up programs, but it doesn't run on startup.  Is there anyway I can make it run on startup?

---

### Post by mevets on 2007-09-05
using gksudo instead of sudo will prompt you for the password.

---

### Post by ThrobbingBrain66 on 2007-09-05
In a terminal open up your /etc/modules file:
```
gksudo gedit /etc/modules
```
add 'bcm43xx' to the end of the file, save it and reboot.  The module should now be loaded at every boot.

Obviously then you don't have to do anything with startup programs. :)

---

### Post by ThrobbingBrain66 on 2007-09-05
> **mevets said:**
> using gksudo instead of sudo will prompt you for the password.

His use of sudo is actually correct being that it's not a graphical application.  
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

In any event, the OP would be asked for his password at every boot which would become a hassle.

---

### Post by chrono310 on 2007-09-05
> **ThrobbingBrain66 said:**
> In a terminal open up your /etc/modules file:
```
gksudo gedit /etc/modules
```
add 'bcm43xx' to the end of the file, save it and reboot.  The module should now be loaded at every boot.

Obviously then you don't have to do anything with startup programs. :)

Yeah, this sounds like the way to go to me, unless you only want to enable that module for specific users.

---

### Post by fontenot_1031 on 2007-09-05
Thank you very much.  Problem solved.

---

