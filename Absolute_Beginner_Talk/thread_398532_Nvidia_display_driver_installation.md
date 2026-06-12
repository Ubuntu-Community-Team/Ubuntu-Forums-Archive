---
title: "Nvidia display driver installation"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by counterpoint on 2007-04-01
My system is running on an Asus MN2PV-VM with onboard Nvidia 6150 graphics. At present, it appears to be using a generic video driver.  It works but offers limited choice of screen resolution.

Using the package manager, I installed nvidia-glx and then ran the command:
sudo nvidia-glx-config enable
then rebooted.

I can run nvidia-settings, but none of this seems to have altered the fact that xorg.conf contains only references to generic video driver and offers a limited range of screen resolutions.  The Nvidia settings don't seem to include basic things like screen resolution.

Also tried downloading the Nvidia driver, but that can't be installed, presumably because nvidia-glx is already installed, and maybe it shouldn't be needed.

What other steps are needed?

---

### Post by mikeyphi on 2007-04-01
Try the directions listed here [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) at item 1.11.2.1
It might be that you need to install other Nvidia packages.

---

### Post by counterpoint on 2007-04-01
Thanks.  I was unfortunately a bit imprecise in my original question.  The video section of xorg.conf contains:
> 
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"EndSection
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
        ....


So the system seems to know about the nvidia driver, but for some reason doesn't see the hardware as being Nvidia 6150.  Or maybe the issue is something else again!  

What I'm really after is getting higher resolutions - the maximum at present is 1024x768 as shown above.

---

### Post by overdrank on 2007-04-01
> **counterpoint said:**
> Thanks.  I was unfortunately a bit imprecise in my original question.  The video section of xorg.conf contains:


So the system seems to know about the nvidia driver, but for some reason doesn't see the hardware as being Nvidia 6150.  Or maybe the issue is something else again!  

What I'm really after is getting higher resolutions - the maximum at present is 1024x768 as shown above.

Hi and welcome. There is one of two ways to add the resolution that you want.
1. You can edit you xorg by using this command *gksudo gedit /etc/X11/xorg.conf* in the terminal and then save.
2. You can use this command in the terminal *sudo dpkg-reconfigure xserver-xorg* and reconfigure the xorg and add that resolution to it.

Hope this helps and I would try the 1st option. Good luck and welcome! :popcorn:

---

### Post by counterpoint on 2007-04-05
Editing xorg.conf seemed to do the trick - thanks :)

---

### Post by counterpoint on 2007-06-01
Now I have a new problem!  Since the last problem, I've had to reinstall Ubuntu several times because of application problems.  Always using 6.10 desktop.

Somehow or other the graphics problems went away because the subsequent installations were done using the normal monitor.  Looking at xorg.conf the video driver is shown as "vesa" and my hardware is (as above) Asus MN2PV-VM with onboard Nvidia 6150 graphics.  Resolution is 1280x1024.

All is fine, but now I have a new monitor that needs to be run at 1600x1200.  Simply editing xorg.conf to add the higher resolution didn't work.  Then I changed it to 1600x1200@60 and that didn't work.  It didn't work in the sense that my choices for resolution still went to a maximum of 1280x1024.

So I tried to install the nvidia driver.  That appeared to go OK, but after rebooting the X-server fails and I have to edit xorg.conf back to the "vesa" video driver from "nvidia" to be able to get graphic screens again.

* * * * *

Since writing the above, I've done a fresh install of Ubuntu 7.04, followed by installing the nvidia-glx driver using the package manager.  The enable command failed, but manual change of 'nv' to 'nvidia' seems to have enabled the nvidia driver - an Nvidia logo flash screen comes up during booting.  Although 1600x1200 appears to be well within the capacity of the hardware, the Gnome screen resolution selector still offers me nothing better than 1400x1050 at 57 Hz. 

How do I get out of this bind and achieve 1600x1200 at 60 Hz?

---

