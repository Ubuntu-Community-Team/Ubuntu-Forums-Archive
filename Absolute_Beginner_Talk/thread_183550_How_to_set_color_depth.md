---
title: "How to set color depth?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-05-28
Hi,

How do I set/check the color depth?

Thanks.

---

### Post by popkid on 2006-05-28
[QUOTE=u.b.u.n.t.u]Hi,

How do I set/check the color depth?

Thanks.[/QUOTE]

You can set it by entering:

sudo dpkg-reconfigure xserver-xorg

in a terminal window, its about the last configuration setting that comes up from memory


also if you type in

xwininfo

then click in a window on screen, the "depth" value is colour depth

pK

---

### Post by u.b.u.n.t.u on 2006-05-28
Thanks popkid,

is there a GUI way of doing this?

---

