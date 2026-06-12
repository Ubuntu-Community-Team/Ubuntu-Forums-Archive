---
title: "Failure to even load or boot..? :("
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by syn` on 2008-01-26
Okay, so here's my problem.

I'm completely new to Linux and ended up running across Ubuntu 7.4 a while back. I tried installing but couldn't get my Radeon 9200 to work for the life of me and after a few nights of frustration I ended up going back to Windows. A couple months later I was browsing around the internet and ran across a link to Linux Mint. It said it was Ubuntu but provided a better "out of the box" experience. I figured that sounded like something that might suit me.

Before I downloaded Linux Mint, tho, my brother gave me his old Radeon 9250 so that hopefully I could get that card to work. After installing it in Windows to see if it worked, I burned my live CD and started the process. So, I installed it and all my hardware was recognized except for my Radeon 9200 and 9250. I figured what my problem was is that I had an old version of BIOS, it didn't let me disable my onboard graphics card, which is what I had been installing and running Linux on so far. Unlike Windows I wasn't able to just switch between the card displays.

I searched around for a while and finally found my BIOS update and flashed my BIOS. The first thing I did was go into it and turn off my onboard and set it to the Radeon. I save and restart, expecting to have everything working.. and my Linux Mint load screen pops up, everything's OK, then it gets stuck. I wait for 15 minutes, still stuck. Restart, try it again. Still stuck. Eventually I tried putting the live CD back in.. same thing. It gets about 20% through the load bar and gets stuck. I pop in my Ubuntu 7.4 and 7.10, PCLinuxOS, Freespire, all the live CDs I had burned and they all do the same thing.

I tried that for about two hours or so and I finally took the 9200 out and put in the 9250 hoping that would solve the problem, that the 9200 was the problem. Load screen comes up, same thing happens. I go through the cycle of the live CDs, same thing happened. I eventually got so frustrated that I set it back to display the onboard and tried all the other ways of getting my card to work. I installed the drivers from Envy, didn't work. Removed, tried the ones from ATI.com, didn't work. I sat in the IRC channel all day asking for fixes, nothing would work. Why would it? It wouldn't even boot up.

So I went out and ordered a Nvidia Geforce 6200 trying to get away from the cursed ATI. So the next few days while I waited for it to arrive, I went about my business using my onboard and waiting patiently. Finally the package gets here, I slap that new graphics card in and.. THE SAME THING HAPPENS. It displays to the loading screen, the bar fills up say 20% and it just stops.

I hit F6 and tried booting up adding: "noapic nolapic" and "noapic" and "nolapic" -- all to no result. I tried booting in recovery mode and it would make it to where it says "* Loading Hardware Drivers" and after that it would just scroll with an entire page of errors and stop. So I know it has to be something with the drivers or something. 

I posted about it on the Linux Mint forums and didn't get any replies really. The forums aren't as active as here, which is why I'm asking. I'm looking for any possible fix for this because right now I'm running Windows and it's driving me crazy. Someone suggested my motherboard? couldn't power the card, but both ATIs ran fine in Windows for years, and the Nvidia is working perfectly right now. I'm including some pictures.

The computer is a **Dell Dimension 2350** ([clicky](http://support.dell.com/support/edocs/systems/dim2350/specs.htm#1106980))

**Showing Card DOES Work In Windows**
[[IMG]http://img352.imageshack.us/img352/2692/nvidiaxz7.th.jpg[/IMG]](http://img352.imageshack.us/my.php?image=nvidiaxz7.jpg)

**The Load Screen It Freezes On**
[[IMG]http://img86.imageshack.us/img86/1691/s5000625ea0.th.jpg[/IMG]](http://img86.imageshack.us/my.php?image=s5000625ea0.jpg)

**The Actual Errors When Splash Is Removed**
[[IMG]http://img222.imageshack.us/img222/2937/s5000628mj4.th.jpg[/IMG]](http://img222.imageshack.us/my.php?image=s5000628mj4.jpg)

**The Actual Errors (With Flash On Camera)**
[[IMG]http://img86.imageshack.us/img86/3581/s5000627mg8.th.jpg[/IMG]](http://img86.imageshack.us/my.php?image=s5000627mg8.jpg)

---

### Post by dstew on 2008-01-26
Did it run any Live CD before you updated the BIOS, either with the onboard graphics adapter or with your plug-in adapter?

---

### Post by syn` on 2008-01-26
> **dstew said:**
> Did it run any Live CD before you updated the BIOS, either with the onboard graphics adapter or with your plug-in adapter?

Yes, the Live CD would work before I updated my BIOS but just with the onboard. It wouldn't work with the plug-in because I couldn't disable the onboard from the old version of BIOS; there was no option to.

