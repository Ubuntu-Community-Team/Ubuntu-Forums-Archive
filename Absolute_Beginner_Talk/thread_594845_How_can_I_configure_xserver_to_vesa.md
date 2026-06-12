---
title: "How can I configure xserver to vesa?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-10-28
I've recently installed 4.10 and had to boot the CD in "safe graphics mode". However, post-installation, the display is screwed and I need to change the xserver settings to vesa. I've run dpkg-reconfigure xserver-xorg a few times, but without success. If someone could point me at a guide to setting up xserver to the equivalent of the live CD's "safe graphics mode" option, I'd be grateful. 

Specs, btw, are these:

Dell Optiplex GXa
Intel P2-233 CPU
192MB RAM
S3 Savage4 video card
AcerView 34eL monitor
4Gb bootdrive
6Gb second drive

---

### Post by Unicycle on 2007-10-28
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Crafty Kisses on 2007-10-28
Make sure you select the vesa drivers.

```
sudo dpkg-reconfigure xserver-xorg
```
This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter. 

When you're done, press Cntrl+Alt+F7 to get back to graphical mode and then Cntrl+Alt+Backspace to reset the X server (so your changes can take effect).

---

### Post by MegaJim on 2007-10-28
lol both the muppets above me didnt read the op :D

I'm no expert but you could try changing this section of your xorg.conf to vesa

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"* < change to vesa*
	BusID		"PCI:1:0:0"
EndSection

```
sudo vim /etc/X11/xorg.conf 
```

---

### Post by moma on 2007-10-28
"xserver-xorg-video-vesa" package is installed by default.

Edit your /etc/X11/xorg.conf and change the Driver to "vesa" in the "Device" section.
Something like this:

$ [COLOR="SeaGreen"]sudo nano /etc/X11/xorg.conf[/COLOR]

```
Section "Device"
...
    Driver  "vesa"
EndSection
```

Or read the advice for "The graphical display will not start." [here...]("http://www.futuredesktop.net/getting-help.html")

---

### Post by gubemton on 2007-10-28
Thanks for the pointers: when I edited the xorg.conf file, I found that vesa was already set in the device section (although my BusID was "PCI:0.14.0" rather than "0.1.0", which I left alone as I assumed when I ran reconfig  xserver, it would have picked up the PCI bus ID).

I had an extra line in the device section:
```

option "useFBDev" "true"

```

I deleted this and was able to start the gnome gui. However, I was then presented with another error message telling me "your session lasted less than ten seconds" and I was invited to try again with a failsafe login. The failsafe gui didn't work, but the failsafe terminal let me  see that the installion went badly wrong: instead of the installation of ubuntu, I can see files from a previous mandrake installation,so it looks like ubuntu's HD formatting/installation options went awry somewhere (I wonder where the installation put the file system?!). 

I think I'll boot from a linux floppy and see if I can reformat the first HD and start afresh with a new installation. Now I know how to manually tweak xorg-conf if I have display problems, it shouldn't be too tricky. 

Thanks for the help :-)

---

