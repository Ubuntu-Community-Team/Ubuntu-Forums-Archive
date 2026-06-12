---
title: "Graphics card problem"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by darkrebel260 on 2008-03-12
I recently upgraded to Ubuntu 7.10 Gutsy. I am using a ATI Radeon X850XT, and after working for the first few hours, nothing I do can get it working again.
Upon bootup I get a message saying that "Ubuntu is running in low graphics mode". I have tried using Envy to update my drivers, however the same message appears every time i start up.
I found a topic that talked about direct rendering, but couldn't figure out how to change the file i found for it. I'm not even sure that i'm heading in the right direction.

---

### Post by andydread on 2008-03-12
When you get the "Low graphics mode" message press Ctrl+Alt F2.  You should get a login prompt at a console.  log in and type sudo -s to become root.  Now.. type

Change directory 
```
cd /etc/X11 
```

Backup current xorg.conf 
```
cp xorg.conf xorg.conf-mybackup
```

Copy older xorg file over current one
```
cp xorg.conf.1 xorg.conf
```

reboot
```
shutdown -r now
```

This worked for me

---

### Post by darkrebel260 on 2008-03-12
no good, still having the same problem every time i boot up.

---

