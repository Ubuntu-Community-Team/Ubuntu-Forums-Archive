---
title: "Graphic Related Problem"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by iv76erson03 on 2008-01-01
When I turned on the computer for the first time everything was working alright. after my first restart it is running so slow the text won't even keep up with my typing. i can't enable any desktop effects or anything. i'm a complete newbie and i'm getting very frustrated because it seems like nothing works.

---

### Post by JoshuaRL on 2008-01-01
Could you post your specs?

What type of computer, video card, ram, and distro.

We can start from there and see what we can do to help.

---

### Post by iv76erson03 on 2008-01-01
Guess that would help. IBM a31p Thinkpad. ATI Fire GL 7800 vid card with 1.7 P4 and 512 Ram. Using 7.10

---

### Post by JoshuaRL on 2008-01-01
Could you go into the terminal and post the output of this:

```

sudo gedit /etc/X11/xorg.conf

```

That is your configuration file for Xserver, the application that allows the GUI/desktop of your choice (yours is probably Gnome)

I want to see how well it's configured for your card.

And welcome to Ubuntu!

---

### Post by iv76erson03 on 2008-01-01
Don't know what you need so here's all of it

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200"
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
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by iv76erson03 on 2008-01-02
Also I don't know that it's a GPU problem. Also Firefox is acting slower that about every other program. Pigin is sorta normal and open office is a tad slow. These three sentances i'm writnig in this box will take about a minute to fully appear so this is reallly bad.

---

### Post by JoshuaRL on 2008-01-02
Okay, this was what I was looking for:

> 
Section "Device"
Identifier "ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection


I just wanted to make sure you were running the open source DRI drivers.  I looked through the forums and there doesn't seem to be a ton of people posting their tweaked xorg.conf files for your card.  However, there's a thread that explains what most of the tweaks mean and how you can figure what will most likely work for you:

[http://ubuntuforums.org/showthread.php?t=396671](http://ubuntuforums.org/showthread.php?t=396671)

Tell you what, try this and tell me what the output is for slot "01:00.0 VGA compatible controller" and the host bridge right under it:

```

sudo lspci -vv

```

That will be your jumping off point.  But if you just want to try something simple and see if it helps, try setting your default color depth to 16 in xorg.conf at here:

> 
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1600x1200"
EndSubSection
EndSection


Save the changes to xorg.conf and reboot.  That should make it run smoother on your card.

EDIT

Okay, I just saw your post.  Okay, can you try adding to the panel along the bottom the little app that gives a graphical output for CPU usage?  That might tell you if something is using your processor.  

For me, gnome ran my P4 2.9ghz at about 30% all the time until I went into Preferences>Administration>Indexing Preferences and turned them off.  It kind of logs what you do in an index so if you want to use desktop search it will be quicker and better.  But I never use it and I wanted the processor all to myself, so I stopped that.  Now I run at about 5-10% even with compositing and gDesklets.

---

### Post by iv76erson03 on 2008-01-02
Yeah I've been looking at hte system monitor and it's running only 15-25% and the memory is 50%. The thing that gets me is that it was running flawlessly with al lthe bells and whistles turned on when it started it hte first time and the second time it turned on it's barely operable. 

Here's this

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7] (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0518
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR+ FastB2B+
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 3000 [size=256]
        Region 2: Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
                Status: RQ=48 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

EDIT: I just jumped on Epiphany and it's a little better but there is still lag and everything else is slow.

---

### Post by JoshuaRL on 2008-01-02
Well, while I work through that try turning off indexing and rebooting to see if that helps it any.

---

### Post by iv76erson03 on 2008-01-02
Alright, i figured out part of it. I had installed the ATI binary X.org driver thinking that was smart. I guess not. I uninstalled it and restarted it and it just sped up alot. Also I can enable visual effects now. However, with the visual effects turned on it's still slow and not at all like it was before. I'm afraid my problems might be stemming from something else i did that I shouldn't have done.

How do i disable indexing?

Also, I was playing around earlier trying install a python thing (I don't even know why now) could i have screwed up my system during that process?

---

### Post by JoshuaRL on 2008-01-02
It's possible, but I'm not sure what it could be then.

Preferences>Settings>Indexing Preferences
Set it to not do any indexing.

Try the first part of this thread to completely remove fglrx:

[http://ubuntuforums.org/showthread.php?t=361136](http://ubuntuforums.org/showthread.php?t=361136)

I've heard they can wreck havoc even after they aren't being used.

---

### Post by iv76erson03 on 2008-01-02
Now I'm experiencing random log offs. When I came back this time, i got this:

The paned encoutered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"
" "OAFIID:Deskbar_Applet"
" "OAFIID:GNOME_Panel_TrashApplet"
" " OAFIID:GNOME_MixerApplet"

Is this a normal thing to have this many problems? I've been giving Ubuntu a try about every year now for the last 3 years and it seems like every time I do, the OS is so messed up after about a day that it is completely inoperable. I'll give it another couple days, but I really don't want to have an OS that I have to fix 4 times a day. Sorry to be grumpy, I just really want something that works.

---

### Post by iv76erson03 on 2008-01-02
Bump

Is there some way to revert all my settings to the way they were when i first installed or go back? This thing is deteriorating rapidly and now i'm getting random lines on the screen.

---

### Post by LowSky on 2008-01-02
your issues seem very odd, but thenagain people with ATI graphic tend to have to fight with the OS. First thing I would try is Envy, that may fix you graphics issue. 

Maybe try another version of linux, Mint is based on Ubuntu but has all the extras that most people install already added. Then theres Fedora, openSuse, PCLOS, and many more which are all free.

---

