---
title: "Refresh Rates Keep Changing"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by geekcliff on 2007-11-01
Anyone know how to make the refresh rate stay at what you set it on, i can get 144 but when i restart my pc its back on 50, had the same problem in fiesty and never cured it, i thought the new ui in gutsy was gona sort this out.:lolflag:

---

### Post by alienexplorers on 2007-11-01
You could try adding a modeline to the monitor section of your xorg.conf file.  A modeline generator can be found here:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

If you are running a nvidia card you could try:
> gksudo nvidia-settings

---

### Post by geekcliff on 2007-11-05
# 1024x768 @ 128.00 Hz (GTF) hsync: 105.86 kHz; pclk: 149.05 MHz
  Modeline "1024x768_128.00"  149.05  1024 1104 1216 1408  768 769 772 827  -HSync +Vsync
---------------------------------------------------------------------
Ok, So this is my mode line, how do i add it to xorg.conf, when i say how i realy mean where.:lolflag:

PS I Was wrong when i said 144 in the first post, as i since found out thats too high.

---

### Post by geekcliff on 2007-11-06
Its ok, ive worked it out, the mode line has fixed my problem, my linux now runs exactly the same refresh rate as my XP and is now still correct when i boot up, i think you just have to ignore the two built in tools for screen size and refresh, and just use the nvidia one.:guitar:

---

