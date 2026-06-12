---
title: "Ubuntu 7.10 boot up problems"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2007-10-18
Installed, went fine and loaded up. So Ubuntu tells me I need the graphics drivers for my card, yeah I knew that so I installed them. So I installed them and rebooted and now all I get is a black screen after the Ubuntu logo/loading screen. I'm guessing it's something to do with X but I'm not sure what to do now :(. 

Thanks

---

### Post by LowSky on 2007-10-18
start ubuntu in safe mode (hit ESC on startup)
then type this at prompt
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Rackerz on 2007-10-18
Unfortunately that just gave me worse troubles, I rebooted and re-installed Ubuntu and now the same thing is happening again. 

However, booting into windows and changing the xorg.conf manually there I managed to get Ubuntu going again. I had to change "fglrx" back to "vesa" to get Ubuntu to boot properly. 

What can I do to get fglrx working? I installed Ubuntu back on my computer for the simplicity of being able to do that.

---

### Post by Rackerz on 2007-10-18
Nobody?

---

### Post by Rackerz on 2007-10-18
If anyone had been following this post, I just simply had to blacklist the old fglrx driver.

---

