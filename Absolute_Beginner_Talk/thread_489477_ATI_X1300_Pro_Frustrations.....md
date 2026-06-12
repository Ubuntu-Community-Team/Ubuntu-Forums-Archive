---
title: "ATI X1300 Pro Frustrations...."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Inkpot on 2007-07-01
Hi there,

I'm a complete newbie to Ubuntu, and after installing 7.04 (Feisty), I *cannot* get my ATI X1300 Pro video card to work. I've pored over the forums here and tried every "solution" I could find (I even tried using Envy to no avail). Nothing works. I either reboot to a black screen or nothing changes at all. I am extremely frustrated at this point, and may have to forget about Ubuntu altogether if I can't get my video card to work properly. Is there anyone out there who can help me??

I am running Ubuntu dual-booted with Windows Vista on an AMD dual core 64-bit processor.

Help me Obi Wan, you're my only hope........ :P




Inkpot

---

### Post by intMain on 2007-07-01
all you have to do is enable the restricted drivers and reboot.. lol.  I have a x1400 in my acer and it works that way but now i just test the official ati linux drivers. ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI))

what happens when you just enable the restricted drivers?

---

### Post by Inkpot on 2007-07-01
Yeah...I tried that.

I rebooted and got nothing but a black screen.


Inkpot

P.S. Here is the output from my fglrxinfo:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

### Post by aznranndydraman on 2007-07-01
same problem, tried every solution I can find, but X still die with a black screen and no response to any key pressed

*btw, a lot of people who has a x1300 seems to have this issue

---

### Post by Inkpot on 2007-07-09
Please, is there ANYONE who can help me? I would be so grateful for some one on one help. I just can't solve this problem.....



Inkpot

---

### Post by serend on 2007-07-10
Same problem, some how it got fixed by using fglrx-dev drivers but i still have no dri

```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
```

II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV515
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
```

```


james@james-desktop:~$ sudo modprobe fglrx
[sudo] password for james:
FATAL: Error running install command for fglrx
```

---

### Post by Inkpot on 2007-07-10
Yes, my problem is rather similar to that one. Looks like linux is a no-go to anyone with this particular ATI card. I even looked into switiching to Mandriva, and they're having the exact same problem with it. So, it looks like I'm just going to forget about it and go back to Windows. It's too bad...I was looking forward to getting into linux, but I'm not going to throw away a perfectly good video card just because it doesn't like linux or vice versa.

Color me disappointed. :(





Inkpot

---

### Post by chrisN_uk on 2007-07-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/117013](https://bugs.launchpad.net/ubuntu/+bug/117013) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same problem here, looks like its nearly fixed though.

check out: [https://bugs.launchpad.net/ubuntu/+bug/117013](https://bugs.launchpad.net/ubuntu/+bug/117013)

---

### Post by No Whammies on 2007-07-18
I'm happy to see they're working on the problem.  I actually had to go back to Vista again because of the recurring problems with my card.  I'd find a fix, it'd work for a couple weeks, but because the drivers had problems with the card, no fix lasted.  Had to use Vista on my new comuter while my old one still has Ubuntu Edgy.  This did turn out to be a good thing though, because I'm getting experience using many different Operating Systems.  The only one I haven't tried yet is BSD, but with the problems linux has with the ATI drivers, I don't think BSD would do well on this one.

---

### Post by tahnok on 2007-07-18
I had the same problem on my ati x1400 card. I fixed though. run:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo startx
```
Hopefully this should start GDM and KDE i think (though I don't use KDE so I not really sure)
This even works on the live cd if you've got a net connection.

---

### Post by Hobo Joe on 2007-07-18
I used to have an X1300, I was never able to get it working. Not even my Linux encyclopedia friend couldn't get it to run.

It frustrated me to point that I decided to go for the new computer that I had been wanting for a while. Besides, the X1300 isn't really a great card anyway. In fact, it was barely better than the 9800 Pro that it replaced for me.

But, obviously, most people wouldn't have that option, or wouldn't be so inclined to do it. But I hear that the ATi incompatability issues are being worked on now(finally), so I would wait a bit before giving up.

---

### Post by quad3d@work on 2007-07-23
Something's wrong with the hardware... Doesn't work on Arch Linux neither. I'm using 8.32.

---

### Post by Cloud22 on 2007-07-28
Use the newest driver, 8.39.4 It fixed my black screen of death. I have tried fixing this for ever (6+ months) and this is only way it has worked. I even have DRI enabled.

---

### Post by Inkpot on 2007-07-29
FIXED!!!

Ok, looks like the new driver from ATI works! I uninstalled the old driver and installed the new one using the latest version of Envy, and now it works! One thing, though: the recommended resolution/refresh rate for my monitor is 1440X900 at 60Hz, but Ubuntu will only let me use that resolution at 30Hz. Here's my xorg info (which will reflect all of my tinkering and - most likely - screwups :P ):


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-75
	VertRefresh	43-75
  # 1440x900 @ 60.00 Hz (GTF) hsync: 60.00 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card Driver"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900_60.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Can anyone out there help me out with this last bit o' configurin'? I'M SOOOO CLOSE!!!



Thanks,
Inkpot

---

### Post by Haxd on 2007-07-29
You're almost there, I got this semi-working by doing this:

```

Section "Monitor"
	Identifier "Generic Monitor"
	Option "DPMS"
	HorizSync 30-83
	VertRefresh 56-75
		# 1440x900 @ 60.00 Hz (GTF) hsync: 60.00 kHz; pclk: 140 MHz
	Modeline "1440x900_60.00" 60.0 1440 1520 1672 1904 900 903 909 934 -HSync +Vsync

EndSection

```

The part which says 60.0 is because my monitor (dell 20inch) only supports 60 hz, and the X server does run, with the proper resolution.

Only problem is the fact that the screen is fuzzy, like there's a double image.

Tried messing with the Vert Refresh / Horizontal Sync, no changes :(

EDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDITEDIT

Okay, having the same problem as you now:

This is really annoying as I've not been able to get this card to work in widescreen at all.

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
	Modeline 	"1440x900_60.00" 60.00 1440 1520 1672 1904 900 901 904 932  -HSync +Vsync
	#Modeline 	"1440x900_60.00" 106   1440 1520 1672 1904 900 901 904 932  -HSync +Vsync
#(II) fglrx(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
#(II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904
#(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 
#(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, 
#(II) fglrx(0): Serial No: DR81276M09WS
EndSection

```

Monitor is displaying 720x400 " 68hz, I have no idea why, it's being stretched to 1440x900, and according to the screen res app, I'm running at 1440x900 @ 33hz

This is not amusing :(

---

### Post by Septor on 2007-08-01
Try removing all timing and modelines...

Your monitor section should only need:
```

Section "Monitor"
	Identifier "Generic Monitor"
	Option "DPMS"
EndSection

```

If that doesn't work, post the Xorg.0.log output here.

If you can get X up and running, try amdcccle (AMD Control Center) and check the Display options there as well.

---

