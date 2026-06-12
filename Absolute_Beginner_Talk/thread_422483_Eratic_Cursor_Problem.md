---
title: "Eratic Cursor Problem"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by rnurick on 2007-04-25
I noticed an intermittent problem with the mouse arrow cursor at times on computer monitor. It sometimes acts erratic and I can't get it to stop moving, or it will zip across the screen by itself.

Another problem that appears to be similar in nature is when I viewing web pages in Firefox. This time it's not a cursor problem but a web browser probem, when the web page I'm on will scroll out of control, over and over unless I press the ESC key or just wait it out, or simply exit out of the program. I've noticed this problem with other Linux distributions with the same results, so I'm not faulting anything. 

I'm hoping that there is a setting somewhere or a configuration script that I can add to or edit to prevent this problem. Being a new user, I also don't want to mess anything where I would need to re-install everything. If I have to, I would just simply live with the problem.

Just to add, I never experienced this problem using WindowXP, but then that's probably because of the differences between the two OSes. Believe me, other than the minor problems i've experienced, I have enjoyed and will continue to use Linux and Ubuntu as my main OS. I will only continue to keep Windows on my hard drive double-booted until I can find a way to use some specific programs I like to use that I haven't been able to get to work in Linux. 

I'm hoping that someone has a clue on what's happening and has an answer that will fix this thing once and for all. I'm not sure if this will help, but my graphics card is a Radeon R100 QD 7200. The processor is an AMD 1.1 Ghz Athlon, and I have 1.5 gb of SDRAM for the motherboard, of which I don't know what type it is. I know that this model computer is a Gateway. I also have my monitor configured at 1024 x 768 at 60 hz since it's the best rate for the Gateway monitor. 

Thanks in advance.

---

### Post by Jussi Kukkonen on 2007-04-25
I don't think this has anything to do with you display or the graphics card. An input device problem would explain all of your symptoms... Are you using some unusual keyboard or mouse? Can you try replacing either?

---

### Post by rnurick on 2007-04-25
Thanks for answering my post as quickly as you did. I'm just using a standard computer mouse with a PS2 connector that came with the computer when I received it. No special hardware that I'm aware of. I have a question for you: have you ever had a problem like I experienced? I've not talked to a lot of Linux users, so I don't know if anyone even has had the same problem.

---

### Post by rnurick on 2007-04-25
I'll try to see if I can swap out a mouse in the meantime or check and see what else I've got hooked up on this system.

---

### Post by Jussi Kukkonen on 2007-04-25
> **rnurick said:**
> Thanks for answering my post as quickly as you did. I'm just using a standard computer mouse with a PS2 connector that came with the computer when I received it. No special hardware that I'm aware of. I have a question for you: have you ever had a problem like I experienced? I've not talked to a lot of Linux users, so I don't know if anyone even has had the same problem.
Well, not the exact same situation. I know that e.g. bluetooth keyboards/mice can get "stuck" -- as in the computer thinks that a arrow key is constantly pressed when in fact the "key up" event was just lost in transmission.

It does sound very odd for something like your hardware, but I really cant think of anything else that could explain constant scrolling or mouse movement...

---

### Post by rabble on 2007-05-20
I have the exact same problem.
No idea what's causing it, but ... maybe good to let someone know you problem is not isolated to you alone.

---

### Post by mrjoey on 2007-06-20
My mouse problem just started. I run edgy, and the cursor always wants to be in the lower left hand corner. I just installed wine and IE4. I'm using a Thinkpad T21. At first, I could plug in an external mouse to fix the problem...that no longer works.

---

### Post by shabri on 2007-08-04
> **mrjoey said:**
> I'm using a Thinkpad T21

I have this problem too and I'm using a Lenovo 3000 C200, so maybe this points to a particular piece of hardware?

I'd be very grateful for a fix - this is the only gremlin I have in an otherwise excellent Ubuntu set up.

:confused:

---

### Post by skyemoor on 2007-08-20
I also have the exact same problem of the cursor/pointer suddenly zipping off to one side (or corner) just to zip to another side moments later.  I started out only doing this for a few seconds,  gradually increasing to minutes now, making this laptop virtually unuseable.

I undocked the laptop and started using the touchpad.  The problem seemed to go away, thought it has started again.  I'm wondering if it has anything to do with the temperature, because it only seems to do this after it has warmed up and the fan starts coming on longer intervals.

