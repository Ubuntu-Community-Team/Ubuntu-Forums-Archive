---
title: "Gutsy and graphics problem"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by phil66 on 2008-01-01
My system:

Dell xps 600 Plentium D dual core 3.0ghz
Video card Nvida GeForce 7900gs
Monitor Dell 2007fp 20 inch DVI Mode
Memory 1024 mb

My problem:

Running live cd start or install mode
System goes thru boot mode at the end displays dots and bars above and below Ubuntu logo
Continues to desktop then  I can only get drop down menu's none of the programs will open
I cannot use shutdown mode I have to shut the computer off by hand

What I have tried:

Checked disk to verify it was ok. This disk came from Ship IT
Start Ubuntu in safe graphic mode same display of bars and dots
It proceeded to desktop and I am able to navigate thru the system including hooking up with dial-up to internet

Screen and graphics performance
Model Nvida Ge Force series 7900gs
Driver Nv Nvida Riva 128,Riva Tnt, Geforce
Test failed

Driver Versa generic versa compliant vid
Test failed This is the default driver

Restricted Drivers 

Nvida accelerated graphics card Not in use

Screen 1024x768x85 hz
Test failed

Device manager:

Nvida g71 Geforce 7900gs
Unknown 0x007e,0x007f,0x00b4

Checked conf file : /etc/X11/xorg.conf
Server layout "Default Layout"
Screen"Default Screen" (0)
Monitor "Generic Monitor"
Devices "Generic Video Card"

Questions:

Is this caused by using the Dvi rather than Vga monitor
Would driver nvida-linux-x86-169.07.pkg2.run solve this problem
This was not a problem in Fiesty

Any and all help and suggestions appreciated

---

### Post by overdrank on 2008-01-01
HI and I would say that if it worked in Feisty that it will work in Gutsy. If you decide to install there are several user that have that card working on Gutsy. Just do a quick search and decide for yourself. Good luck!

---

### Post by phil66 on 2008-01-01
> **overdrank said:**
> HI and I would say that if it worked in Feisty that it will work in Gutsy. If you decide to install there are several user that have that card working on Gutsy. Just do a quick search and decide for yourself. Good luck!

Thanks for the reply

I agree if it worked in fiesty it should work in gusty! But it does not

Why does the desktop display then  no apps can be opened?

I do not see that installing the distro will solve this problem! Do you

Can you go from safe mode to standard mode without rebooting?

Thanks again

---

### Post by overdrank on 2008-01-01
> **phil66 said:**
> Thanks for the reply

I agree if it worked in fiesty it should work in gusty! But it does not

Why does the desktop display then  no apps can be opened?

I do not see that installing the distro will solve this problem! Do you

Can you go from safe mode to standard mode without rebooting?

Thanks again

HI and not that I know of. Have you considered just upgrading ( through update manager) or if you are happy with Feisty and all works then just stick with it. Then just wait for Hardy and see. Good luck in what ever you choose.

---

### Post by skymera on 2008-01-01
i have that graphics card.

7900GS - i used envy and worked 110% on gutsy

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

for live cd mine worked fine, 
try nv driver or alternate cd

---

