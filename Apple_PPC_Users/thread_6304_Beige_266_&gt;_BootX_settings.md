---
title: "Beige 266 &gt; BootX settings"
date: 2004-11-27
forum: Apple PPC Users
---

### Post by xico on 2004-11-27
Hello,
Still trying to get in the first boot process, after 4 days!!
G3 beige minitower 266/640/2X4,5 (one of the HD dedicated to future Ubuntu).
My floppy drive is out of order.
My video card is :IMS tt3d
I intalled BootX, I reach the install screen with these settings:
 "video=imsttfb:vmode:16,cmode:32"
but the screen I get doesn't allow me to perform the boot: the boot display only shows half of itself at the bottom of the screen.

How can I manage this?

Thanks

Xico

---

### Post by xico on 2004-11-27
I got it!
It needs a space between arguments!!: 
"video=imsttfb:vmode:16,cmode:32"
becomes  "video=imsttfb: vmode:16, cmode:32" 

 :mad:

---

