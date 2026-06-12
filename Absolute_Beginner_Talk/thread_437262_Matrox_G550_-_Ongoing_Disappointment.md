---
title: "Matrox G550 - Ongoing Disappointment"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by clubsoda on 2007-05-08
I got my Matrox G550 single DVI graphic card just after Edgy was released with a broken mga driver => unlucky timing.  Thankfully, Feisty's mga driver is fixed but I'm still having a few issues.

**1) Need Framebuffer**
I've found only two ways to get my system booted:-
  i) use "vga=795" as a boot option (enabling the VESA framebuffer)
    [In this case, the display resolution cannot be changed from "Default"]
  ii) add matroxfb_base to /etc/modules (enabling the matrox framebuffer)
   + comment out matroxfb_base from /etc/modprobe.d/blacklist-framebuffer
   + add  Option "UseFBDev" "True" to /etc/X11/xorg.conf
Without one of these framebuffers, I get the splash screen, but when the login page is reached the monitor goes "Out of Range" and cycles on and off.  
Surfing around the 'net, the consensus seems to be that framebuffers are to be avoided if possible.  Can I run Xubuntu on my G550 without a framebuffer?

**2) Glxgears **
Glxgears runs, and fairly quickly too, but if I try to move its frame to a different place on the screen, only the frame and control buttons move... the rotating gears stay at the top left screen position.  Is that normal or should I blame the Matrox?

**3) libsvga1 Crashes**
I've tried setting HorizSync, VertRefresh and some modelines in /etc/vga/libvga.config, even tried forcing chipset G400, but whenever I run something on libsvga1, I get a total freeze which responds to nothing short of a hard reset, and kludges up my /tmp partition, often requiring manual fsck-ing on the next boot <ugly>.  I wish libsvga would allow me to run in a 640x480 sub-window (like SDL) instead of trying to take control of the hardware directly.  How can I waste hours playing *vgacardgames* and *thrust* without libsvga??? :popcorn: 

As always, thanks for any assistance.

PS: System was upgraded via command line from an Xubuntu Edgy installation.  Also ran sudo dpkg-reconfigure xserver-xorg, selecting mga driver.

---

### Post by clubsoda on 2007-05-13
Here's how I got my system going.

First and foremost, I visited [http://matrox.tuxx-home.at](http://matrox.tuxx-home.at) and downloaded Alexander's latest version of the mga driver.  The driver consists of two parts, an "mga_hal" part which appears to be identical to the current feisty version and is a proprietary driver provided by Matrox, and an "mga" part which is evidently different (and somehow better) than the feisty version.

Next, I undid all the framebuffer hacks mentioned in the previous post.  My xorg.conf now differs from a standard *dpkg-reconfigure* as follows.
Added:-```
Section "ServerFlags"
        Option  "IgnoreABI"     "True"
EndSection
```
Removed (commented out):-```
#       Option          "OldDmaInit"            "True"
#       Option          "UseFBDev"              "True"
```**lsmod** indicates that vesafb is still being loaded.  

**glxgears** runs at 325 frames per second with DefaultDepth set to 24 bits per pixel, increasing to 480fps at 16bpp.  Problem #2 (glxgears becoming detached from their frame) remains.

Finally, it turns out that **libsvga1** does work with the "chipset G400" option enabled.  If you feel nostalgic for DOS-style games on your linux box then this can only be good news.  [You can even use Synaptic to search for packages which depend on libsvga1.  ;)]

---

