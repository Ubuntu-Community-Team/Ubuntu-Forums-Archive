---
title: "[SOLVED] Ubuntu and PS3"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-09-25
So I installed Ubuntu on my PS3 and it seemed to work fine, except for the resolution. I fully updated it but I still only have one choice for resolution and refresh rate. It is something really small like 3**x2**, a resolution size I hadn't even heard of before and the refresh rate is 30 Hz. Does anyone know of how to get more resolutions?

---

### Post by Hospadar on 2007-09-25
You can run ubuntu on a ps3? Awesome.

uh, but what you probably need to is edit your xorg.config file.  If you know how to do it manually (or do enough googling to figure out how without making everything blow up) it's located at /etc/X11/xorg.conf  probably a safer choice would be to run ```
sudo dpkg-reconfigure xserver-xorg
```  there will be a bunch of choices you can probably skip right through, and there will be a page with a bunch of resolutions to select with the space bar, pick all the ones you want to appear.  Also from this dialog you can change the refresh rates.

---

### Post by slughappy1 on 2007-09-27
Damn. I was hoping not to have to deal with that. But thanks, I did kind of forget about that command

---

