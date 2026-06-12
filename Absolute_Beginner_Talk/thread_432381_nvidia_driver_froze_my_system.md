---
title: "nvidia driver froze my system"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2007-05-03
I just installed Fiesty and everything was working well until I installed the nvidia driver. I have a GeForce MX 4000. Now when I boot the computer it freezes at the login screen. Is there anyway to disable the driver before the login screen?

---

### Post by nanotube on 2007-05-04
> **rubrboots said:**
> I just installed Fiesty and everything was working well until I installed the nvidia driver. I have a GeForce MX 4000. Now when I boot the computer it freezes at the login screen. Is there anyway to disable the driver before the login screen?

run in recovery mode (select that from grub), then edit your /etc/X11/xorg.conf to use the "nv" driver instead of "nvidia". (back up the xorg.conf first)
then reboot...

---

### Post by rubrboots on 2007-05-04
Thanks nanotube, I did as you said and I can now login again. But when I try and enable desktop effects it says that I must enable the nvidia driver. If I enable the driver as it suggests the same problem happens and I cant login. How can I install a driver that will allow me to use my video card for things like desktop effects and still be able to login?

---

### Post by nanotube on 2007-05-04
well, since the nvidia driver has problems with your hardware, and since desktop effects require it, you just have to live without desktop effects for the time being.
or you could search around on google for your video card and nvidia driver... maybe you find a fix...

---

