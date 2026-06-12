---
title: "Weird update behaviour."
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-12-20
It seems that everytime I get a kernel upgrade (like today), my Ubuntu/linux won't boot the next time I try it. It gives an error 17. Now as this is not the first time this has happened, I already know how to fix it. However, I am wondering why this happens. From what I've been able to see the reason things go wrong is the fact that the entries in 'menu.lst' suddenly point to one place higher than they are supposed to (so (hd0,6) instead of (hda0,5)). Am I doing something strange or is it the update that messes things up?

---

### Post by philinux on 2007-12-20
It's the update ok. Someone else had same thing.

---

### Post by philinux on 2007-12-20
Here's the thread with a possible fix.

[http://ubuntuforums.org/showthread.php?t=645116](http://ubuntuforums.org/showthread.php?t=645116)

Doesn't seem to affect everyone though. I had no such problem, weird indeed. Worthy of a launchpad bug report

---

### Post by EvilBro on 2007-12-20
Is it known what causes this? I mean, the first time this happened I was not amused (and that's putting it lightly as I had only installed ubuntu for the first time the previous day). Now it is just annoying (but it just shouldn't happen. The update shouldn't change anything in menu.lst that was already there).

---

### Post by philinux on 2007-12-20
a kernel update does change grub, always has.

Why it should mess with the root ident I dont know. Report it a as a bug giving your system specs. Like I said I did the upgrade and no change. 

I've got two HD's maybe its a dual boot on one drive thing . :confused:

---

### Post by EvilBro on 2007-12-20
> **philinux said:**
> I've got two HD's maybe its a dual boot on one drive thing . :confused:
Nope, that's not it. I've done this on a dual boot (one drive) and a single boot machine and both messed up.

---

### Post by EvilBro on 2008-02-07
The latest kernel-update messed up one of my machines again. The other one stayed okay though. I did notice something else I found puzzling. After the update my machine's samba users were disabled (which caused me not to be able to get into shares or the printer). A simple 'smbpasswd'-enable user command was enough to restore functionality. Why is samba affected by a kernel update?

---

### Post by Huss on 2008-02-08
Great! That worked for me. I thought It would be hours of searching for a solution. 

THANK YOU!

---

### Post by mike.headon on 2008-02-10
In my case the problem seemed to be that menu.lst had been refreshed from the contents of menu.lst~.
If somebody had a valid config in menu.lst~ then I imagine no problem would have arisen.

---

