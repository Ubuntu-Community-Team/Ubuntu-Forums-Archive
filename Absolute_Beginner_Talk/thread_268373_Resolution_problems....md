---
title: "Resolution problems..."
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by BuRn_sLuG on 2006-09-30
Hey guys,

Yesterday I posted a thread here, asking a few questions about uBuntu, before I installed it. I have successfully installed it, and I am loving it :-D . 

However, when I was running Windows XP Pro, I could have my monitor resolution at 1280 x 1024 (which is it's native resolution), BUT in Ubuntu, I can only have it at 1024 x 768 MAX (with 640 x 480 and 800 x 600 also available).

I have installed the latest nVidia drivers from the guide [http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
 , and restarted after doing so (I can see an nVidia splash screen right before the login window now, which I presume is good). But the drivers still won't let me put the resolution up.

If anyone could point me in the right direction I'd appreciate it, you guys are really fast at replying too :mrgreen:  and will know a lot more about Linux than me ](*,) .

Cheers

Brendan

---

### Post by jordanmthomas on 2006-09-30
Open up a terminal
type
```
gksu gedit /etc/X11/xorg.cong
```
Find the section with the resolutions, and add this to each of them
```
"1280x1024"
```
so it would be like
```
"1280x1024" "1024x768" "800x600"
```
Save it and close gedit
Restart X
<Ctrl><Shift><Backspace>

---

### Post by BuRn_sLuG on 2006-09-30
Cheers man it worked. :mrgreen:

---

