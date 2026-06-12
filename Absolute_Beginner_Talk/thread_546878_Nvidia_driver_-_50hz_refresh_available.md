---
title: "Nvidia driver - 50hz refresh available?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by lamar_air on 2007-09-09
I have a Nvidia card in my pc and it's only allowing me to have 50hz refresh rate.  How can i change it to 75?

It seems to have recognized the card as nvidia.

---

### Post by toasterofirony on 2007-09-09
Have you installed the nVidia driver? If not, I would suggest downloading "[Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb")" and running that.

---

### Post by lamar_air on 2007-09-09
I installed envy and ran it for nvidia and it still only gives me the 50hz option.  Should I try editing the xorg.conf file to force it to 75hz?

Thanks

---

### Post by nonewmsgs on 2007-09-09
that's what i would do.

---

### Post by alienexplorers on 2007-09-09
Add a modeline to your monitor section in xorg.conf.......   I have a modeline maker in my signature line.......   Give it a try.

---

