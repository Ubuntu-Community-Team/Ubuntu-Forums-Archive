---
title: "Just a white screen... on ONE user?!?!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by gdoermann on 2007-06-07
Ok, so Feisty crashes on me every once in a while.  It just freezes up.  I restart, and things seem to work just fine.  (I don't know if that has to do with a clvm bug I was fixed before or not).  

Anyhow, I last time I restarted the Desktop Effects on the account  I was signed on to got corrupted (or that's what I'm assuming).  When I sign into that account it just goes to a white screen.  I have tried restarting the Desktop Effects with Alt+Ctl+Backspace with no avail... Any ideas?

---

### Post by Seisen on 2007-06-07
I got that white screen before when I tried Desktop Effect so you might want to disable it and see if you sitll have the same problems.

---

### Post by Crafty Kisses on 2007-06-07
> **Seisen said:**
> I got that white screen before when I tried Desktop Effect so you might want to disable it and see if you sitll have the same problems.

That's exactly your problem, disable the desktop effects and you should be good. :p

---

### Post by gdoermann on 2007-06-07
How do I disable the Desktop Effects, and what will that effect?

---

### Post by gdoermann on 2007-06-07
Is there a way to fix it then re-enable the desktop effects after?

---

### Post by Crafty Kisses on 2007-06-07
> **gdoermann said:**
> Is there a way to fix it then re-enable the desktop effects after?


You should try to reconfigure your X server, try the following:
```
 sudo dpkg-reconfigure xserver-xorg
```
After you do that, you can back it up, and next time if anything goes wrong you can recover it.

To recover your X server, try the following:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```
Hope this helps. :p

---

### Post by gdoermann on 2007-06-16
Thanks, but it finally fixed itself when I updated the system!

---