The Live CD will still work but only while the BIOS is set to the onboard option. If I turn the default display or whatever to the plug-in that's the errors I get. But as long as it is set to my onboard, I have no problem loading any Live CD up.

---

### Post by syn` on 2008-01-26
Up.

---

### Post by dstew on 2008-01-26
Sometimes the Live CDs will just not work with a particular machine. You tried boot parameters. Maybe you should use an alternate install (text-based) CD. I don't know if Mint has one.

---

### Post by syn` on 2008-01-26
> **dstew said:**
> Sometimes the Live CDs will just not work with a particular machine. You tried boot parameters. Maybe you should use an alternate install (text-based) CD. I don't know if Mint has one.

It wasn't just the Live CD, tho. 

When I got the Nvidia card Mint was already installed, I was just running it off the onboard. I turned off the computer, put the Nvidia in, changed the BIOS to the Nvidia and I still got that error.

It's not just an installation problem I'm having, but once the OS is already installed I get the same problem. Same errors, freezes on the load screen.

---

### Post by syn` on 2008-01-26
Up.

---

### Post by syn` on 2008-01-26
Up, again.

---

### Post by syn` on 2008-01-27
Up again.

---

### Post by syn` on 2008-01-27
Giving it another shot ;)

---

### Post by dstew on 2008-01-27
Just to get back in the game, I need to understand. The problem is that your installed Ubuntu will not boot (freezes) if either your ATI or Nvidia card is in place and selected by the BIOS, but it will boot if you have selected the on-board video. Is this the situation?

---

### Post by zubrug on 2008-01-27
Try this
When you get to the install options at the initial install dialogue, hit f6 and then type 
all generic ide
hit enter and good luck, this usually works for myself.

---

### Post by syn` on 2008-01-27
> **dstew said:**
> Just to get back in the game, I need to understand. The problem is that your installed Ubuntu will not boot (freezes) if either your ATI or Nvidia card is in place and selected by the BIOS, but it will boot if you have selected the on-board video. Is this the situation?

That is exactly it.

Boots fine as long as BIOS is set to onboard. My Nvidia or ATI and it freezes/gives me the errors if I remove the splash.

---

### Post by syn` on 2008-01-27
> **zubrug said:**
> Try this
When you get to the install options at the initial install dialogue, hit f6 and then type 
all generic ide
hit enter and good luck, this usually works for myself.

No such luck.

Still froze at the same spot.

---

### Post by syn` on 2008-01-27
Up.

---

### Post by syn` on 2008-01-28
Up.

---

### Post by syn` on 2008-01-28
Up.

---

### Post by dstew on 2008-01-28
So, it is probably the driver for your video card that is the problem. What card is currently installed? Post the content of your **/etc/X11/xorg.conf** file on the forum.

---

### Post by syn` on 2008-01-28
> **dstew said:**
> So, it is probably the driver for your video card that is the problem. What card is currently installed? Post the content of your **/etc/X11/xorg.conf** file on the forum.

Well, I've went through all 3 of my PCI cards to try and get this work and I have the same issue with every one of them.

Radeon 9200
Radeon 9250
Nvidia 6200

But I put my Nvidia in another machine, slapped in the Live CD, and it booted up fine. I take the Nvidia out, put it in this machine, I get nothing.

I formatted lastnight to put Windows in so I could do *something* with my computer. But the xorg I can tell you was still set to the onboard. And if I changed it to the ATI or Nvidia and rebooted, I just got prompted for safe graphics mode and it never recognized the ATI or Nvidia.

But I'd have to install Mint again on another partition to tell you. I haven't installed it again because the Live CD wouldn't work and it wouldn't boot up. I'll reinstall I guess real quick, tho.

---

### Post by dstew on 2008-01-28
> But I put my Nvidia in another machine, slapped in the Live CD, and it booted up fineThat proves that the card is OK, but you already knew that. The problem has to do with how the card works with the balky machine and with the Ubuntu drivers. For example, if the PCI controller is different, the card might work in one machine but not the other. It has to do with the software that runs the hardware, both card and PCI, and possibly other things.> I formatted lastnight to put Windows in so I could do something with my computer. But the xorg I can tell you was still set to the onboard. And if I changed it to the ATI or Nvidia and rebooted, I just got prompted for safe graphics mode and it never recognized the ATI or Nvidia.I don't understand. Did you install windows in the balky machine? What do you mean that the "xorg was set to the onboard"? What do you mean if you "changed it to the ATI or Nvidia"? You mean changing your BIOS, or editing the /etc/X11/xorg.conf file?
EDIT: Here is an idea. If you can boot with your BIOS set to use onboard video, and your ATI or Nvidia card in place, do so. Then we can try to reconfigure Ubuntu to detect and use the ATI or Nvidia card. Linux is designed to avoid using your BIOS once the boot starts, so we should be able to do this.

