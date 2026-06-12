---
title: "What does VGA= do as a bootloader option?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by warbread on 2006-11-05
I'm a curious soul, and recently saw vga=771 used as a kernel boot option to get linux installing.  What does that option actually do?  Also, if anyone can give me a resource that describes what other such options do, that'd be great.

---

### Post by DanSchnell on 2006-11-05
This should give you a little help:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Eversmann on 2006-11-05
> **warbread said:**
> I'm a curious soul, and recently saw vga=771 used as a kernel boot option to get linux installing.  What does that option actually do?  Also, if anyone can give me a resource that describes what other such options do, that'd be great.

AFAIK, it changes the video mode on the boot splash screen.

Can't help more about this, sorry.

---

### Post by warbread on 2006-11-05
> **DanSchnell said:**
> This should give you a little help:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thank you, that's useful, but not what I'm looking for.  I know that it does work and when to use it, but I don't have an understanding of what it actually does.  I think it's something to do with a number of display lines, but that's fuzzy to me.

---

### Post by steve.horsley on 2006-11-05
It sets the VGA mode that the colsole will use. This includes both resolution and colour depth. I don't have a full table of VGA modes, but I found this page that lists some:
[http://www.digitalhermit.com/linux/hiresconsole.html](http://www.digitalhermit.com/linux/hiresconsole.html)

It seems you can also do **vga=ask** which might be interesting.

---

### Post by warbread on 2006-11-05
Thanks, I appreciate the link.

---