Dell Latitude C810
Feisty 7.04
basic xconf
external LCD monitor

Code:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file) 
# 
# This file was generated by dexconf, the Debian X Configuration tool, using 
# values from the debconf database. 
# 
# Edit this file with caution, and see the xorg.conf(5) manual page. 
# (Type "man xorg.conf" at the shell prompt.) 
# 
# This file is automatically updated on xserver-xorg package upgrades *only* 
# if it has not been modified since the last upgrade of the xserver-xorg 
# package. 
# 
# If you have edited this file but would like it to be automatically updated 
# again, run the following command: 
#   sudo dpkg-reconfigure -phigh xserver-xorg 

Section "Files" 
	Fontpath	"/usr/share/fonts/X11/misc" 
	Fontpath	"/usr/share/fonts/X11/cyrillic" 
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled" 
	Fontpath	"/usr/share/fonts/X11/Type1" 
	Fontpath	"/usr/share/fonts/X11/100dpi" 
	Fontpath	"/usr/share/fonts/X11/75dpi" 
	# path to defoma fonts 
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" 
EndSection 

Section "Module" 
	Load		"i2c" 
	Load		"bitmap" 
	Load		"ddc" 
	Load		"extmod" 
	Load		"freetype" 
	Load		"glx" 
	Load		"int10" 
	Load		"vbe" 
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

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"stylus" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"stylus" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"eraser" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"eraser" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"cursor" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"cursor" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "Device" 
	Identifier	"nVidia Corporation NV11 [GeForce2 Go]" 
	Driver		"nvidia" 
	Busid		"PCI:1:0:0" 
	Option		"AddARGBVisuals"	"True" 
	Option		"AddARGBGLXVisuals"	"True" 
	Option		"NoLogo"	"True" 
EndSection 

Section "Monitor" 
	Identifier	"HC194D" 
	Option		"DPMS" 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"nVidia Corporation NV11 [GeForce2 Go]" 
	Monitor		"HC194D" 
	Defaultdepth	24 
	SubSection "Display" 
		Depth	1 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	4 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	8 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	15 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	16 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
	SubSection "Display" 
		Depth	24 
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"	"640x400" 
	EndSubSection 
EndSection 

Section "ServerLayout" 
	Identifier	"Default Layout" 
  screen "Default Screen" 
	Inputdevice	"Generic Keyboard" 
	Inputdevice	"Configured Mouse" 
	Inputdevice	"stylus"	"SendCoreEvents" 
	Inputdevice	"cursor"	"SendCoreEvents" 
	Inputdevice	"eraser"	"SendCoreEvents" 
EndSection 

Section "DRI" 
	Mode	0666 
EndSection

