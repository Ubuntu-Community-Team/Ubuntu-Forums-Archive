---
title: "Install problem, Live CD does not open, graphics card?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-04-06
Hi,
I wanted to install ubuntu (actually xubuntu) to my old computer (not so old for xubuntu, pent 3, 256 mb ram).  Xubuntu Install cd got stuck in the middle of opening live CD (EVEN BEFORE INSTALLATION). Then I used ubuntu cd, since I installed many times from this cd, it comes to last point where ubuntu supposed to start and I was supposed to click on install button ON THE UBUNTU, but I see just a blank screen. Therefore I assume there is a video related problem. (I checked both live CD's work in my laptop, so no problem with the CDs).
-----------------------------------------------------------------------------------------------------------------------
MONITOR:
I have dell 21 inch monitor ([http://www.dealtime.com/xPF-Dell-P1130-21-in](http://www.dealtime.com/xPF-Dell-P1130-21-in))
 Resolutions supported  	 1024 x 768 • 1280 x 1024 • 1600 x 1200 • 2048 x 1536 • 640 x 480 • 720 x 400 • 800 x 600
 Synchronization Range - Vertical 	48 - 170 Hz
 Synchronization Range - Horizontal 	30 - 130 kHz
 Native (Recommended) Resolution 	1280 x 1024

The CARD is : NVidia Riva TNT2 Model64

I fresh installed Win2000 and it works perfectly. From win2000 I can see from Display Adapters, there are 2 adapters
1-Default Intel Corporation 810 Graphics Controller Hub
2-NVidia Riva TNT2 Model64

Monitors
Default Monitor
Plug and Play Monitor

Location
on Intel Corporation 810 ...
on NVidia ...
---------------------------------------------------------------

Any suggestion would help! Thanks in advance
findik

---

### Post by Aircooledmadness on 2007-04-06
You could try yanking the Nvidia card,  then install it off the Intel integrated.....they are supported very well.

Then do a little research on your Nvidia card...see if other people have problems.  Once your system is up and running,  toss the Nvidia card back in,  and do a 'sudo dpkg-reconfigure xserver-xorg'

---

### Post by Bachstelze on 2007-04-06
Maybe the computer's specs are a bit too low for a Live CD. Have you tried an Alternate ?

---

### Post by findik1 on 2007-04-06
> **Aircooledmadness said:**
> You could try yanking the Nvidia card,  then install it off the Intel integrated.....they are supported very well.

Then do a little research on your Nvidia card...see if other people have problems.  Once your system is up and running,  toss the Nvidia card back in,  and do a 'sudo dpkg-reconfigure xserver-xorg'


since I am new, would you explain how I can do that?

---

### Post by findik1 on 2007-04-06
> **HymnToLife said:**
> Maybe the computer's specs are a bit too low for a Live CD. Have you tried an Alternate ?

I thought about that. In Live CD there is some options like (F7,F8 as far as I remember) but since I am new live CD install would be much easier for me. So I did not tried much.

The thing is that the compuer spec should be OK, since I installed ubuntu on pent 3 1ghz (dell dimension) before without a problem. And this one is dell optiplex pent3 933MHz. Also whole point of xubuntu is to be able to install to old machined I assumed. What I am suspecting is that dell monitor maybe too advanced (although it is not new). It has CRT monitor but there are 2 video output like LCD monitors. Maybe linux had trouble with that. I am just guessing.

thanks anyway
findik

---

### Post by findik1 on 2007-04-06
> **Aircooledmadness said:**
> You could try yanking the Nvidia card,  then install it off the Intel integrated.....they are supported very well.

Then do a little research on your Nvidia card...see if other people have problems.  Once your system is up and running,  toss the Nvidia card back in,  and do a 'sudo dpkg-reconfigure xserver-xorg'


I remember that there are 2 video inputs from the back of the computer. I tried once this:  connected monitor cable to intel itegrated monitor adaptor, but it did not work either...

---

### Post by xerox on 2007-04-06
You may need the Nvidia graphics driver...

Not sure if this would help, but I found this.

[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

---

### Post by findik1 on 2007-04-06
> **xerox said:**
> You may need the Nvidia graphics driver...

Not sure if this would help, but I found this.

[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

ok thank you. It seems this requires you first to install linux (it says dont use this with live CD). I will try to bring my computer to workplace and install liveCD, then I can follow these steps
best
findik

---

