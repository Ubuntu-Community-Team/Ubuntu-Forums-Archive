---
title: "Where can I get my graphics card driver for download?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-26
I got an ATI Radeon Xpress 200m:popcorn:

---

### Post by logos34 on 2007-12-26
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by spiderbatdad on 2007-12-26
the screenshot below shows your driver, i think. But rendering for composite windows is another issue. xserver-xgl may not work with that driver, idk. I've seen results using aiglx, but you might have to get that from source.

---

### Post by spiderbatdad on 2007-12-26
have you ever tried just installing xserver-xgl in synaptic, closing synaptic, opening a terminal and entering```
compiz --replace
``` then rebooting and going to Preferences>>Appearance>>Visual Effects>>Custom.

That should work, assuming you have emerald and are using an emerald theme for your windows manger. I don not know if this will work with fglrx driver above. I would try it without that driver.  BTW you have to have compizconfig-settings-manager too.

---

### Post by hilariousness16 on 2007-12-26
ty vm

---

