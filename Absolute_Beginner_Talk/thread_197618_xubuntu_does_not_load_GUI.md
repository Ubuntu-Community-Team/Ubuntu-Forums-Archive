---
title: "xubuntu does not load GUI"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by unicycler on 2006-06-16
I have xubuntu installed, but I cannot get the GUI to come up. This is a fresh install from the Alternate CD.

When starting the computer, it shows all steps, but then when it should start the GUI, the screen goes black. Not black like the monitor is not getting a signal, but the screen is actually getting the color black to show up.

Tower is 333MHz Intel Celleron, 512 MB SDRAM, ATi 7000 32MB Video Card (AGPx X - I don't know the slot's speed.

---

### Post by aysiu on 2006-06-16
Is it totally black?

Or is it black with some white text on it?

---

### Post by nalmeth on 2006-06-16
At the black screen, can you hit CNTL-ALT F2 to get to a virtual terminal? 
If so, login and type:

sudo dpkg-reconfigure xserver-xorg

---

### Post by unicycler on 2006-06-16
All black, no text, and I have no access to tty1 through tty6

---

### Post by vuul on 2006-06-16
Does that video card have the s-video output? I know you have an ATi card, but I was working on getting my nvidia twinview working and a couple of times when I had bad options in my xorg.conf I had the same symptoms you are describing.

---

### Post by unicycler on 2006-06-16
yes, there is an S-video port? Do I make changes in dpkg-reconfigure xserver-xorg

---

### Post by unicycler on 2006-06-16
I am trying to work 2 forums here, so I have learned that my fix to this problem is in the /etc/X11/xorg.conf

I changed the driver from "ati" to "vesa" 
and xserver starts right up.

Thank you all for your help.

---

### Post by vuul on 2006-06-16
I remember when I was using an ATi card that there are two native drivers available for Ati cards. One is ati, and the other is radeon. Edit /etc/X11/xorg.conf go to the Device section and where it says something like this:
```
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
```
(This is a snip from my xorg.conf file)
Change the word in quotes next to Driver to either "ati", or "radeon"
Then reboot to try the driver.

---

### Post by sylvanmedia on 2008-07-12
i've tried all of what was said in this post, nothing worked for my system, i am using ubuntu 8.04LTS Server. On a P3 833MHz. The GUI just won't load every time i boot the GNOME Display module, it says FAIL, but it boots fine at startup, but won't go into GUI mode.

---

### Post by steve8track on 2008-07-12
Here are some further suggestions:

1.  If you installed a server edition of Ubuntu/Xubuntu, then no GUI is installed by default.  Try installing from the Desktop CD or installing ubuntu-desktop to get the GUI working.  If you installed the Desktop version, you can always add server software easily later.

2.  Maybe the CD is bad.  Try running the test for errors on the CD's boot options.  If there are errors, you can download the iso again.  If that doesn't work, you can try downloading a different version or a different image of Ubuntu.

Also, I don't know about your particular graphics card, but if there are drivers more specific to it, then go with those.  Vesa, for example, seem to be more general purpose.  It's good to get those working to make sure your hardware is supported and working correctly, but it's still well worth getting better performance with the specific drivers.  You can search around the web for the drivers your hardware needs.

I hope this helps someone.

Steve

---

