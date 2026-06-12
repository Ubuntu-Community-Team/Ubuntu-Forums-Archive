---
title: "Little refresh rate problem..."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by orange2k on 2007-07-10
I mostly work in 1280x1024 resolution, with refresh rate of 85Hz and thats fine.
But when I work in 1152x864 resolution, I would like the refresh rate to be 100Hz, because my monitor supports it (works without flaw in Windows) - but I cannot select this refresh rate.
Can I modify the xorg.conf file in some way to get this working?

---

### Post by Alexander2007 on 2007-08-02
> **orange2k said:**
> I mostly work in 1280x1024 resolution, with refresh rate of 85Hz and thats fine.
But when I work in 1152x864 resolution, I would like the refresh rate to be 100Hz, because my monitor supports it (works without flaw in Windows) - but I cannot select this refresh rate.
Can I modify the xorg.conf file in some way to get this working?

Open a terminal window, type: "sudo gedit /etc/X11/xorg.conf" 
Press "Enter"
Enter your password and hit "Enter" again
You will now see the configuration file. 
Look for | Section "Monitor" | and where you see "HorizSync" and "VertRefresh", replace them with the corresponding values in your monitors manual.
After you are done, Hit "Save", close the window and restart your computer. 
Try selecting your resolution now. :)

---

