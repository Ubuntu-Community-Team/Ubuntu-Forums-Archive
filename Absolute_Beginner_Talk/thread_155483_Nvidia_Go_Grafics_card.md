---
title: "Nvidia Go Grafics card"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by millol on 2006-04-05
Hello
I'm running Ubuntu on my laptop which has an Nvidia FX go5600 64MB Grafics card.
I tried the nvidia-glx drivers but I found out that it's not compatible with my "go" series card. In fact, the result was worse than the default driver.
Any help?
Thank you.

---

### Post by hw-tph on 2006-04-05
How do you know the driver is not compatible? Is this stated in the X logfile? (**grep -i nvidia /var/log/Xorg.0.log** could help)

In most cases you just need to fine tune your X configuration (/etc/X11/xorg.conf), so some more information would be helpful. Like what kind of display do you have? What is the native resolution of it?


Håkan

---

### Post by spasmoid on 2006-04-05
I would actually like to know how one goes about installing the driver that NVidia distributes on their website. After I installed ubuntu, I thought the performance was a bit lacking in the display, so I thought that installing the NVidia driver might help.

Only problem is, that it has all these requirements...
First, I had to find a way to run it as root (I'm a n00b)
Second, I had to figure out how to install binutils
Third, I have to figure out how to run it without having X running but I can't have it in runlevel 1.

Any ideas how I can kill X without it restarting but still be in multi-user mode?

---

### Post by hw-tph on 2006-04-06
If you search this forum I think there is a howto or two for installing the nvidia drivers as packaged by nvidia. I use the official debs or source debs and am quite pleased with how they perform on my GeForce4 Go 420.

To answer your other questions:

In Ubuntu, root has no password by default. Instead you use the [sudo command](https://wiki.ubuntu.com/RootSudo) to gain superuser privileges temporarily (demonstrated in the commands below). To get a root shell, type **sudo -i**.

Installing binutils is easy: Simply type **sudo apt-get install binutils**.

To stop the X server, type **sudo /etc/init.d/gdm stop**. To start it again, replace "stop" with "start". 


Håkan

---

### Post by tseliot on 2006-04-06
[QUOTE=millol]Hello
I'm running Ubuntu on my laptop which has an Nvidia FX go5600 64MB Grafics card.
I tried the nvidia-glx drivers but I found out that it's not compatible with my "go" series card. In fact, the result was worse than the default driver.
Any help?
Thank you.[/QUOTE]
You might want to try my guide:
[HOWTO: Latest NVIDIA drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

Use Method 2 and driver 8178 (it's all explained in my guide)

---

