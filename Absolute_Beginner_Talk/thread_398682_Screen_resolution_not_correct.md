---
title: "Screen resolution not correct"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-04-01
Hi guys,

I've just bought a ViewSonic VG930m monitor. Its screen resolution(as said on the box) should be 1280x1024@60hz.

At first it displayed fine under 1024x768, but if I changed it to the 1280x1024@60hz, it'd get a bit stretched...so I downloaded the nvidia drivers via envy(I hadn't done it before), and installed it, and reconfigured the xorg.conf.

After that, the problem still persisted. It worked fine at 1024x768, but if I switched to 1280x1024@60hz, the image would still be too big to fit on the screen...and if I tried 1280x1024@75hz(though I don't know why frequency(hz) would make a difference), it would look as though the whole picture was on the screen, the some bits of the side still got chopped off...and the words didn't look too good. :(

When I reconfigured the xorg with "dpkg-reconfigure xserver.xorg" it detected my monitor correctly (viewsonic VG930m), so I'm a little curious why I'm still having these problems.

Any ideas guys? :(

Cheers and thanks in advance.
Kinson

---

### Post by dmjones500 on 2007-04-01
After changing the resolution to 1280x1024, did you press any relevant buttons on your monitor to readjust it?

When I first used my current resolution with my monitor, I had to select it's auto-setup function so that it would resize its output and fit the whole desktop onto my screen....

---

### Post by Eduardo Serra on 2007-04-01
I have the same problem right now, and i think it's not a very common one. Look at what people has told me and maybe it will help you: [http://www.ubuntuforums.org/showthread.php?t=392803](http://www.ubuntuforums.org/showthread.php?t=392803)

---

### Post by kinson on 2007-04-01
> **dmjones500 said:**
> After changing the resolution to 1280x1024, did you press any relevant buttons on your monitor to readjust it?

When I first used my current resolution with my monitor, I had to select it's auto-setup function so that it would resize its output and fit the whole desktop onto my screen....


...... :oops: :oops: :oops: :oops: :oops: 

Thanks a lot man :) And for anybody who happens to be as stupid as me here( and happens to stumble upon this thread)...that worked :p I just needed to auto adjust it again.

Thanks man :)

Cheers,
Kinson

---

