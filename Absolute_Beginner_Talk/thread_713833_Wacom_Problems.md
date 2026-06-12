---
title: "Wacom Problems"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-03-03
So under 6.06, I had full Intous 3 support (If I let the OS start up with it plugged in).

Now I have 7.10 and the wacom tablet is not working fully, even if I have it plugged in form startup.

Any suggestions?

---

### Post by Xarok on 2008-03-03
Shameless bump

---

### Post by BillDozer on 2008-03-03
You have to uncomment three lines in xorg.conf.
```
gksudo gedit /etc/X11/xorg.conf
```

I cannot remember which lines, search for uncomment and you should be able to find them.

---

### Post by Xarok on 2008-03-03
Hmm, after I did that and restarted my system...
THe whole OS is now jacked up.

HOw can I start up in just text mode?
(To revert the file back)

---

### Post by Xarok on 2008-03-03
OK well I figured out how ot revert it,
but it's still messed up.

Must be messed up from something else.
annoying...

---

### Post by BillDozer on 2008-03-03
What is messed up? The wacom tablet or your xorg.conf

---

### Post by Xarok on 2008-03-03
I posted a new thread about it called "No Resume Image".

Basicly after the load screen, the login screen is all garbled and I can't see anything.

Is there a way to restart gnome?

---

### Post by BillDozer on 2008-03-03
Sorry to hear about that, I replied to your other post with at solution to that problem.

I also found a link about the Wacom activation: [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

---

