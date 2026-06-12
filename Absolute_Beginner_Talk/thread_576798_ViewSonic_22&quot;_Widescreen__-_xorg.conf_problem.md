---
title: "ViewSonic 22&quot; Widescreen  - xorg.conf problems"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-10-15
Hey guys,

I recently built a new machine with a rather large hard drive, so i partitioned 40GB for ubuntu and installed using the alternate-install CD.(Have tried live disc in the past, the alternate disc seems to work better for me)
The rest of my HDD went to M$ XP Pro

Here are a few specs:
Primary monitor: ViewSonic 22" widescreen LCD ( 1680 x 1050 native res. )
Secondary monitor: Gateway 15" CRT analog( 1024x768 )
GPU: nVidia GeForce 8600 GTS

After install, Ubuntu loaded successfully.  The maximum resolution available to me was 1024x768, which with my monitor, was not near the native res.  So I downloaded envy from albertomilone.com/nvidia_scripts1.html
and rebooted my machine.  After the reboot, ubuntu loaded at my full 1680x1050 res. and everything looked perfect.(I didnt have dual monitors but i was going to save that battle for another day)  

A few of my keyboard keys werent working correctly so i ran:
```
dpkg-reconfigure xserver-xorg

```to change the keyboard settings.  Well in doing that, i must have changed a monitor setting because now when i boot my machine into Ubuntu i either get one of 2 things:
1)  In the boot process, when it loads GDM, i get a blue screen saying that my xserver was not configured correctly.
2)  My monitor goes black and a monitor warning window shows up saying:
Out of Range
HF 65 KHz
VF 60 Hz

Could someone point me in the right direction?

---

### Post by ITdrummer on 2007-10-15
I might add that, I know the proper thing to do would be to post my xorg.conf so you guys could use to troubleshoot, but in my effort to troubleshoot on my own, my xorg.conf got deleted somehow.  This is my current problem:  getting a new copy of xorg.conf, but the problems mentioned above were happening when i had a valid xorg.conf file.

---

### Post by rsambuca on 2007-10-15
The dpkg command changed your xorg.  Since envy seemed to have worked the first time for you, I would re-run envy to install the nvidia drivers.  As for the keyboard, you should just be able to change the default layout after you have your video working again.

---

### Post by rsambuca on 2007-10-15
I just saw your second post.  There should be a backup xorg.conf file (I believe envy creates one).  If you can't find it, then just run the dpkg-reconfigure xserver-xorg again and it will create one.

---

### Post by LowSky on 2007-10-15
xorg.conf wont create a backup unless your using nvidia's update xorg program. you must manually back up your xorg.

Best thing to do is pop in your live cd and copy the live cd's xorg file to your hard drive

---

### Post by ITdrummer on 2007-10-15
Ok, so i ran ```
dpkg-reconfigure xserver-xorg
```
to create a new xorg.conf file.  When i restarted, xserver failed again and said:
> 
FATAL:  Could not open
'/lib/modules/2.6.20-16-generic/volatile/nividia.ko': No such file of directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernal module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


---

### Post by rsambuca on 2007-10-15
Now run envy again from the command line.

---

### Post by russell.h on 2007-10-15
I have that exact monitor at home (about 1600 miles away), I'll try to grab the xorg.conf and post it.

---

### Post by russell.h on 2007-10-15
Alright, here we go, I'm attaching it to this post. No garuntees though.

Edit: and now that I look at it, its far from ideal, (it supports a resolution the monitor doesn't support for example), but it might get you started. Good luck, I have to go take a midterm.

---

### Post by ITdrummer on 2007-10-15
Thank you for your help.  Ubuntu is now running 1680x1050 res.  Now, about my other monitor.  How do i go about setting that up for use?

---

