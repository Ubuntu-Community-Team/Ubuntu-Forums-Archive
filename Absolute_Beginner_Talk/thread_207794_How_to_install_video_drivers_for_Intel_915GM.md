---
title: "How to install video drivers for Intel 915GM?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by chonzy on 2006-07-02
I have a Dell Inspiron 1300 Laptop, and i was wondering how can i install the actual drivers for the graphics card, because i cant seem to play in a decent way any 3d games, not even TuxRacer. The model of the graphics card is "intel(R) 915GM". There are some drivers available at Intel's website, but i cant figure out a way of installing them... 


Many thx in advanced :rolleyes:

---

### Post by chonzy on 2006-07-02
Any help would be greatly apreciated

---

### Post by H.E. Pennypacker on 2006-07-02
You should already have the driver installed, but you are likely not using it yet.  First, let's make sure that it is installed.  Start Synaptic, and look for xserver-xorg-driver-i810 (or just type in i915 into the search box).

If it is already installed (the box next to it is green), we can go to the next step.  If it is *not* installed, install it.  I too have i915 installed, and the problem is that Ubuntu didn't go ahead and use the i915 driver as it was supposed to have done.  Instead, it relied on VESA.  If you're interested in what VESA is, read about it, but its not important, so keep reading.

We're now going to make sure the system uses the driver it is supposed to use, instead of VESA.  We're going to do that by opening up /etc/X11/xorg.conf.  Go into the terminal, and type in gksudo gedit /etc/X11/xorg.conf.  This will open the file using gEdit.

You should now have /etc/X11/xorg.conf on your screen.  Go to the following section:

> Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	Option          "XAANoOffscreenPixmaps"
	BusID		"PCI:0:2:0"
EndSection

You see where my driver says i810?  That's because I changed it to i810.  Before, it said "vesa," because it wasn't using the driver it was supposed to use.  You may be wonder...why i810 when you actually have the i915?  Well, i810 is the name that covers the entire family, including i915.  So, change the driver from whatever it is (likely "vesa"), change it to say i915, as you see in the above example.

Now, to have things go into effect, save the document, and restart your system.  Your system should now be using the correct driver, instead of Vesa.

---

