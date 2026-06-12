---
title: "Display colors swapped: Red is the new Blue (and vice-versa)?!"
date: 2007-04-17
forum: Apple PPC Users
---

### Post by SubGothius on 2007-04-17
[I just got Xubuntu 6.10 Edgy installed and running on an "OldWorld" PowerPC Mac](http://ubuntuforums.org/showthread.php?p=2419715#post2419715) (Umax S900 dual-200 604e -- a PowerMac 9500/9600 MP clone) with the stock ixMicro/IMS TwinTurbo 128+ video card ("imsttfb", same stock card Apple supplied in the Power Mac 9500/9600), took me a while to realize why my colors appeared somewhat strange... It appears that my Red and Blue channels/components/values have been swapped!

I.e., Red things are blue and vice-versa, and other blended values are altered accordingly; e.g., yellow smileys appear cyan, hex value #00FF00 is correctly green, but #FF0000 produces blue, and #0000FF produces red! I know my monitor, cable, and vidcard are fine, as everything still displays fine when booted back in Mac OS 9.  BTW, this uses the weird Mac wide-D VGA connector pinouts (later, NON-sync-on-green type) for what's essentially a VGA signal (in fact, the video-in port on the back of my Apple Multiple Scan 1705 Display has a VGA-type compact-D pinout; the cable is Mac wide-D on one end and VGA compact-D on the other).

The only clues I've been able to find on this suggest it may be an Endian issue, perhaps a limitation/bug in fbdev (tho' my xorg.conf specifies the "imstt" driver, and I've tried setting "UseFBDev" to "false"), perhaps PPC-specific...?

Whaaa... :confused: Anyone got a quick fix for this?

---

### Post by kornhead127 on 2007-04-17
I've completely forgotten how to fix this problem. It has something to do with bigendian (RGB) and littleendian (BGR). You've stated that green is always the same, and as you can see BGR and RGB both have green in the center but blue and red are mixed up. I'll try to look for a fix gimme second, unless you figure it out yourself.:KS

---

### Post by kornhead127 on 2007-04-17
Ok you can try this, but I'm not sure if it will work. Open a terminal from the xubuntu menu or right lcikcing desktop, and type this.

```
sudo mousepad /etc/X11/xorg.conf
```

Scroll to the Device section and add this

```
Option "SubPixelOrder" "RGB" 
```

Hopefully that helps.

---

### Post by fkdev on 2007-04-17
You could also try this (though if kornhead's suggestions works please just ignore me):

edit xorg.conf:
```
 nano /etc/X11/xorg.conf 
```

change
```
 DefaultDepth 24 
```

to 
```
 DefaultDepth 16 
```

I remember than when I was testing out the fbdev driver one day, the colors were screwed up in 24 bit depth mode.

---

### Post by SubGothius on 2007-04-18
Switching to 16-bit color as my default worked to unswap my color values, but of course it's only 16-bit color, and I'd prefer to get full 24-bit color working properly.  Tho' I will kinda miss that warmly Hellish red-orange login screen and other items... :twisted:  Guess I'll hafta look into creating a Theme to recapture that look "properly".

Adding that **Option "SubPixelOrder" "RGB"** line to my xorg.conf framebuffer "Device" section did not fix things in 24-bit color (and was irrelevant in 16-bit color), and I tried other permutations: placing it before and after the "UseFBDev" line, "UseFBDev" "true" vs. "false", "SubPixelOrder" "BGR" vs. "RGB", etc.

BTW, what's this fbdev and what's a "true" vs. "false" value do?  Doesn't seem to have any noticeable effect to me... well wait, cursory experimentation suggests that UseFBDev=false might resolve some annoying Xfce Panel issues for me (e.g., apps not launching from the menu, panel freezes, etc.)  FWIW, my xorg.conf framebuffer "Device" section specifies "driver" "imstt"

Keep thinking!  I sense imminent color winnage here... \\:D/

BTW, the relevant section of my xorg.conf (working in 16-bit color):
```
Section "Device"
	Identifier	"Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128]"
	Driver		"imstt"
	Option		"UseFBDev"		"false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-62
	VertRefresh	60-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by SubGothius on 2007-04-19
{Bump}
I know yr all prolly getting yr greedy li'l hands on Feisty right now, but... :roll: Anyone?  Bueller...? :-k

---

### Post by kornhead127 on 2007-04-20
Wow, this is way over my head to try and solve right now. 

BTW, You ever tried zenwalk?

---

### Post by anders_gud on 2007-04-20
> **SubGothius said:**
> 
Whaaa... :confused: Anyone got a quick fix for this?

Have you tried: 
depth 32

The card should support it... also check if the card is in the right PCI slot (1 or 2, weird PCI bus on those clones). Long time ago - I could be wrong.
Had to swap the twinturbo on my Umax S900 to a 3dfx voodo...


Some links:
[http://www.xlr8yourmac.com/tips/umaxS900tips.html](http://www.xlr8yourmac.com/tips/umaxS900tips.html)
[http://lowendmac.com/supermacs/s900.shtml](http://lowendmac.com/supermacs/s900.shtml)

---

### Post by abtabt on 2007-04-25
hello truble with imstt card  ???

i cant se any BusID in your xorg.conf file  ??? you most have that

its a tricky card  not easy too configure

but you can tray this do a 

reconfigure on the x.org file 

then put in under

Section  "Screen"

 DefaultDepth  24 

 DefaultFbBpp  32  



and under SubSection "Display"

                  Depth          24
                  Modes        "1024x768" (or what want  but only one )



tray this and report

---

### Post by SubGothius on 2007-04-25
Thx for the tip -- I will try the modifications to the "Screen" and "Display" sections you recommend.

I have been advised that, having only one video card, I do not need to specify any BusID, and that has seemed to work fine in every mode except 24-bit color.  Earlier, when X was not working properly at all, I ran "lspci -x" which said my video card is at 00:0e.0 on the PCI bus -- so that should be equivalent to PCI:0:14:0 in my xorg.conf, yes? However, X refused to start with that BusID setting, saying it can't find the expected device at PCI:0:14:0 ... :confused:

So far, I have the best results without any BusID at all.  I just want to get full 24-bit color working!  I will try your other suggestions.  Thx much!

BTW, aside from X, I suspect my "console" type output (i.e., before X starts, or where X is not running) is displaying as black text on a black background -- my monitor seems to be getting a signal (it doesn't go into no-signal sleep mode), and I can see the edges of a light-black box filling most of the screen, presumably representing the all-black text console output ([Please post tips on this issue here](http://ubuntuforums.org/showthread.php?t=423267)).

---

### Post by kornhead127 on 2007-04-27
try this.

When grub loads up, you might have to press [esc]. Press [E] on the kernel line and add to the end this...
```
vga=792
```

Hope that works.

-=]Rob Swift[=-

---

### Post by SubGothius on 2007-04-28
Can't use grub on an OldWorld PPC Mac, but is that vga=792 a kernel argument?  Something I could pass along with the **root=/dev/sdb4 video=imsttfb**...(etc.) stuff in my BootX bootloader?  Hm, might just try it that way anyway, along with those other things now...  Thx!

**Update:**The vga=792 thing wasn't necessary (but might also have worked?  What does it do anyway?).  Spec'ing these two lines in the "Screen" section of my xorg.conf finally did the trick:```
DefaultDepth 24
DefaultFbBpp 32
```(no mods to the "Display" section required, just used existing Depth 24 subsection as-is :) ).  Inferring that "FbBpp" means "framebuffer bits per pixel", am I right in thinking this makes the vidcard send a 24-bit color signal, but internally processing it in 32-bit mode, so it can use the 8-bit "overhead" while still keeping within the fully-accelerated 24-bit mode supported by the imstt driver?  At any rate, this means that I (and others in similar straits) finally have full 24-bit color! \\:D/

Muchthxwise to all! ;D

Now, if only I could figure out why [all my console screens (e.g. boot messages and F-key virtual consoles) seem to be all-black-on-black](http://ubuntuforums.org/showthread.php?t=423267)...

---

### Post by abtabt on 2007-04-28
if you have truble with the boot and cant see  the boot process (black sreen) or other problem

tray to set kernel arg in bootex like this exampel

video=imsttfb:vmode:17,cmode:32 root=/dev/sdb6     (use your own vmode cmode and root comands)

ex
imsttfb     (ims card driver if you use a another card you must use a nother like atyfb etc)

vmode:xx    (sets the resulution like 1024x768 75hz     xx is the number of the res  )
 
cmode :xx   (sets the bit for color   xx is the number of the 8 15 16 24 or 32 (bit 15 is a od only some ppc use that)


to find the right pci number of the video card do a 

lspci

 then you get all card you got on pci bus

but it reports in other form like  00.0d.00

a=10 b=11 c=12 d=13 e=14 
 
a reflection
 thats a lot of imscard  (i now 3 diffrents card and the xconfig is not the same on them)

---

