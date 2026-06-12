---
title: "screen resolution/color depth problem"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Yubeh on 2006-07-02
This is the first time i am trying linux, so im a total newbie.
My configuration: P4 2ghz, 512ram, ge6600gt agp, dualboot with winxp
I downloaded the desktop .iso, checked it with the md5 thing, burned, checked again - so the cd is 100% ok. So i ran the preview cd, but the screen went weird, with green lines etc.. like when the monitor cant handle the resolution or something... i rebooted and i found out the only working mode was 1024x768x32. everything else in the list give the weird screen. (my monitor is a few years old, but should handle everything up to 1600x1200).
I then installed ubuntu (6.06 ofc), rebooted and boom, again that weird screen. The logo with the loading stuff under it works, it just has some really low resolution, like 640x480, but it goes wrong when the desktop (gnome?) is supposed to load. 
I tried everything i could with the dpkg-reconfigure xserver-xorg, but nothing helped. I tried to select only the 1024x768 resolution, with 24 bits (=truecolor?), i entered the right horizsync and refresh rate, but nothing. Should the loading screen have that low resolution, even if I selected 1024x768 before? When i select 1024x738x32  in the livecd, it gets applied to the loading screen.

---

### Post by u.b.u.n.t.u on 2006-07-02
What is your graphics card? Are you able test a different graphics and monitor?

---

### Post by Dr. Nick on 2006-07-02
in the dpkg-xorg did you ever try out the vesa driver?

---

