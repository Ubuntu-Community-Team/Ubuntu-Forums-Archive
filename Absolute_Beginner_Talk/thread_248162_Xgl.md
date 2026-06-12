---
title: "Xgl"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-08-31
Hey all,
I want to install XGL on my system to try it but I don't have an add in Graphics card. I have a built in 64mb one. will this be enough? is it even possible to use XGL with it?

Thanks for all the help.

---

### Post by TFX360 on 2006-08-31
Could be I will check for you. Just a sec. I need the complete name of your card. Try:

```
sudo lspci
```

And paste the result here...

---

### Post by PPAAUULL on 2006-08-31
I have an Integrated Intel® Extreme Graphics 2 card. Can I use XGL and have it run smoothly or even run for that matter?

---

### Post by PPAAUULL on 2006-08-31
I think I have found a sweet site that will allow me to get XGL without all the bugs and with less RAM. if anyone wants the site here you go. [AIGLX]("http://jaganath.wordpress.com/2006/06/25/ubuntu-install-log-4-awesome-graphics-on-the-linux-desktop-using-aiglx-and-compiz-better-than-vista-and-os-x/")

---

### Post by ronmarley1 on 2006-08-31
> **PPAAUULL said:**
> I have an Integrated Intel® Extreme Graphics 2 card. Can I use XGL and have it run smoothly or even run for that matter?
You may have issues with XGL on Intel integrated.  I tried that first and could not get it to work.  I tried AIGLX (see the post above) on an Intel 855GM (using the 810 driver) 32 Mb card on a R51 ThinkPad and it runs great!  Good luck, and be patient.  You may need to tweak a few things, but it's definately worth the effort!  This How-To helped me: [http://ubuntuforums.org/showthread.php?t=244559](http://ubuntuforums.org/showthread.php?t=244559)

---

### Post by TFX360 on 2006-08-31
With 64 mb should run smooth. Have a lot of patients and take care of your OpenGL first. If that is up and running via the drivers only then start installing Xgl/Compiz/Quinn/CGWD.

---