---

### Post by syn` on 2008-01-28
I had a few things I had to get done on the computer, so I reformatted and slapped Windows in temporarily. I just reinstalled Linux, tho. I'm on it right now, on the onboard. But when I logged in to boot up, it prompted me about the restricted drivers for the Nvidia. That is something that never happened with the ATI, and it's using the onboard, so maybe this is promising and we can get somewhere. 

I did read on a thread where the guy is having the same problem that someone told him to Blacklist his onboard so that it just wouldn't use it since Linux doesn't use BIOS, but I'm clueless on this stuff.

I have currently not done anything. I haven't enabled the restricted or ran Envy. The card I will be using (and want to use) is my Nvidia 6200, which is currently plugged in, but not in use at the moment. And here is my xorg.conf:

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"E151FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"E151FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by syn` on 2008-01-28
I just did what I read in another thread, or tried to. I don't know if I did it right.

But I found my way to **/etc/modprobe.d/blacklist/** and tried adding Intel to that list, hopefully forcing it to use the Nvidia. But I wasn't sure what to call the driver, so I just put intel. But I saved, rebooted and it's still using this damn Intel driver, didn't even switch to the Vesa. 

I probably did that wrong, tho.

---

### Post by dstew on 2008-01-28
If you want to get the Nvidia card going, enable the restricted drivers manager. "Restricted" refers to drivers with a restricted license, so they cannot come enabled as default in Ubuntu, which is made using open (unrestricted) software. I am not sure, but I think if you enable the restricted Nvidia driver, your system will update the /etc/X11/xorg.conf file for you. If not, we can edit it later.

---

### Post by syn` on 2008-01-28
> **dstew said:**
> If you want to get the Nvidia card going, enable the restricted drivers manager. "Restricted" refers to drivers with a restricted license, so they cannot come enabled as default in Ubuntu, which is made using open (unrestricted) software. I am not sure, but I think if you enable the restricted Nvidia driver, your system will update the /etc/X11/xorg.conf file for you. If not, we can edit it later.

OK, so, I enabled the restricted drivers for Nvidia. It downloaded them, installed, and told me I needed to restart. Upon restarting using my onboard graphics card and getting to the user login page, it told me I was running in Low Graphics Mode. I went to the graphics card tab and up top was the Intel, but running off the Vesa driver, below it the Nvidia. Here's the kicker, it said I had a **Nvidia Geforce 6800** when I infact have a 6200. Now, that might not be a big deal, but whatever.

So, before I messed around with setting the onboard graphics card back to Intel from Vesa I plugged the monitor into the Nvidia and got nothing. I selected the Intel driver for my onboard and restarted. When it got back to the user login page, it was visually messed up. Lines everywhere, kept flashing. I restarted again and it booted up. It's not in low graphics mode, but the resolution is pretty low.

So I just checked my xorg.conf and this is what I have now:

```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1280x960@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:1:4:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
```




**Edit:** I just checked the Restricted Drivers Manager again and the check next to Enabled isn't checked and it says it isn't in use. Going to check it again.

---

### Post by syn` on 2008-01-28
OK, so I enabled the restricted drivers again. Before I restarted I checked the xorg.conf and noticed that it wasn't removing the Intel from it. It was just adding the Nvidia under it. I don't know if that causes a problem or not and I'm not really sure on how to edit anything in there. 

But when I restarted, the same thing happened. I plugged it into the Nvidia and got nothing while it was booting up so I plugged it into the onboard and it brought me up in Low Graphics mode. Should I be changing the BIOS when I restart to read the Nvidia only? I did that once and it still got stuck. The Restricted Drivers Manager still has the Nvidia unchecked.

I think it has to do with the xorg, tho. I just checked it and the Nvidia and Intel are still there:


```

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1280x960@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:1:4:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1280x960@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by syn` on 2008-01-28
Up.

---

### Post by syn` on 2008-01-28
Up.

---

### Post by syn` on 2008-01-28
I decided to surf around the internet some more about the problem and eventually stumbled on a thread on some forums that lead me to quite a few others. But the threads were full of people having the same problem. Every one of them had an Intel integrated chip. It has something to do with that, and I seen various fixes, tried a few, they didn't work. 

But I figured I'd just keep this a Windows box. Going to turn the new computer into a Linux box hopefully with no troubles.

Thanks for trying to help.

---

