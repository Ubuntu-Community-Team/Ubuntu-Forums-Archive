---
title: "Kubuntu Crashing"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by SavageFreedom on 2007-07-02
Something has gone majorly wrong with my PC here. It all happened after I integrated some of the Ubuntu Studio components into Kubuntu Feisty. The guide I read was for Ubuntu Feisty with no guaranteed Kubuntu success, so I suppose this may be what I get for that, but it really seems kind of odd for Kubuntu to be crashing in such a windoze-esque fashion.

1) When I boot the PC up, grub automatically selects (as it has been doing for some time now) the low-latency mode for Kubuntu. The Kubuntu loading screen appears, loads fully, blinks out as if it'll now go to the login window, but then blinks back in with no progress on the loading bar. It stays like that for about 5-10 seconds and then goes to a flashing cursor, no terminal prompt or anything. From that point I can do nothing but physically reboot it. Then I have to select Kubuntu generic, same version but not the low-latency version. This boots up normally and seems to work relatively fine for a brief period of time.

2) Firefox crashes periodically now.

3) Battle For Wesnoth crashes every few minutes and screws up the resolution on the desktop.

What might have happened here? Any tips? PC specs are in my sig, the comp this is happening on is the "work" comp, (thank god.)

---

### Post by ndefontenay on 2007-07-03
Maybe just your graphical card screwing up no?

Have you checked your xorg.conf file?

What are your computer specs?
What kind of graphical card particularly?

---

### Post by SavageFreedom on 2007-07-03
The PC is a Dell Dimension B1100, the graphics card is an nvidia GeForce 5500 PCI 256mb.

When I tried to edit my xorg.conf file, this is what the terminal threw back at me... yikes.

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

---

### Post by SavageFreedom on 2007-07-03
Though when I did get xorg.conf open, here's the device section. My GeForce 5500 is PCI, but it's using the embedded graphics as the identifier, but otherwise it seems to be set up here properly...

```
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"nvidia"
	#BusID		"PCI:0:2:0"
EndSection
```

---

### Post by Raineer on 2007-07-03
> **SavageFreedom said:**
> The PC is a Dell Dimension B1100, the graphics card is an nvidia GeForce 5500 PCI 256mb.

When I tried to edit my xorg.conf file, this is what the terminal threw back at me... yikes.

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```
Not as bad as you think, comment out the following lines as seen here:
```
#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "stylus"
#        Option          "Device"        "/dev/input/wacom"
#        Option          "Type"          "stylus"
#        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "eraser"
#        Option          "Device"        "/dev/input/wacom"
#        Option          "Type"          "eraser"
#        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection 

#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "cursor"
#        Option          "Device"        "/dev/input/wacom"
#        Option          "Type"          "cursor"
#        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection 
```
Any time you see "Wacom" in the Driver heading, if you're not using a tablet PC you want that commented out. That's why you see those errors.

As a small editoral... I absolutely LOVED the KDE interface, but found it too buggy :(  The whole "kdeinit is not running" bug happened way too often for me, and X crashing to the login prompt was all too common, even when I only had 6-7 windows open.  I can completely **torch** Gnome with 15-20 windows, 4 workspaces, floaty cubes in all their wobbly goodness and it hasn't crashed yet.  I'm better off for the experience of learning KDE (and EAGERLY await 4.0 later this year), but for now I'm sticking with Gnome as I can't afford to lose any more work. 

If I was just listening to music, web browsing, and playin games...then I'd probably pick KDE, but not for a work PC.

---

### Post by Damanther on 2007-07-03
Did you happen to install the latest nvidia drivers from the restricted modules recently? Same thing happened to me a few days ago when I, without thinking, updated the nvidia through adept, and I had to go straighten it out in console mode to get it working again.

Damanther

---

### Post by Raineer on 2007-07-03
> **Damanther said:**
> Did you happen to install the latest nvidia drivers from the restricted modules recently? Same thing happened to me a few days ago when I, without thinking, updated the nvidia through adept, and I had to go straighten it out in console mode to get it working again.

Damanther
I had that happen to me too, turned out I messed up because I had a newer version of driver than was configured into my kernel. [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") appears to sort this out by actually doing the kernel work necessary to support later drivers.

---

