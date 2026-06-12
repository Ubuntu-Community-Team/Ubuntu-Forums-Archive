---
title: "Problems with blender interface in Jaunty"
date: 2010-01-07
forum: Art &amp; Design
---

### Post by mike255 on 2010-01-07
Hello.
I've just installed blender 2.49b on Ubuntu 9.04. The main window works, 3d, textures too. But when I try to access menus, they're not visible, or visible with some bugs. Please help.
There is screenshot:
[http://img41.imageshack.us/img41/1959/screenshotqp.png](http://img41.imageshack.us/img41/1959/screenshotqp.png)
Video card (ATI HD3200) driver is installed.
*Thanks in advance*.
P.S.: Sorry for my bad English...

---

### Post by Exodist on 2010-01-07
Are you running Compiz Fusion? If so disable it.

---

### Post by mike255 on 2010-01-07
Thanks, it works! :)

---

### Post by Exodist on 2010-01-08
> **mike255 said:**
> Thanks, it works! :)
Kewl, not sure why it causes such conflict. I had the same issues trying to run it under Jaunty as well with Compiz.

---

### Post by Labello on 2010-01-09
> **Exodist said:**
> Kewl, not sure why it causes such conflict. I had the same issues trying to run it under Jaunty as well with Compiz.

yeah and it's still the same with karmic.

disabling compositing does the trick for me too. but it is the same with xcompmgr and compiz. and what bothers me most is, that it's still the same with blender 2.5....

---

### Post by mike255 on 2010-01-09
> **Exodist said:**
> Kewl, not sure why it causes such conflict. I had the same issues trying to run it under Jaunty as well with Compiz.
I had blender running on other computer (with Jaunty and compiz enabled), it worked without these interface bugs...Maybe there are some hardware dependencies?...

---

### Post by Exodist on 2010-01-09
> **mike255 said:**
> I had blender running on other computer (with Jaunty and compiz enabled), it worked without these interface bugs...Maybe there are some hardware dependencies?...
It could be a mixture of issues. Compiz version, Kernel version, Xorg version, Hardware version and Blender version. My main 3 guess is Compiz -vs- Xorg -vs- hardware. Blender is just the collateral damage.
Also note that Blender is rock solid under Vista with Aero running..?

---

### Post by hessiess on 2010-01-09
Blender has historically had a lot of problems with ATI cards, they provide an incomplete OpenGL implementation and Blender makes extensive use of `uncommon' OGL features.

---

### Post by Exodist on 2010-01-10
> **hessiess said:**
> Blender has historically had a lot of problems with ATI cards, they provide an incomplete OpenGL implementation and Blender makes extensive use of `uncommon' OGL features.
I have never had any issues with Blender using ATI cards on both Linux and Windows. Only issues I ever experience was when Compiz fusion was running.

---

### Post by mike255 on 2010-01-10
> **Exodist said:**
> It could be a mixture of issues. Compiz version, Kernel version, Xorg version, Hardware version and Blender version. My main 3 guess is Compiz -vs- Xorg -vs- hardware. Blender is just the collateral damage.
Also note that Blender is rock solid under Vista with Aero running..?
I've seen this bug on Google somewhere... Will try searching again later... As I remember, it's about some library/libraries related to Xorg...
Don't know about Vista, didn't use it...

---

### Post by mike255 on 2010-01-10
> **hessiess said:**
> Blender has historically had a lot of problems with ATI cards, they provide an incomplete OpenGL implementation and Blender makes extensive use of `uncommon' OGL features.
Maybe...But I've never noticed problems related straight to video-card, only this bug with compiz and some troubles with drivers...

---

