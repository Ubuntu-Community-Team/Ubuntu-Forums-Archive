---
title: "Different Res at 16bit &amp; 24bit despite xorg.conf"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by lirael on 2006-12-07
I've noticed that I can't get higher resolutions (anything above 1024x768) while in 24bit mode regardless of what I have configured in "etc/X11/xorg.conf", but I can't use Firefox in 16bit because it'll crash when it encounters Flash files... I would really like to get a higher res than 1024x768 because I'm used to using 1600x1200 and the former resolution just looks huge in comparison. Is there anyway to fix this?

---

### Post by riven0 on 2006-12-07
> **lirael said:**
> I've noticed that I can't get higher resolutions (anything above 1024x768) while in 24bit mode regardless of what I have configured in "etc/X11/xorg.conf", but I can't use Firefox in 16bit because it'll crash when it encounters Flash files... I would really like to get a higher res than 1024x768 because I'm used to using 1600x1200 and the former resolution just looks huge in comparison. Is there anyway to fix this?

Have you installed the official drivers for your graphics card and then reconfigured the xserver?

---

### Post by lirael on 2006-12-07
I just installed the drivers (which took some research and work) but now everything works wonderfully, thanks!

---

