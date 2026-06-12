---
title: "Video Card Help"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by boredcollegekid89 on 2007-11-12
All right I have a Nvidia Quadro NVS 110M on my laptop and when I attempt to run desktop effects it tells me I need drivers and that desktop effects can't work. I went to Nvidia's site and find I have the most up to date drivers. My friend told me I need the linux drivers, but failed to mention where I could find them. 

If I do need linux drivers, where do i get them, and after I install them will my video card still work in Windows? Because I am dual booting Ubuntu and XP.

Thanks

---

### Post by drunkardivan on 2007-11-12
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

This fixes the video drivers by figuring out what you have installed and what you need to
drive it. Then it goes and gets what you need, and installs it for you.

---

### Post by alienexplorers on 2007-11-12
After running the nvidia scripts in drunkardivan's post, use > gksudo nvidia-settings to set your resolution and refresh rate.

---

### Post by Duck2006 on 2007-11-12
> **boredcollegekid89 said:**
> If I do need linux drivers, where do i get them, and after I install them will my video card still work in Windows? Because I am dual booting Ubuntu and XP.

Thanks

Then your in ubuntu windoze has not one thing to do with linux, you load drivers for linux and they sit on the linux partition. When you load windoze drivers they sit on the windoze partition.

---

