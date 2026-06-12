---
title: "[SOLVED] Howto edit file. Says I'm not owner?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by ocean223 on 2007-08-11
How do I edit this file /etc/modprobe.d/options ??
It keeps telling me I can't change permissions cuz I'm not the owner.
I can't seem to find out how to do this.:confused:
I know this is for my protection but it gets annoying at times.
Is there any way to be logged on as superuser all the time so I don't have to deal with this permissions thing?

---

### Post by p_quarles on 2007-08-11
Try this:
```
gksudo gedit /etc/modprobe.d/options
```
That will allow you to edit the file and save changes.

---

### Post by eapache on 2007-08-11
in a terminal, run```
gksudo nautilus
```this opens the file browser with super permissions. I would suggest putting this in a link (right click and select 'edit menu')

---

### Post by ocean223 on 2007-08-11
Thanks ! I Thats it. Now I hope I don't blow up the box........again.  So little knowleddge is sooooooo
dangerous.:)

---

