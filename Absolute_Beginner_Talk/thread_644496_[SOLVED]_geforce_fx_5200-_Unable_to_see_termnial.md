---
title: "[SOLVED] geforce fx 5200- Unable to see termnial"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by ghoran on 2007-12-18
Ubuntu 7.10
From synaptic package manager chose and applied nvidia-glx
All is working great except when I put up a terminal it is all white with no command prompt.
I can go out to other's without a problem ctrl-alt-F2 for example

---

### Post by overdrank on 2007-12-19
> **ghoran said:**
> Ubuntu 7.10
From synaptic package manager chose and applied nvidia-glx
All is working great except when I put up a terminal it is all white with no command prompt.
I can go out to other's without a problem ctrl-alt-F2 for example

HI and could you post the output of this command in the terminal ```
cat /etc/X11/xorg.cong
``` and maybe we can help.

---

### Post by bumanie on 2007-12-19
The same happened to me following nvidia card install. I think this is how I fixed it. 
Push CTRL - ALT - F1 together, this gets you into a console. After putting in username and password when prompted, type the following command 
sudo nvidia-xconfig --add-argb-glx-visuals -d 24 --> enter
reboot --> enter

---

### Post by ghoran on 2007-12-19
This worked perfectly!!!!!
Thanks bumanie
and thanks overdrank for looking to help

I LOVE THIS FORUM!!!!

I did this:
> 
Push CTRL - ALT - F! together, this gets you into a console. After putting in username and password when prompted, type the following command
sudo nvidia-xconfig --add-argb-glx-visuals -d 24 --> enter
reboot --> enter

This added the following
Option         "AddARGBGLXVisuals" "True"
to /etc/X11/xorg.conf

---

