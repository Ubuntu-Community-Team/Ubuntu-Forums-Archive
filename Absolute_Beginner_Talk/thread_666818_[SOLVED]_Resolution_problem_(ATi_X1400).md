---
title: "[SOLVED] Resolution problem (ATi X1400)"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by yatesl on 2008-01-13
Sorry if this has been asked a million times already, I've looked through topics and couldn't find an answer.

I have a Dell Inspiron 6400 laptop, with an ATi X1400 graphics card.  I've followed some instructions (enabled restricted drivers etc.) and managed to get special desktop effects working ... however, I can't get my resolution above 640x480, yet my native resolution is 1200x800.

Could anyone point me in the right direction, before my eyes start bleeding?   

Thanks in advance.

---

### Post by nikoPSK on 2008-01-13
So, in screen resolution it doesn't work? Was it always like this? If it wasn't do this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Regards,
nikoPSK

---

### Post by yatesl on 2008-01-13
Tried to fix it myself, Linux stopped working, had to reinstall. :tongue:  I'm on a fresh install now, and I'll say the exact steps that I've done.

System -> Administration -> Software Sources, and enabled Main, Universe, Restricted and Multiverse.
System -> Administraction -> Restricted Drivers Manager, and enabled ATI accelerated graphics driver.

However, I've yet to restart.  At the minute, I have three resolution options -- 640, 800, and 1024.  However, as I said, my laptop can go to 1024x800.  I fear that, when I restart my laptop (therefore finalising the driver install or whatever), I'm going to be kicked back to 640x480, and the other two options will be ... Well, gone.

I'll update this post in a minute, when I've done it.


Edit:  Oh Lord, it actually worked!  Ignore this thread now!

---

### Post by nikoPSK on 2008-01-13
> **yatesl said:**
> Tried to fix it myself, Linux stopped working, had to reinstall. :tongue:  I'm on a fresh install now, and I'll say the exact steps that I've done.

System -> Administration -> Software Sources, and enabled Main, Universe, Restricted and Multiverse.
System -> Administraction -> Restricted Drivers Manager, and enabled ATI accelerated graphics driver.

However, I've yet to restart.  At the minute, I have three resolution options -- 640, 800, and 1024.  However, as I said, my laptop can go to 1024x800.  I fear that, when I restart my laptop (therefore finalising the driver install or whatever), I'm going to be kicked back to 640x480, and the other two options will be ... Well, gone.

I'll update this post in a minute, when I've done it.


Edit:  Oh Lord, it actually worked!  Ignore this thread now!

Glad to see you got it working :)! Please mark this thread as "SOLVED".

Regards,
nikoPSK

---