```

---

### Post by Ryandor on 2007-10-03
I too, have this same issue, however it's slightly different. It didn't do this at all under 7.04, only since I've installed 7.10 beta. It doesn't jump across the screen, but it just seems to lose track of where it's at vs. where I am clicking. It will sometimes be off by 100 pixels or less. When clicking buttons it just seems to be "off" a bit, but it does click in the right spot. .. As I'm typing this it appears every 15 seconds or so, the keyboard lags badly. It appears that there is something polling the system in background which interferes with the input. Any ideas what would cause this?
Specs: HP Compaq NC6220 laptop: Pentium M 1.73MHz, 1 GB ram. The mouse is a Dell branded OEM mouse (detected as "Logitech Optical USB Mouse")

My knowledge is fairly basic, but I do have a tiny clue.. top shows Xorg averages about 4-8% but jumps to about 20% about once every 15-20 seconds. Not sure if that's related or not. There's also a couple other processes that jump for a second every now and then too. Top probably isn't the best way to figure this out, but like I said, I have only a tiny clue as to what I am doing.

On another note, I will have to say that I am very appreciative of all the help I've gotten through the forums here, even though I've not really posted anything. Everyone is very helpful here!

-Ryandor

---

### Post by CarVac on 2007-10-21
When I'm in Firefox, and a page takes a while to load, the mouse cursor simply vanishes. This has happened over three distributions: edgy, feisty, and gutsy. I usually don't use Firefox, but since Opera hasn't come out, I have to use it. What could be the problem?

---

### Post by raucous1 on 2007-10-21
I am having a similar problem. I am running Gutsy Gibbon 7.10 on a Compaq/HP NC6220.

The problem seems to happen whenever I close the lid of my computer and then reopen it (the power option is set to just blank to the screen). After opening the lid again, the computer will become much slower, and the mouse cursor will become quite erratic (just using the touchpad). The entire computer seems to become sluggish, then act normal for 5-10 seconds, and then act sluggish again. Any suggestions?

---

### Post by blinxdk on 2007-10-29
> **raucous1 said:**
> I am having a similar problem. I am running Gutsy Gibbon 7.10 on a Compaq/HP NC6220.

The problem seems to happen whenever I close the lid of my computer and then reopen it (the power option is set to just blank to the screen). After opening the lid again, the computer will become much slower, and the mouse cursor will become quite erratic (just using the touchpad). The entire computer seems to become sluggish, then act normal for 5-10 seconds, and then act sluggish again. Any suggestions?

Unfortunately no suggestion, but I have the exact same problem with my nc 6220.

---

### Post by raucous1 on 2007-10-29
> **blinxdk said:**
> Unfortunately no suggestion, but I have the exact same problem with my nc 6220.

Honestly, I downloaded the latest version of openSuse (10.3) and it has been working very well! (I tried both the gnome and kde versions, and settled on the KDE)

I really like ubuntu, but upgrading to Gutsy nuked this computer. I probably could have downgraded back to feisty, but this experienced kinda soured me. Luckily Suse is pretty good, I would recommend checking it out.

---

### Post by bojo42 on 2008-01-03
hello i also did have a jumping cursor from time to time on my nc6220 and xserver crashes which seems related to a cursor problem. please see this bugreport [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/153466](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/153466) for further informations.

cheers

---

### Post by Jim BruceJ8PM9 on 2008-02-02
> **rnurick said:**
> I noticed an intermittent problem with the mouse arrow cursor at times on computer monitor. It sometimes acts erratic and I can't get it to stop moving, or it will zip across the screen by itself.

Another problem that appears to be similar in nature is when I viewing web pages in Firefox. This time it's not a cursor problem but a web browser probem, when the web page I'm on will scroll out of control, over and over unless I press the ESC key or just wait it out, or simply exit out of the program. I've noticed this problem with other Linux distributions with the same results, so I'm not faulting anything. 

I'm hoping that there is a setting somewhere or a configuration script that I can add to or edit to prevent this problem. Being a new user, I also don't want to mess anything where I would need to re-install everything. If I have to, I would just simply live with the problem.

Just to add, I never experienced this problem using WindowXP, but then that's probably because of the differences between the two OSes. Believe me, other than the minor problems i've experienced, I have enjoyed and will continue to use Linux and Ubuntu as my main OS. I will only continue to keep Windows on my hard drive double-booted until I can find a way to use some specific programs I like to use that I haven't been able to get to work in Linux. 

I'm hoping that someone has a clue on what's happening and has an answer that will fix this thing once and for all. I'm not sure if this will help, but my graphics card is a Radeon R100 QD 7200. The processor is an AMD 1.1 Ghz Athlon, and I have 1.5 gb of SDRAM for the motherboard, of which I don't know what type it is. I know that this model computer is a Gateway. I also have my monitor configured at 1024 x 768 at 60 hz since it's the best rate for the Gateway monitor. 

Thanks in advance.
I am using Ubuntu 7.10-Gutsy Gibbon.  I was using Vista on this Acer 3680 notebook.  I was having trouble with episodes of the cursor jumping all over the screen, usually leading to me inserting text somewhere I didn't want it.  On a notebook forum I discvoered references to the use of the mouse and touchpad together was the cause of such a problem.  I found an icon of a "finger and touchpad" on the F7 key, so used FN-F7 to disable the touchpad.  That solved the problem  My hands rest over the keypad and I was brushing it, causing cursor movement I didn't expect.  Hope this helps the  hyperactive mouse problem for someone else too.  BTW I have been using Linux for less than a week and am entrhalled by the speed and simplicity of the system.   Now I want to learn the thing inside out....Jim

---

### Post by JæKæ on 2008-03-11
Same problem here. It seems to be only laptops with a USB mouse plugged in. So just disable part of the touchpad function, should fix it. 
Here's what I did:

System > Preferences > Mouse
Touchpad tab > untick 'tap to click'

---

