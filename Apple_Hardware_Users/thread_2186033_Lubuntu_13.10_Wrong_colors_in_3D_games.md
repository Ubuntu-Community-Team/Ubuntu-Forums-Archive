---
title: "Lubuntu 13.10: Wrong colors in 3D games"
date: 2013-11-05
forum: Apple Hardware Users
---

### Post by xeno74 on 2013-11-05
Hi there,

I've installed Lubuntu 13.10 succesfully. The 3D gfx acceleration and sound works. But I have wrong colors in gl games like SuperTuxKart, Neverball etc.. Is there a problem with Mesa for PowerPC?

Rgds,

Christian

---

### Post by rsavage on 2013-11-05
Hi Christian, I've not been involved with any of the recent releases, and I'm a bit out of the loop, but it used to be the case that there were some endian problems with mesa.  You may find using User Space Mode setting better (12.04 or Debian wheezy are the easiest for this).  Another thing you could try is using an environment that uses compositing (like Xubuntu); this has solved some colour problems with me under KMS (Kernel Mode Setting).

Adam

---

