---
title: "[SOLVED] How do I change drivers for Intel graphics card in Ubuntu Studio?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by seanfitz64 on 2007-07-24
I'm new to Linux and I recently installed Ubuntu Studio Feisty Fawn 7.04 on my laptop. When I tried to run the Second Life client I get a "Window creation error" message.

The weird thing is if I load regular Ubuntu FF *live* distro onto the same machine I can run the Second Life client with no problems.

It appears the "Window creation error" message points to a problem with my graphic card's setup and drivers.

A comparison of the drivers loaded using each distro brings up interesting results. At this stage I am assuming this is the cause of my problem.

Here is the relevant section of the xorg.conf from installed Ubuntu Studio FF:

[INDENT]Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection[/INDENT]

Here is the relevant section of the xorg.conf from the Ubuntu FF live distro:

[INDENT]Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
EndSection[/INDENT]

It appears that the Ubuntu live distro is doing a better job of detecting the video card and selecting the correct driver than Ubuntu Studio did when it was installed.

I've tried to change xorg.conf manually, but that didn't work... the x-server didn't load at all on reboot!

So how do I ensure the correct drivers get loaded into Ubuntu Studio and referenced in xorg.conf?

Thanks in advance.

Sean

---

### Post by ramjet_1953 on 2007-07-24
This link will give you the information that you need.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

It is probably best to still stick with the 915resolution solution, as the new Intel driver is still a bit buggy and crashes X if an application dynamically tries to change the screen resolution.

Regards,
Roger :cool:

---

### Post by seanfitz64 on 2007-07-24
Thanks ramjet_1953, but the problem wasn't with the resolution, it was with selecting the correct driver and having the correct settings in xorg.conf.

After some more research I discovered I could reconfigure my video setup with 'sudo dpkg-reconfigure xserver-xorg'. 

I was presented with way more variables than I was ready to deal with though. I selected the i810 driver as that was the one working on Ubuntu live and went with the defaults on everything else.

I later found out that 'sudo dpkg-reconfigure -phigh xserver-xorg' provides less options - just driver and screen resolution.

So all is well and Second Life runs fine now. :-)

---

