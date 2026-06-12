---
title: "Trouble With Screensavers"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-28
Hello, after installing Ubuntu on my main desktop PC I am taking time to configure it (with the forums help). Anyway, when I select any 3D screensaver in the screensaver preferences box and preview it, it plays for about 1.5 seconds an then stops or freezes. 2D screensavers (such as 'Floating Ubuntu') also play with a low frame rate. I suspect it has something to do with my graphics card drivers so here are the details.

ATi RADEON X600 256MB HyperMemory
1 GB RAM
Intel Pentium 4 3.00GHz

I haven't installed any special drivers for my graphics card, its just working from a default installation. Can anyone help me? Thanks.

---

### Post by emarkd on 2008-01-28
See if there are restricted drivers for your card by clicking on:

System > Administration > Restricted Drivers Manager

---

### Post by Crumpets and Jam on 2008-01-28
> **emarkd said:**
> See if there are restricted drivers for your card by clicking on:

System > Administration > Restricted Drivers Manager

Yes, there are but after I install these I can't enable the Compiz Fusion desktop effects. In a previous post, somebody suggested that I install the restricted drivers and then XGL. Would this solve these problems?

---

### Post by emarkd on 2008-01-28
Maybe. XGL is required for some ATI card, I think.  You could try installing xserver-xgl and see if it works, but know that it may break what you've already got going.  Make sure you've got a backup of your /etc/X11/xorg.conf file before you try it.

---

### Post by Crumpets and Jam on 2008-01-28
> **emarkd said:**
> Maybe. XGL is required for some ATI card, I think.  You could try installing xserver-xgl and see if it works, but know that it may break what you've already got going.  Make sure you've got a backup of your /etc/X11/xorg.conf file before you try it.

Could you explain what XGL is?

---

### Post by Crumpets and Jam on 2008-01-29
Could anyone confirm is this would work? Thanks.

---

