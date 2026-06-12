---
title: "[SOLVED] Refresh rate moniter problem in Gusty"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by mmccaule on 2008-01-11
When I tried to change the refresh rate of my monitor in Gusty I noticed that the monitor said "custom" and the only choice was 60 hertz. So I changed the monitor from custom to ViewSonic P775 which is what I have. Now When I boot the system tells me that it is in low graphics mode because my screen and graphics card could not be correctly be identified and to configure it manually. When I try that it detects the ViewSonic but the only resolution I can choose is 800x600 at 85 hertz which is low resolution. My graphics are an onboard Trident Video Accelerator Blade 3D/ProMedia. I would be happy to just get back to the "custom" settings I had to start with. How can I do this without doing a reinstall?

---

### Post by Tteddo on 2008-01-11
Try to reconfigure X. do <CTRL><ALT>F1 and then execute the command:
> sudo /etc/init.d/gdm stop
To stop gdm, now you can reconfigure the X server. Do the following:
> sudo dpkg-reconfigure -phigh xserver-xorg
When that is done, then type:
> sudo /etc/init.d/gdm start

Let me know what happens. In my experience with the 4 Ubuntu machines I have here the 
Screen and Graphics tool in Administration causes alot of chaos when you try to change monitors with it. My guess is that if the monitor section doesn't exactly match what the tool changes it to, then you get the problem you have.

---

### Post by mmccaule on 2008-01-11
Tteddo,

Thanks for the info. but I'm afraid to try it since I think I have my problem solved. I went back into Screens and Graphics and choose the Generic 1024x768 Monitor. I can now choose different resolutions and refresh rates. I may have asked for help to quick after only spending a couple of hours on this. Anyhow, thanks for your help!

---

### Post by Tteddo on 2008-01-11
Ok! It's no problem!
Can you mark this thread as solved under thread tools? Other people can benefit from what you did then!
Thanks!

---

