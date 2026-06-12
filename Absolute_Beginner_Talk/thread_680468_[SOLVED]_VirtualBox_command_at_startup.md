---
title: "[SOLVED] VirtualBox command at startup"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by karuzo on 2008-01-28
Hello all,
    Some time ago when I had problems running a virtual session, I found I had to run "chmod 777 /dev/vboxdrv" before initiation.
However, it seems as everytime I start a virtual session I will need to enter this command (with sudo).
Any suggestions how to prevent this requirement?
Thanks,
    Doron

---

### Post by Zars on 2008-01-28
Is your user login a member of the vboxuser user group? You can add yourself to the group in the user settings, under manage groups :)

Let me know if it helps
Zars

---

### Post by karuzo on 2008-01-28
Thanks,
    It worked - It didn't take affect until I restarted X.

---

