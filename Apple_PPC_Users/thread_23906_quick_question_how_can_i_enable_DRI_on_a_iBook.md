---
title: "quick question: how can i enable DRI on a iBook?"
date: 2005-04-04
forum: Apple PPC Users
---

### Post by revs on 2005-04-04
Just checked and DRI (Direct Rendering) is not enabled on my iBook (500Mhz), how do i enable it?

Cheers!

---

### Post by callipeo on 2005-04-05
As long as direct rendering is supported for your card, you can do "sudo dpkg-reconfigure xserver-xorg" and tell it to load the "dri" module.

---

