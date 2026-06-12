---
title: "Just got new widescreen monitor"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by SapiensFossor on 2007-06-13
Hi there,

I just got a Samsung widescreen SyncMaster 906 BW monitor.  The problem is that Ubuntu (fesity) doesn't fill up the whole width, there's a black space on the right side for about 2 inches (and the picture is also a little blurry).

Can anyone help me sort this out?

Thank you so so much for any help.

---

### Post by locke.dragon on 2007-06-13
what video driver do you use?  and have you fiddled with the buttons on the monitor?  sometimes there will be something that will help you get rid of that black space.

---

### Post by annda on 2007-06-13
what is your graphic card? what driver do you use? for example, if you have the nvidia driver, you can sudo nvidia-settings to easily adjust the configuration and update the xorg.conf file.

---

### Post by annda on 2007-06-13
> **locke.dragon said:**
> what video driver do you use?  and have you fiddled with the buttons on the monitor?  sometimes there will be something that will help you get rid of that black space.

if you have any sort of 'auto' button on your monitor, try that first.

---

### Post by GSF1200S on 2007-06-13
> **SapiensFossor said:**
> Hi there,

I just got a Samsung widescreen SyncMaster 906 BW monitor.  The problem is that Ubuntu (fesity) doesn't fill up the whole width, there's a black space on the right side for about 2 inches (and the picture is also a little blurry).

Can anyone help me sort this out?

Thank you so so much for any help.

Well, the fact that its blurry makes it sound like the resolution is off. Im no expert here, but does your hardware support the monitors resolution? I THINK, and dont quote me because I could be talking from my butt, that the graphics card has to be capable of the resolution. If yours isnt, that would pose a problem. If someone else knows more, please say something.

As for the black bar on the side of the screen- have you tried manually adjusting the monitor to fit? I know I had to do that on my Moms computer when I first installed Ubuntu.

Hope this helps...

---

### Post by punx45 on 2007-06-13
yeah, you are right.   we need to know the video chipset and go from there.   am I correct in assuming that Feisty still does not come with proprietary graphics drivers?

the only feisty system i have is headless :-k

---

### Post by GSF1200S on 2007-06-13
> **punx45 said:**
> yeah, you are right.   we need to know the video chipset and go from there.   am I correct in assuming that Feisty still does not come with proprietary graphics drivers?

the only feisty system i have is headless :-k

Depends on the chipset. My laptop with an Nvidia card needed the drivers from the Nvidia website. My moms desktop with an intel card, had compiz working out of the box (just enable desktop effects). I actually crashed the Xserver trying to install a driver that was already installed :) . I had to use the LiveCD to fix that one..:p

In short, if its an ATI or Nvidia, the proprietary driver isnt included. At least with my experience with Intel, its included out of the box...

---

### Post by Atomic Dog on 2007-06-13
open up Terminal and then type:

```
lspci
```

Then give us the output of the line that starts with: Display controller:

---

### Post by locke.dragon on 2007-06-13
just give us the lspci thing.  we can get it working.  the hardware thing isn't true.  you can pretty much get any resolution working as long as the screen supports it.  and why would they make a monitor for a certain resolution and make it so it couldn't use that resolution?  :P

---

### Post by SapiensFossor on 2007-06-14
Here's what I get when I type in lspci.  Thanks a lot for the help :)

```
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:08.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
```

---

### Post by locke.dragon on 2007-06-14
ah.  nVidia card.  sorry, can't help ya there.  i've got meself an intel!  w00t!  :P

---

### Post by BlackMeTaL on 2007-06-14
Well it seems that the native resolution of your monitor is 1440x900
What resolution do you get when you look at System -> Preferences -> Screen resolution?

---

### Post by SapiensFossor on 2007-06-17
The highest it will let me change the resolution is 1024x768.  I did, however, fix the blurryness of the monitor by changing the refresh rate from 50 to 54.

Thanks a lot for helping me :)

---

### Post by BlackMeTaL on 2007-06-19
I'm still not satisfied :)
Could you post the /etc/X11/xorg.conf file of your Ubuntu installation?

---

