---
title: "Problem with installing Nvidia drivers"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Beamvr6 on 2006-09-24
Hi,

After another lethal Windoze crash 2 weeks ago I decided to make a near full switch to Linux except for things that only run well under Windoze such as games. Ubuntu looked like a nice pick for me and I installed it today and it looks very promising. :) 

Where I'm stuck is installing the driver for my GeForce 6600. I downloaded a driver package from Nvidia (NVIDIA-Linux-x86_64-1.0-8774-pkg2.run), navigated to the dir where it is saved and ran "sh NVIDIA-Linux-x86_64-1.0-8774-pkg2.run" following the instructions on Nvidias website. The package starts and then shows the message "ERROR: nvidia-installer must be run as root". :mad: 

The log in the terminal shows "Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 1.0-8774......................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging."

I checked User and Groups and there is no user "root" there and I am not sure how to proceed from here.

Device Manager reports the graphics card as NV43 [GeForce6600/GeForce 6600 GT]

My aim of installing the driver is to increase screen refresh rate from the max current 60 Hz to the 85 Hz possible in that other OS.

I fully realize I am an absolute noob on Linux so I might be missing something very obvious, help appreciated. :oops: 

TIA.

---

### Post by lonce on 2006-09-24
Use automatix.  It will automatically install your nvidia drivers.  Just search for automatix on the forums or they have their own forum from the front page.  All you do is install automatix and run it and it gives you lots of options of things it will automatically install for you.

---

### Post by Beamvr6 on 2006-09-24
Thanks for the quick reply Ionce! Both Automatix and the nVidia drivers installed now. There is a lot to learn in this world.

---

### Post by fragos on 2006-09-24
Whenever a command tells you "must be run as root" start the command with sudo as in "sudo nvidia-installer" and you will be asked for your user password before the command executes with root permissions.

---

### Post by lonce on 2006-09-24
No problem.  I am here to help.  I just started using ubuntu about 2 months ago.  Once you get past the learning curve and things are setup, its awesome.  I will never touch windows again.

---

