---
title: "Change default OS to Windows in GRUB"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by derekr44 on 2007-05-25
Yes, you read it right.  My wife can't stand having to use the arrow key to pick Windows instead of Ubuntu when GRUB loads.  So I would like to set Windows as the default OS in GRUB, that way she can turn on the computer and walk away for a few minutes while Windows loads (MS jab).

I read [this topic]("http://ubuntuforums.org/showthread.php?t=451799&highlight=grub+default&page=2") about switching the other way around, but this didn't help me.

So how can I set Windows as the default OS in GRUB?

And have a kernel while you're at it :popcorn:

---

### Post by icechen1 on 2007-05-25
Check [this]("http://www.linuxquestions.org/questions/showthread.php?t=468735") out.

---

### Post by Znupi on 2007-05-25
That was the first thing I managed to do by myself in Linux, lol. It's really easy, here's how to do it:
```

gksudo gedit /boot/grub/menu.lst

```
The first thing you will see that doesn't have a hash (#) in front of it will probably be
```

default 1

```
Change **1** to what your Windows menu item number is. For example, if your GRUB menu looks like
```

Ubuntu Linux 7.04
Ubuntu Linux 7.04 -- recovery mode
Ubuntu Linux 7.04 -- memtest86+
---------------------------------------------
M$ Windowz XP

```
You'll have to change **default 1** to **default 5**. This is the default if you're just dual-booting Ubuntu and XP.

---

### Post by derekr44 on 2007-05-25
I'll give this a try when I get home.  Thanks!

---

