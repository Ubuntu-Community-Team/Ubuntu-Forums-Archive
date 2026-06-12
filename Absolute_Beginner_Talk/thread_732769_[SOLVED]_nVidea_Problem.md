---
title: "[SOLVED] nVidea Problem"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by yizuman on 2008-03-23
I just tried using the restricted drivers for my Geforce 2 integrated chipset and it caused my system to lock up, so I had to use the recovery mode to get back on.

I tried the Legacy driver and it doesn't work.

Apparently Ubuntu hates my chipset. It works fine under Windows XP, but not on Ubuntu 8.04 Beta (i recently upgraded from 7.10 to see if the problem got resolved. Still the same problem.)

Any ideas?

---

### Post by hhhhhx on 2008-03-23
try installing through envy

---

### Post by yizuman on 2008-03-23
I did and it still locked up the system. :-/

---

### Post by yizuman on 2008-03-23
I went to the nVidia forum

[http://forums.nvidia.com/index.php?showtopic=62921](http://forums.nvidia.com/index.php?showtopic=62921)

So far, no response yet, but someone may have an idea why I am having an error from my last post on there.

Suggestions??

---

### Post by overdrank on 2008-03-23
> **yizuman said:**
> I just tried using the restricted drivers for my Geforce 2 integrated chipset and it caused my system to lock up, so I had to use the recovery mode to get back on.

I tried the Legacy driver and it doesn't work.

Apparently Ubuntu hates my chipset. It works fine under Windows XP, but not on Ubuntu 8.04 Beta (i recently upgraded from 7.10 to see if the problem got resolved. Still the same problem.)

Any ideas?

Hi and I have had some troubles with the nvidia drivers on my integrated graphics, how much memory is shared with the graphics?

---

### Post by smartboyathome on 2008-03-23
By the way, this should be posted in the hardy herron development forum, not here.

Anyway, try using Envy to install the drivers and see if that helps.

---

### Post by yizuman on 2008-03-23
> **overdrank said:**
> Hi and I have had some troubles with the nvidia drivers on my integrated graphics, how much memory is shared with the graphics?

>   	Integrated NVIDIA® GeForce2™ Graphics with up to 32MB shared system memory:

    * 64-bit hardware-accelerated 3D graphics
    * Compaq DVD Player/Navigator
    * Video Player (AVI, MPEG2 and others)
    * Maximum non-interlaced resolution of up to 1920 x 1440 @ 75Hz (when supported by monitor)


That help any?

---

### Post by yizuman on 2008-03-23
> **smartboyathome said:**
> By the way, this should be posted in the hardy herron development forum, not here.

Anyway, try using Envy to install the drivers and see if that helps.

Oops, well, if a Mod sees this post, please feel free to have it moved.

Like I said in my earlier post, Envy still locked up my system when I used it during 7.10 before I upgraded to 8.04.

I'll try it again, but I bet the result will be the same, a lock up in my system.

---

### Post by smartboyathome on 2008-03-23
It shouldn't, 7.10 uses the Legacy version, it was rewritten for 8.04.

---

### Post by yizuman on 2008-03-24
> **smartboyathome said:**
> It shouldn't, 7.10 uses the Legacy version, it was rewritten for 8.04.

Ok it worked this time, using a newer version of Envy geared for the Heron version.

Worked just fine.

Problem is when I tried to use the "Desktop Effect" it uninstalled my Legacy driver for some reason. So I'm not gonna bother that "Desktop Effect" again, unless there's a way to prevent it from uninstalling it.

Thanks again.

---

