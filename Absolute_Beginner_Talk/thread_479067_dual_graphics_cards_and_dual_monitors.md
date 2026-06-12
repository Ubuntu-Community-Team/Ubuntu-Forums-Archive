---
title: "dual graphics cards and dual monitors"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by dfjcms86 on 2007-06-19
i have two nvidia  6800 gcs and i have two monitors 
i am sorry of this question but i have to ask
i have searched and searched and can not find any posts about how to configure this i have one monitor plugged in to one gc and the other monitor in the other gc 
please in a step by step process guide me through how to configure this i am sry
right now my os is only seeing one gc and one monitor
thanks
i am running Ubuntu 7 64bit
thanks

---

### Post by charles.g.moore on 2007-06-19
Im not sure about the two vid cards but I have a dual monitor setup using a single nvidia card (el cheapo) one monitor is plugged into the DVI and the other in the VGA port.

I used a native nvidia deal called TWINVIEW.

Hopefully this helps...

If you see that you may use twinview I can send you all the posts i used to configure mine when I get home...

I figure the reason you are only seeing one monitor is because you have to tell the Xserver tht you have two monitors and there should be two instances of their configurations in the xorg.conf

---

### Post by dfjcms86 on 2007-06-20
thanks that worked great

---

### Post by charles.g.moore on 2007-06-20
> **dfjcms86 said:**
> thanks that worked great

Glad to help!!!

---

