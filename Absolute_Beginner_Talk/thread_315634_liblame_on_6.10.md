---
title: "liblame on 6.10"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by n3ldan on 2006-12-09
So I just install 6.10, and so far I hate it.  It seems to be lacking many packages.  I'm trying to use audacity, I need libmp3lame.so, so I need to install liblame-dev, and I can't find a package for it that works in 6.10.

Help is appreciated :confused:

---

### Post by sailor2001 on 2006-12-09
iblame-dev is listed in synaptics

---

### Post by n3ldan on 2006-12-09
I forgot to add multiverse to /etc/apt/sources.list

Now it installs fine, and the other packages I couldn't find before are there too :D

---

### Post by gboursiquot on 2006-12-11
> **sailor2001 said:**
> iblame-dev is listed in synaptics

What is synaptics?

---

### Post by PriceChild on 2006-12-11
liblame-dev is development headers... you don't need them.

Just **liblame_0_**

---

