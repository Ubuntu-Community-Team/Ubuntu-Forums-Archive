---
title: "Disabling touchpad tapping"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by dracovich on 2007-10-24
Hey guys, touchpad tapping is driving me nuts, it's hyper sensitive and i keep dragging files i didn't mean to, closing windows i'm using and generally just doing crap. After some googling, everyone was raving about how Gutsy had implemented a default touchpad tab in the mouse preferences, but sadly i can see no such thing. I saw a few non-GUI methods to do the trick which i could probably figure out how to do, but if there's suppose to be GUI method to do it i'd like to have it enabled as it would make my life easier.

So far i tried installing the qsynaptics package through the packet manager thinking maybe i just needed that to get the tab to appear, but no such luck.

---

### Post by dracovich on 2007-10-24
Anyone?

---

### Post by lazyart on 2007-10-24
omg.... i didn't know there was a touchpad tab in Mouse Preferences.  That darn vertical scroll kept rotating the cube. 

Check your bios settings?  Maybe it's emulating a mouse instead of being a synaptic device?

---

### Post by dracovich on 2007-10-24
To be honest i'm not sure what i should be looking for in BIOS but even if i did, i doubt i'd find it. I've never seen a bios with so few options. I could basically select master/slave devices and boot sequence, that was it (and and there was an option where you could select win95,98,2000,xp, vista or other as your os, i tried switching it to other but it does nothing).

