---
title: "wine problems"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-07
i got this issue with wine,
i want to use the wine browser all the time and not have it only open during the terminal use, anyone wanna help?

---

### Post by Max Luebbe on 2006-07-07
Irish, I think you're in the wrong thread.

Real quick way to see if you installed the server version by mistake would be the startx command.

If you get a graphical display of any kind rather than bad command or filename, you've got a bad desktop install.

You may need to reboot after this step however.

---

### Post by CounterBlow on 2006-07-07
> **Max Luebbe said:**
> Irish, I think you're in the wrong thread.

Real quick way to see if you installed the server version by mistake would be the startx command.

If you get a graphical display of any kind rather than bad command or filename, you've got a bad desktop install.

You may need to reboot after this step however.
I entered: "startx" at 'the prompt', and it said, unknown command. *shrug*

---

### Post by tonyr on 2006-07-07
The inference from **Max Luebbe**'s suggestion and what you saw from
trying to do **startx** is that you have the wrong kind of installation,
a **server** installation, which has **no** X support and **no**
desktop.   There is a way to get all that on your installation, but it
is relatively complicated.  The better thing to do is to get a LiveCD
disk image, burn it (as an iso image) to a CD, and redo the install.

If the install disk **is** a LiveCD, then something went very wrong
during the installation, or the CD was bad, in which case you should
get another one anyway.

---

