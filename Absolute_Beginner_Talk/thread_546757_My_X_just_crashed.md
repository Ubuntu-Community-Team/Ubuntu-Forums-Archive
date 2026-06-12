---
title: "My X just crashed"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by OskarB on 2007-09-09
Hello!

I was just doing my homework and installing som programs, no large ones. Only to be able to see the weather next to the clock and so. When the installations were ready the computer told me to reboot.. so I did... and now I cant log in.. I get the following Error:

Error: API mismatch: The NVIDIA kernel module has version 1.0-8762, but the x module has the version 1.0-9631. Please make sure that the kernel module and all NVIDIA driver components have the same version.

(EE) NIVIDIA(0)  Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for detailes.
***Aborting***
(EE) Screen(s) found but none have usable configuration
Fatal server Error: No screens found.

I have a Toshiba PORTÉGÉ laptop..

Please help me! I would really need to get that homework done by tomorrow...

Thanks a lot!!

//Oskar

---

### Post by Sef on 2007-09-09
What are your specs?

What version and type of *buntu are you using?

---

### Post by soma4me on 2007-09-09
OskarB,

Please do a search at forum home page with this string: "kernel update" +nvidia.   You'll see a lot of similar issues, some of them are resolved that may be matching your condition.

Hope this help.

---

### Post by OskarB on 2007-09-09
Ok.. I agree, I should have looked harder for a nother thread with the same issue...

Now I´ve finaly found out what I have to do... I´ll re install nvidia-glx and nvidia-kernel..

...but... 

to do that I need to be connected to the internet... and my internetconnection is a mobile usb-modem kind of modem and in order to use it I will have to run a file, in my case called Telia... And ones I´m running it I cant do anything else... Is it possible to run two tasks at the same time? in that cas how?

Thanks a lot!!

---

### Post by Diggs808 on 2007-09-10
My solution is this:

Log-in terminal 

cd /etc/X11

sudo Nano xorg.conf

under Device change the driver from "nvidia" to "nv"

Ctrl-X to exit (verifying save by hitting y when prompted...be sure to save the file as xorg.conf)

at prompt type "startx" to restart with nv driver

Fix problem using synaptic

open up terminal

cd /etc/X11

sudo Nano xorg.conf

under Device change the driver from "nv" to "nvidia"

Ctrl-X to exit (verifying save by hitting y when prompted...be sure to save the file as xorg.conf)

Ctrl+Alt+Backspace to restart X

---

