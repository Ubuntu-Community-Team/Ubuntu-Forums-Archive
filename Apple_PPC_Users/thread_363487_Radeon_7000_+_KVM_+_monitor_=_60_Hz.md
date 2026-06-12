---
title: "Radeon 7000 + KVM + monitor = 60 Hz?"
date: 2007-02-17
forum: Apple PPC Users
---

### Post by smurfmac on 2007-02-17
I'm a linux newb...I have a blue G3 system that's not exactly speedy running OS X, so to extend the useful life of the system, I want to use Linux and access my Mac OS software using MoL.  I'll worry about MoL later, right now I'm trying to get my video card/monitor working to their best ability.

I've got two available video cards, and I'll use whichever one is going to be easier.  I've got the machine connected via a USB KVM, and it needs to stay that way.  Mac OS 9 and Mac OS X both recognize all available resolutions/color depths/refresh rates, so I'm almost positive it's not the KVM's fault.

Right now I have a 32MB PCI Radeon 7000 in the system.  It booted a live CD and installed 6.10 without any issues at all.  It's quite usable, with one exception: the monitor (a 19" KDS CRT) only has three selectable resolutions - 640x480, 800x600, and 1024x768, and the only available refresh rate is 60Hz (56 is available for 800x600, incidentally).  I know some people don't have issue with low refresh rates, but I can see already that it's going to make me physically ill to stare at 60Hz on that monitor.  Is there something I failed to install, or something I can install to get everything available?  The Device Manager recognizes that the Radeon 7000 is there but says some weird things:

Vendor: ATI Technologies Inc
Device: Radeon RV100 QY [Radeon 7000/VE]
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

The "unknown" is what bothers me, but now that I look around, alot of items say that.  Sometimes it doesn't (like my mouse says "input" and several others say "alsa"), but I don't think the display adaptor should.

Any suggestions/downloads/help would be greatly appreciated.

I also have the stock Rage 128 16MB card available if need be.  I saw the post about reducing color depth to 16-bit if I need to.

Thanks!

Ben

---

### Post by smurfmac on 2007-02-17
Rage 128 is the same way, so I'm sticking to the 7000.  I found a nice primer on modifying the configuration file to enter my normal horizontal and vertical refresh speeds based on the monitor manufacturer's specs on their website.

---

### Post by XarvoX on 2007-03-10
I had the exact same problem on my Blue/white g3.
I had a friend to help me, now it works great with a nifty app called "Resolution Switcher"

In terminal, type sudo gedit /etc/X11/xorg.conf
enter password

Almost at the bottom of the document you will find entries similar to those posted below.
ill _underline_ the changes we did.

Hope it helps :)

(cutout from my xorg.conf-file)
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 RE/SG"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	_27-96_
	VertRefresh	_50-160_
EndSection

---

