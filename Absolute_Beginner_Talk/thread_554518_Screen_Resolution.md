---
title: "Screen Resolution"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-09-19
I just got my drivers updated with Restricted Drivers help, which I have a nvidia card. When I restarted, m resolution went down to 800x600. I want it to be 1024x768 but I dont have that option.

Please help...


Phiz.

---

### Post by alienexplorers on 2007-09-19
why don't you run:
> gksudo nvidia-settings
to set your display resolution.

---

### Post by phizikal on 2007-09-19
Ok, It asked for a password prompt then nothing loaded up.

I tried it again, and nothing.

I also tried alt+F2, and it said "Could not open location 'file:///nvidia-settings'".

---

### Post by alienexplorers on 2007-09-19
This could mean your drivers for your video card are incorrectly installed.  Try using the ENVY script that is show in my sig line.  You will have to first run ENVY to unload/remove your current drivers.  When done run ENVY again installing the new drivers.

reboot your sysytem.
now try running sudo nvidia-settings

---

### Post by phizikal on 2007-09-19
You got a error.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)

---

### Post by alienexplorers on 2007-09-19
My script to link to envy is working fine.

---

### Post by phizikal on 2007-09-19
"Internal Server Error
The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [email]support@supportwebsite.com[/email] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log."


Have a alternative?

---

### Post by ravenwere on 2007-09-19
The link is to a package try right click save as... or right click actions download or if all else fails .......
go to the website [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and find the link to download.

---

### Post by phizikal on 2007-09-19
Yay, I got NVIDIA corectly working..

But my resolution is still off.....

=/

---

### Post by ravenwere on 2007-09-19
> **alienexplorers said:**
> why don't you run:
sudo nvidia-settings
to set your display resolution.

What happened when you ran the above? Did you get the resolution options you wanted?

---

