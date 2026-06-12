---
title: "Slow Video on Laptop for Google Earth, etc."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by rtower on 2007-01-14
When I started Google Earth, it said it could not find video card, that is would be using software emulation. This is an HP Pavilion ze2000 laptop. The video was very slow. The video for the chess program was also very slow.

Could it be that my laptop does not really have a true video card and is using software emulation? No video card shows up in Device Manager.

Is there anything I can do to speed up the graphics? Google Earth under Windows XP on the same machine works fine.

Thanks.

---

### Post by jd65pl on 2007-01-14
You can check if you have hardware 3D rendering by doing

```
glxinfo | grep direct
```

If you don't have a graphics card then there isn't much you can do, you could check you are using the correct driver for your chipset.

---

### Post by mikewhatever on 2007-01-14
I had to add/install GLX support on my HP DV5000. Having Nvidia card I did ```
sudo apt-get install nvidia-glx
```
and got direct graphic rendering. What's you video card by the way?

---

### Post by Albi on 2007-01-14
Type lspci to find out ur graphics card (post the results here if u cant figure it out)

---

### Post by rtower on 2007-01-14
Thanks for the replies.

Here is the additional information:

ron@ron-laptop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
ron@ron-laptop:~$ 
ron@ron-laptop:~$ lspci

<snip>

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

<snip>

---

### Post by rtower on 2007-01-14
All,

I did a search for the graphics card you helped me find, and found a how to for the driver and that worked. Google Earth and the chess program now work fine.

Thanks.

---

