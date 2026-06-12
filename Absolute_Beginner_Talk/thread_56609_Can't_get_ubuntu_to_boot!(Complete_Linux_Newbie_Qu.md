---
title: "Can't get ubuntu to boot!(Complete Linux Newbie Question)"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by Zarok on 2005-08-13
Ok, so I finally had the guts to venture into the world of Linux. I installed it on my HP Pavillon 6158EA laptop(details at [http://h10010.www1.hp.com/wwpc/fi/fi/ho/WF06b/22095-315715-1301501-1301501-1301501-12200384-56001193.html](http://h10010.www1.hp.com/wwpc/fi/fi/ho/WF06b/22095-315715-1301501-1301501-1301501-12200384-56001193.html) , sorry bout them being in finnish but couldn't find it in any other language, you should see the important info from that too) using the ubuntu AMD 64 version 5.0.4 install cd. Everything went just fine until it was time to boot it the first time. It allowed me to login, but gets stuck when it tries to open the desktop. I can get the linux working using the recovery mode boot, but I have no idea on how to fix the GUI problem with it. Any ideas?

---

### Post by Lord Illidan on 2005-08-13
You have an Nvidia card?

I think you can solve that problem from the console (recovery mode)

Can you give tell us if under the section Device in /etc/X11/xorg.conf, the driver is nv?

Let me give u a walkthrough..

Log in the console..

```
sudo vi /etc/X11/xorg.conf
``` 

And navigate to the section Device..

Your's might look like mine:

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

but probably it will be like this

Section "Device"
        Identifier      "What ever your graphics card is"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

You have to change "nv" to "vesa", to do this, press the Insert button, then when you are done editing, press escape, and a colon will appear on the bottom of the screen. Type wq to exit..

Reboot and see if you can login to a GUI...

---

### Post by Zarok on 2005-08-13
Found the folder using find... heh... Still got an ati card, not a NV one, Device says:

Identifier "ati technologies, inc. Radeon Xpress 200M (rs480)"
Driver      "ati"
busid      "pci:1:5:0"
endsection

Ubuntu just starts up, plays the login music(really laggy tho, makes some weird sounds with it), opens the logo image with a part of the bottom missing, keeps loading, and when the logo image is completely loaded, gets stuck there and doesn't react to anything.

---

### Post by Lord Illidan on 2005-08-13
Try changing it to "vesa"

---

### Post by Zarok on 2005-08-13
[QUOTE=Lord Illidan]Try changing it to "vesa"[/QUOTE]
It's alive! ALIVE!!!!!!!!!!!!! lol... Thanks mate :)

---

