---
title: "FreeBSD x11 mouse problems"
date: 2008-09-28
forum: BSD
---

### Post by yahn on 2008-09-28
I realize this may not be the best place to ask questions about FreeBSD.  However, the Ubuntu community has been so helpful to me and there is no large BSD community that I am aware of, so I come here.

I did a standard FreeBSD installation that included x11.  I then did pkg_add -r xfce4.  When I do /usr/local/bin/startxfce4, the mouse is not being recognized.  However, when I configure the x11, the mouse appears to be working fine.

I have a wireless mouse manufactured by Microsoft.  I don't know how relevant that is.

Thank you.

---

### Post by cardinals_fan on 2008-09-28
That's odd.  It always worked fine for me.

---

### Post by Bachstelze on 2008-09-29
Have you done your X configuration properly? There are several ways to do it, but what I do is (as root):

```
cd /root
X -configure
```

It will generate a sample X config file in the current dir called xorg.conf.new. Try it out:

```
X -config /root/xorg.conf.new
```

In most cases, it will work fine so you can move it to the default place:

```
mv xorg.conf.new /etc/X11/xorg.conf
```

You might then need to tweak a few details, but it usually makes a usable configuration if you don't have very exotic hardware.

---

### Post by yahn on 2008-09-29
I forgot to move xorg.conf.new.  Thank you.

---