I tried this as well: [http://scottcollins.net/blog/2006/01/disable-touchpad-tap-in-kubuntubreezy.html](http://scottcollins.net/blog/2006/01/disable-touchpad-tap-in-kubuntubreezy.html)

without luck.

---

### Post by ThrobbingBrain66 on 2007-10-24
> **dracovich said:**
> Hey guys, touchpad tapping is driving me nuts, it's hyper sensitive and i keep dragging files i didn't mean to, closing windows i'm using and generally just doing crap. After some googling, everyone was raving about how Gutsy had implemented a default touchpad tab in the mouse preferences, but sadly i can see no such thing. I saw a few non-GUI methods to do the trick which i could probably figure out how to do, but if there's suppose to be GUI method to do it i'd like to have it enabled as it would make my life easier.

So far i tried installing the qsynaptics package through the packet manager thinking maybe i just needed that to get the tab to appear, but no such luck.

The tab should be there....is for me anyway.  Can you post the contents of your xorg.conf? More specifically, maybe you can just cut out the section that refers to a mouse or Synaptic.
```
cat /etc/X11/xorg.conf
```

---

### Post by dracovich on 2007-10-24
Sure, here's what i have:

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device" "/dev/input/mice"
  Option      "Protocol" "ExplorerPS/2"
  Option      "Emulate3Buttons" "false"
  Option      "Buttons" "5"
  Option      "ZAxisMapping" "4 5"
  Option      "ButtonMapping" "1 2 3 6 7"
  Option      "Resolution" "800"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option 		"SHMConfig" 		"on"
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


I added the SHMConfig line earlier in order to try and fix it, the mouse part i added yesterday in order to enable the thumb button on my MX510 (the touchpad tab was missing before though as well) and i included those three references to wacom as well, as i dont have a tablet PC and figured that might be something causing the problem (although i did try commenting it out and restarting x without help).

---

### Post by NilsE on 2007-10-24
In "Configured Mouse" section change

Option "Protocol" "ExplorerPS/2"

to

Option "Protocol"		"ImPS/2"

and see if that makes a difference in the mouse menu

---

### Post by mcurtiss1970 on 2007-10-24
weird.  i have a touchpad tab in my mouse preferences where i can disable tapping.  this was enabled out of the box.

---

### Post by jsully1 on 2007-10-24
Adding ```
 Option      "MaxTapTime"    "0"
``` to the touchpad portion of xorg.conf will disable tap.

---

### Post by rorestuff on 2007-10-24
This drove me nuts too.
I use syndaemon:

[http://www.linuxcommand.org/man_pages/syndaemon1.html](http://www.linuxcommand.org/man_pages/syndaemon1.html)

To install:
```
sudo aptitude install syndaemon
```

---

### Post by NotTheMessiah on 2007-10-24
Install Touchpad from add/remove and disable tapping(System/Preferences/Touchpad

"GSynaptics is a GUI configuration tool for the Synaptics touchpad driver of the X server.
This allows for modifications of the driver parameters on the fly.
Version: 0.9.7-3 (gsynaptics)
Touchpad integrates well into the Ubuntu desktop"

---

### Post by dracovich on 2007-10-24
Tried ImPS2, didn't work

Added the MaxTapTime option under the synaptics part in xorg and it didn't work.

The syndaemon seems to be to disable it during typing, i want it disabled altogether because i keep inadvertently dragging things and clicking them when i'm just trying to move the cursor, and i never use it anyway (use the actual buttons under the touchpad).

---

### Post by dracovich on 2007-10-24
NotTheMessiah:

I did that now, uninstalled qsynaptic first and then installed gsynaptic, but it won't load it tells me:

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I did go under the synaptics driver in xorg and added the line

	Option		"SHMConfig"		"true"

But it still won't start.

---

### Post by NotTheMessiah on 2007-10-24
Try this:
```

Section "InputDevice"
	Identifier 	"Synaptics Touchpad"
	Driver 		"synaptics"
	Option 		"SendCoreEvents" 	"true"
	Option 		"Device" 		"/dev/psaux"
	Option 		"Protocol" 		"auto-dev"
	Option 		"VertEdgeScroll" 	"1"
	**Option           "SHMConfig" 		"on"**
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  	screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	**Inputdevice	"Configured Mouse"**
 	**InputDevice 	"Synaptics Touchpad"**
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection
```

---

### Post by dracovich on 2007-10-25
Sorry for the late reply, was getting late and had to hit the hey last night.

But i tried that one and it still doesn't work.

---

### Post by Tulip on 2007-10-25
Im watching this with interest - Ive got the same problem

---

### Post by NotTheMessiah on 2007-10-25
> **dracovich said:**
> Sorry for the late reply, was getting late and had to hit the hey last night.

But i tried that one and it still doesn't work.

it has to work. I went through exactly the same problem and after installing Touchpad it worked.But it is possible that i've missed some line in the xorg.conf.

---

### Post by NotTheMessiah on 2007-10-25
```

Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"	
EndSection

```

---

### Post by dracovich on 2007-10-25
Sorry man don't know what to tell you, not working for me :/

Those mouse settings are the default ones, i changed them up to get my thumb button to work. I tried reverting back to the old ones (same as you posted) and restarting x, but i still get the same error message when i try to open up the touchpad preferences.

---

### Post by NotTheMessiah on 2007-10-25
Try to reinstall it. I remember that i had to remove it and reinstall the thing a couple of times. Are you running Feisty?

---

### Post by GrayWizardLinux on 2007-10-25
not the messiah


I get this message when I try to use touchpad: you have to set 'SHMConfig' 'Ture' in xorg.conf or XF86Config to use GSynaptics.

I have no clue what to so with this info.  Can  you please be simple/basic and 

thank ytou.

I am totally a neophyte.

---

### Post by NotTheMessiah on 2007-10-25
Yes i know. I was getting the same message when i tried to install the Touchpad(front end gsynaptics) so then i edited my xorg.conf file - then removed and reinstalled Touchpad again from add/remove applications.

This is part my xorg.conf  for the touch pad

```

Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"	
EndSection

Section "InputDevice"
	Identifier 	"Synaptics Touchpad"
	Driver 		"synaptics"
	Option 		"SendCoreEvents" 	"true"
	Option 		"Device" 		"/dev/psaux"
	Option 		"Protocol" 		"auto-dev"
	Option 		"VertEdgeScroll" 	"1"
	**Option 		"SHMConfig" "on"**
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
 	**InputDevice 	"Synaptics Touchpad"**
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection
```

---

### Post by dracovich on 2007-10-25
I'll try that. And no, i'm running Gutsy (hence me wanting the pretty graphical tab :( )

---

### Post by NotTheMessiah on 2007-10-25
Well just to prove that it works here it is in action

---

### Post by GrayWizardLinux on 2007-10-25
thanks but I have no clue how to even get into this xconfig - I know terminal but after that I am lost - thanks but I guess I will keep the double tap and learn to live with it.

Thank you for your help.

---

### Post by NotTheMessiah on 2007-10-25
> **GrayWizardLinux said:**
> thanks but I have no clue how to even get into this xconfig - I know terminal but after that I am lost - thanks but I guess I will keep the double tap and learn to live with it.

Thank you for your help.

Ok this is the command BUT be very careful with the xorg(since you are a newbie)

sudo gedit /etc/X11/xorg.conf

and add the line - the one in bold and install Touchpad - in fact you can copy/paste the code

```

Section "InputDevice"
	Identifier 	"Synaptics Touchpad"
	Driver 		"synaptics"
	Option 		"SendCoreEvents" 	"true"
	Option 		"Device" 		"/dev/psaux"
	Option 		"Protocol" 		"auto-dev"
	Option 		"VertEdgeScroll" 	"1"
	**Option 		"SHMConfig" "on"**
EndSection
```

---

### Post by GrayWizardLinux on 2007-10-25
I did it as you said and it still occurs.... I cannot use it - same message appears

i just deleted all the stuff above and went back to the way it was....

---

### Post by NotTheMessiah on 2007-10-25
Did you uninstall gsynaptics(touchpad) and reinstall?

---

### Post by GrayWizardLinux on 2007-10-25
yes i did and the same message came up.

---

### Post by ugm6hr on 2007-10-25
Don't want to interfere in a stream of advice - but I think this is the issue:

in xorg.conf:

```
Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
**	Load		"synaptics"**
EndSection
```

If that doesn't help - try looking at complete xorg.conf examples - linked from my signature below "post your xorg"

Having done the edit, restart X (Ctrl-Alt-Backspace), then the "options" should work.  If you don't have GSynaptics, it can be installed from Synaptic package manager.

Please note I use Feisty, but I suspect that xorg is not loading the synaptics driver (hence the line in bold to be added).

---

### Post by NotTheMessiah on 2007-10-25
```

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
```

strange i don't have that line in my xorg

---

### Post by GrayWizardLinux on 2007-10-25
Thanks - this could be the problem and the answer - but I did a tweak from another post and it crashed my system.  I just spent the last week redoing it and tweaking and a clean install - I am not doing that again for nothing.

I will live with this hassle but at least all other stuff works.

That is the problem with linux!!!

hence why I use all macs...Not 1 freakin problem at all. everything works!

This is my experimental laptop so that I could honestly give linux a chance.

by the way I am using Mint Celena based on Ubuntu...

Thank you guys again.  But I think I am finished with this thing.

when the laptop popps out - I am done with linux I am sorry to say.  I will take what works now; but I am not reliving this experience again and also the extra cost for the laptop to run linux didn't help either.

I did and am giving this a fair shot.

but there are way too many issues and crashes and hassles when you start dealing with the dreaded 'X' aspect of linux.

Thank you again.

---

### Post by dracovich on 2007-10-25
I don't have anything called Section "Module" in my xorg.conf period :S

I added the section and kept only the line you put in bold, and restarted X, but it didn't work.

---

### Post by NotTheMessiah on 2007-10-25
Did you put  - 
InputDevice 	"Synaptics Touchpad"

in the ServerLayout section?

I don't know what else to suggest. I am stumped :(

---

### Post by dracovich on 2007-10-25
Yup that was actually there to start wit

---

### Post by dracovich on 2007-10-25
I've at least found a temporary solution which will at least stop it from being annoying when i type. It's an Alienware Sentia m3450 and pressing fn+F1 disables the touchpad in it's entirety. It's still hell to use when i actually don't ahve a mouse plugged in but at least it's that's one situation where it's not killing me.

---

### Post by NotTheMessiah on 2007-10-25
try this :
Option "SHMConfig" "1"
and restart Ctrl-Alt-Backspace

see what happens

It worked for these guys 

[http://ubuntuforums.org/archive/index.php/t-455667.html](http://ubuntuforums.org/archive/index.php/t-455667.html)

---

### Post by dracovich on 2007-10-25
Nope, no luck, tried setting it to "true" as well. Did a search on the error and i've been going through all the topics. There seem to be a few people out there that just can't get it to work :/

---

### Post by dracovich on 2007-10-25
Noone has solutions? :/

Should i file this as a bug report to the official team or something of the sort? It seems that this is a problem that i'll have to live with. It's quite annoying but not much to do about it. At the moment it's my only gripe with Ubuntu and the pluses are many more so i'm not leaving it or anything.

---

### Post by dracovich on 2007-10-25
Alright one last ditch effort to bump this to the top in case some linux god sees it and knows what my problem is :) if not i guess i just have to live with it.

---

### Post by lazyart on 2007-10-25
after you make these changes to xorg.conf, are you restarting X?

---

### Post by dracovich on 2007-10-25
yup, ctrl-alt-backspace every time i made a change (although for some reason i have to do it twice to make it restart).

---

### Post by lazyart on 2007-10-25
maybe try running the xserver configuration over again?```
sudo dpkg-reconfigure xserver-xorg
```You can do it while X is running by just opening a terminal.  Again, I didnt even know about the tab in the mouse properties until you opened this thread.  It was just there for me.

---

### Post by dracovich on 2007-10-25
Alright, went through that and edited the xorg.conf again according to the suggestions made here, but no dice :/

---

### Post by NotTheMessiah on 2007-10-25
This is annoying the hell out of me. I distinctly remmber that i had to change(SHMConfig = on,1,true which all equal to true) and restart a few times. But i can't remember what i tweaked precisely when it worked. Look, try ksynaptics - install it from the curiously named synaptic package manager :lol: u have nothing to lose :)

---

### Post by NotTheMessiah on 2007-10-25
You know what? I'll try to destroy the gsynaptics on my laptop(i'll try  to reproduce the error) and then i'll try to fix it again. I don't have time now but i'll definitely  try later today. Stay tuned

---

### Post by NotTheMessiah on 2007-10-25
Ok here we go:

I've deleted the line "SHMConfig" "on"

```


Section "InputDevice"
	Identifier 	"Synaptics Touchpad"
	Driver 		"synaptics"
	Option 		"SendCoreEvents" 	"true"
	Option 		"Device" 		"/dev/psaux"
	Option 		"Protocol" 		"auto-dev"
	Option 		"VertEdgeScroll" 	"1"	
EndSection

```

The tap-click IS back together with the error : I will try to fix it again and post the results

---

### Post by ugm6hr on 2007-10-26
> **dracovich said:**
> Tried ImPS2, didn't work

Added the MaxTapTime option under the synaptics part in xorg and it didn't work.

The syndaemon seems to be to disable it during typing, i want it disabled altogether because i keep inadvertently dragging things and clicking them when i'm just trying to move the cursor, and i never use it anyway (use the actual buttons under the touchpad).

There is clearly something unusual here.... If Syndaemon works, then the synaptic driver must be working just fine.

So why the other functions are not working is unclear.

I think the most sensible approach is for you to post your entire xorg.conf for people to see.

This is pretty useful: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

This will also give you all the info you need:
```
man synaptics
```

---

### Post by NotTheMessiah on 2007-10-26
Putting the line "SHMConfig" "on" fixed the problem - AGAIN... ....so it has to be something specific with your machines or you're doing something wrong(which i doubt)

---

### Post by dracovich on 2007-10-26
> There is clearly something unusual here.... If Syndaemon works, then the synaptic driver must be working just fine.

To clarify, i never tried the SynDaemon he suggested, as it seemed that this was advice to get it to stop from clicking as i was typing. I just want to turn of tapping all-together.

> Putting the line "SHMConfig" "on" fixed the problem - AGAIN... ....so it has to be something specific with your machines or you're doing something wrong(which i doubt)

Well don't be so sure lol, while i would classify myself as quite computer literate, i'm obviously completely new to linux and how it works. Is there a possability though that it is not detecting my touchpad as a touchpad but as some different kind of device? And if so is there any way to change this? My first thought was that maybe all those Wacom things were the culprit and it was detecting it as a tablet surface, but i commented those out and it made no difference.

I uploaded my current xorg here so you can check it out if you would like.

---

### Post by NotTheMessiah on 2007-10-26
I've seen your xorg and i will not comment on it but i'm uploading my xorg so you can see the differences

---

### Post by tommytomthms5 on 2007-10-28
question are touchpads even fully supported in general??? if not then why the fluxbox do they advertise that it works oh so perfectly on laptops????

i just wanna shove a screwdriver through that damn pad already

---

### Post by tommytomthms5 on 2007-10-28
ok being as how theres absolutly no way to stop my wild mouse from being retared im going back to M$ winblows

---

### Post by jsully1 on 2007-10-30
Everyone's making this much more complicated than it needs to be!  To disable the tap function only, and leave the touchpad working, all you need to do is add a single line to xorg.conf

Here is the relavant bit:

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizEdgeScroll" "0"
**_        Option      "MaxTapTime" "0"_**
EndSection

To help, here is my complete xorg.conf, which also enables the use of the middle mouse button as a scroll, like how it works with thinkpads in Windows.

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "on"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
        Option      "EmulateWheel" "true"
        Option      "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizEdgeScroll" "0"
        Option      "MaxTapTime" "0"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "TexturedVideo" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1400x1050"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "1"
EndSection
```

---

### Post by NotTheMessiah on 2007-10-30
"Everyone's making this much more complicated than it needs to be!"

Not really..at least not 'us'...because you still need a configured mouse, and still need to add individual lines of code(and this didn't work for me which is why i installed the 'Touchpad' front end in the first place
So it is definitely complicated(unnecessarily -but not by us). People don't expect to start messing with code on their very first brush with Ubuntu(screen resolutions, synaptics touchpad etc). That is the point....it should be done in a seamless fashion(not all people like to 'hack' their os they may just want the thing to work.They are not asking for much.

---

### Post by jsully1 on 2007-11-01
I understand that it should be configurable via the GUI, however adding a single line to xorg.conf is very very simple - and  simpler than some of the other proposed solutions.  That's all I was commenting on.

---

### Post by NotTheMessiah on 2007-11-07
> **jsully1 said:**
> I understand that it should be configurable via the GUI, however adding a single line to xorg.conf is very very simple - and  simpler than some of the other proposed solutions.  That's all I was commenting on.

Adding a single line to xorg didn't work for some people - that is what i was saying. So they tried to install the GUI which again didn't work. It is simple BUT when it WORKS :) Cheers

---

