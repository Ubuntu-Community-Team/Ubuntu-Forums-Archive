---
title: "Blank Screen"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Bengaul on 2005-10-06
Hi,

After going through the ubantu install, I arrive at a blank screen. no sound, nothing! It goes through the process of loading, but no desktop! 

Could it be something to do with selecting a too high res at the install?:confused: 

Please help.

P4 3.0, 1GB RAM, 80GB HDD.

---

### Post by Ampersand on 2005-10-06
Try pressing Ctrl, Alt and F1. This should bring you to a terminal. Log in here, and type 'sudo /etc/init.d/gdm restart', entering the same password that you used to log in when prompted. Do you get any error messages?

---

### Post by Bengaul on 2005-10-06
Thanks, I tried the above, and it goes to a blank screen again. So I do ctrl, alt, F1, and there have been no error messages.

---

### Post by Ampersand on 2005-10-06
Try pressing Ctrl, Alt and +. This will cycle through the available resolutions. If it remains blank, go back to the terminal by pressing Ctrl, Alt and F1, log in again and run 'sudo dpkg-reconfigure xserver-xorg'. Iit might be useful if you make a note of your graphics card and monitor settings before doing this (if you have a Windows installation you can use to check them).

---

### Post by Bengaul on 2005-10-07
Ahhhh! Thank you. I pressed ctr, alt, + and voila! Many thanks!

Ben.

---

### Post by Bengaul on 2005-10-07
Following on from this thread, the problem I am now having is that ubuntu is still defaulting to the high res each boot. Is there any way to set it to start at a lower res?

Many thanks,

Ben.

---

### Post by Ampersand on 2005-10-07
You can either run 'sudo dpkg-reconfigure xserver-xorg' from a terminal, this will allow you to set up your keyboard, mouse and video with the correct settings.

You can also run 'sudo gedit /etc/x11/xorg.conf', scroll down to the part with the hearding 'Section "Screen"' and remove the resolutions that don't work on your monitor.

Finally, you could go to the System menu, then under Preferences you'll find 'Screen Resolution'. Make sure that a resolution that works is set as the default.

---

