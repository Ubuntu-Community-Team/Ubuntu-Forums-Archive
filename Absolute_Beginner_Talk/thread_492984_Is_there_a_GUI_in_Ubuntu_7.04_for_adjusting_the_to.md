---
title: "Is there a GUI in Ubuntu 7.04 for adjusting the touchpad mouse?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-07-05
My touchpad mouse is very jittery in Ubuntu 7.04. I have a dual boot with Win98, and the touchpad works fine there. But in Ubuntu, it jumps all around at the least touch, and it moves too fast. I want to slow it down and make it more stable.

Is there a GUI for mouse adjustment? Or even a command line-type adjustment? I would prefer to use a GUI if it exists for this purpose.

---

### Post by Raineer on 2007-07-05
System / Mouse / Motion   menus should get what you want, right?  This is a gui that adjusts mouse sensitivity, threshold, and acceleration.

---

### Post by wastedfluid on 2007-07-05
The System->Mouse->Motion works.  try 'sudo apt-get install gsynaptics' 

then when you run it, you have to add a line to /etc/X11/xorg.conf's "input devivce" for your touchpad.

```

        Option          "SHMConfig"             "true"

```

This is what mine looks like afterwards.. .

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection


```

Hope this helps.  Gsynaptics is a lot more advanced, and allows for a lot of options to be changed/set "on the fly"

Enjoy.

---

### Post by swarup on 2007-07-05
> **wastedfluid said:**
> The System->Mouse->Motion works.  try 'sudo apt-get install gsynaptics' 

then when you run it, you have to add a line to /etc/X11/xorg.conf's "input devivce" for your touchpad.

```

        Option          "SHMConfig"             "true"

```

This is what mine looks like afterwards.. .

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection


```

Hope this helps.  Gsynaptics is a lot more advanced, and allows for a lot of options to be changed/set "on the fly"

Enjoy.

Many thanks to both you and raineer. The mouse GUI is great-- it solved that very problem I was writing about. Now, I do have another mouse problem, which I have not been able to solve. The mouse GUI which Raineer mentioned solved the motion problem, but does not address this next prolem.  I am wondering whether the "gsynaptics" you are recommending to me will solve it. 

Here is the problem: my touchpad mouse does not work for "click and hold" ie to grab things. The only way I can grab things is to hold down the left click button. The other way of doing it--double tapping the touchpad and holding down on the second tap--does not work. Does the "gsynaptics" application have a place in it where I can enable this? I would really like to have that feature working. Thanks!

---

### Post by swarup on 2007-07-05
> **wastedfluid said:**
> The System->Mouse->Motion works.  try 'sudo apt-get install gsynaptics' 

then when you run it, you have to add a line to /etc/X11/xorg.conf's "input devivce" for your touchpad.

```

        Option          "SHMConfig"             "true"

```

This is what mine looks like afterwards.. .

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection


```

Hope this helps.  Gsynaptics is a lot more advanced, and allows for a lot of options to be changed/set "on the fly"

Enjoy.

"then when you run it, you have to add a line to /etc/X11/xorg.conf's "input devivce" for your touchpad."

Could you spell it out a little more for a beginner like me-- I can't run the program because it gives an error saying I need to do what you are saying to do. But how do you add the line you are saying to add, without running the program? Is there some configuration window I open in terminal in order to add this line? What is the first command to get the process started?

---

### Post by wastedfluid on 2007-07-05
> **swarup said:**
> "then when you run it, you have to add a line to /etc/X11/xorg.conf's "input devivce" for your touchpad."

Could you spell it out a little more for a beginner like me-- I can't run the program because it gives an error saying I need to do what you are saying to do. But how do you add the line you are saying to add, without running the program? Is there some configuration window I open in terminal in order to add this line? What is the first command to get the process started?



Sure.  My apologies.  

Go to a terminal.

Type in:

```

sudo gedit /etc/X11/xorg.conf

```

Look for this line in GEDIT:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"

```

After you find this line, it'll probably look something like this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

Just add in the line: 

```

	Option		"SHMConfig"		"true"

```

Your finishing product should look something like this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection

```

Hope this helps!

---

### Post by wastedfluid on 2007-07-05
> **swarup said:**
> Many thanks to both you and raineer. The mouse GUI is great-- it solved that very problem I was writing about. Now, I do have another mouse problem, which I have not been able to solve. The mouse GUI which Raineer mentioned solved the motion problem, but does not address this next prolem.  I am wondering whether the "gsynaptics" you are recommending to me will solve it. 

Here is the problem: my touchpad mouse does not work for "click and hold" ie to grab things. The only way I can grab things is to hold down the left click button. The other way of doing it--double tapping the touchpad and holding down on the second tap--does not work. Does the "gsynaptics" application have a place in it where I can enable this? I would really like to have that feature working. Thanks!

By "click and hold" - you mean drag and drop?  Double tapping the touchpad is probably disabled.  If you get Gsynaptics up, you can enable "tapping" on the touchpad.  Gsynaptics has it's own "tapping" tab - that should fix the tapping issue for you.

Hope this helps!

---

### Post by swarup on 2007-07-06
> **wastedfluid said:**
> Sure.  My apologies.  

Go to a terminal.

Type in:

```

sudo gedit /etc/X11/xorg.conf

```

Look for this line in GEDIT:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"

```

After you find this line, it'll probably look something like this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

Just add in the line: 

```

	Option		"SHMConfig"		"true"

```

Your finishing product should look something like this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection

```

Hope this helps!

I entered the command line as per your direction: sudo gedit /etc/X11/xorg.conf

However, in the output there was no line appearing like this:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"

There were lots of lines reading: Section "InputDevice", but none of them had an identifier of "Synaptics Touchpad". Maybe that's why my touchpad is not working correctly.

The closest thing to a touchpad in the output was the identifier, "Configured Mouse". See below, where I've pasted that ouput. Has Ubuntu gotten confused that my touchpad is a traditional mouse? And is that why my touchpad is not working right?


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

 And yes, that is what I meant--my touchpad will not "drag and drop". Or, for example, it cannot grab a scrollbar and move it up and down. In order to grab the scrollbar, I have to use the left click button. By tapping twice on the touchpad and then holding on the second tap, it will not grab onto the scrollbar. It will not grab onto anything and move or drag it.

---

### Post by swarup on 2007-07-06
Anyone have any idea why in gsynaptics, in /etc/X11/xorg.conf there is no "input devivce" for my touchpad? 

See previous notes for further detail.

---

### Post by zabien1970 on 2007-07-06
Don't know if this will help but I found this
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by swarup on 2007-07-06
> **zabien1970 said:**
> Don't know if this will help but I found this
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Actually the link you sent me was, I believe, very much needed. Because the Touchpad up till now was not even listed as an Input Device in the /etc/X11/xorg.conf file. And this link gives the instructions of how to add it. The link describes that this will need to be followed in Dapper in order to make the Touchpad work. Although it does not state anything there about 7.04, it seems obvious since my 7.04 did not have it either, that I should have to add it. And I did-- I added the below lines to the xorg.config file as directed:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection

And I also added

        InputDevice     "Synaptics Touchpad"

at the end of the xorg.config file, under the Section "ServerLayout", as directed. And then I saved the changes to the xorg.config file and closed out of the file.

But STILL, my touchpad is not working for drag and drop. Help!! This is the very problem I am trying to solve, and adding all the above doesn't seem to have made a bit of difference.

I've loaded GSynaptics to try and see if that will help, but when I try to start the application, it gives the below error message.

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

But I already did what it is saying to do (set SHMConfig to "true"). 

So how can I get my Synaptics Touchpad to start working right?? And how can I get GSynaptics to run???

---

### Post by macogw on 2007-07-07
I'm rather surprised that no one else has said it, but you probably have a touchpad that isn't a Synaptics touchpad which is why Synaptics Touchpad isn't in your xorg.conf and why GSynaptics doesn't work.  Google a bit and see what kind of touchpad is on your laptop.

---

### Post by zabien1970 on 2007-07-07
You could check using "cat /proc/bus/input/devices"  mine shows an alps touchpad yet these settings still work for me,  The directions in the link show setting 'SHMConnfig' 'on', I had to set it to 'true' though to get it to work, further down in the link there are some changes for different touchpads, maybe try them.

---

### Post by swarup on 2007-07-07
> **zabien1970 said:**
> You could check using "cat /proc/bus/input/devices"  mine shows an alps touchpad yet these settings still work for me,  The directions in the link show setting 'SHMConnfig' 'on', I had to set it to 'true' though to get it to work, further down in the link there are some changes for different touchpads, maybe try them.

I was pretty sure it is a Synaptics Touchpad, and the command you suggested confirms it (see below). It is true, as you say the directions in the link show setting 'SHMConnfig' 'on'. My touchpad would not work (would not drag and drop) using that setting, so I had tried changing it to "true", and it did not make any difference. You mention changes for different touchpads further down in the link, but since mine is in fact a Synaptics Touchpad, I don't think these other changes should be needed. 

I know my touchpad works fine, because my laptop has a dual boot with Win98 and the Touchpad works normally there. So any suggestions anyone?? I would really like to get this touchpad working. And when the above link was suggested to me, I thought that was surely the solution-- but STILL it isn't working. Any help at this juncture would be really gratefully accepted. Thanks!


I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

---

### Post by zabien1970 on 2007-07-07
If you go to System>Preferences> does it show 'Touchpad' in the list?
 Also, does the Touchpad work at all or is it just certain features like dragging that aren't working?

---

### Post by zabien1970 on 2007-07-07
I found another link that is extremely informative (although it deals mainly with the alps touchpad) It may also work for you, it gives alot of details and may be worth checking out.
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Post-Installation](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Post-Installation)

---

### Post by zabien1970 on 2007-07-07
On second look it deals with synaptics touchpads also,

---

### Post by swarup on 2007-07-07
> **zabien1970 said:**
> If you go to System>Preferences> does it show 'Touchpad' in the list?
 Also, does the Touchpad work at all or is it just certain features like dragging that aren't working?

Replies to your questions:

1. If you go to System>Preferences> does it show 'Touchpad' in the list?

Yes, it does. But if I click on it to open it, then it just continues to give me an error message saying I need to  set that setting to "true" (in the config file), which I've already done. 

2. Also, does the Touchpad work at all or is it just certain features like dragging that aren't working?

The Touchpad works. I've been using Ubuntu 7.04 for two months now, and it has been working ever since I loaded Ubuntu. But there are two principle problems with the way it functions:
    A) The dragging function does not work
    B) The cursor is not stable. If I just touch the Touchpad, the cursor gets all jumpy. So when I try to click on things, sometimes I miss what I am trying to click and end up clicking on something else. Because the cursor is not so stable and easy to control, as it is in my Win98. I tried adjusting the settings to "slow" in the Mouse options under preferences, but it hasn't really made much difference.

Thanks for the other link you just gave me. I'll go there now and see what information it may have.

---

### Post by swarup on 2007-07-07
Could someone please take a look at this link which Zabien1970 has referred me to ([http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Post-Installation](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Post-Installation)) and let me know if, having Ubuntu 7.04, I need to go through everything described there in order to get my Synaptics touchpad working? I would have thought this Touchpad should have worked out of the box with Ubuntu 7.04. Anyhow, the drag and drop function is not working. 

For example, the above mentioned link says one has to do the below (plse see below) in order to move ahead with Synaptics Touchpad installation. Is it really the case that Ubuntu 7.04 would not have  CONFIG_INPUT_EVDEV and CONFIG_MOUSE_PS2 ??

Thanks!

(see below)

In any case, assuming you have the right kernel version, the configuration is simple. Just make sure you have both CONFIG_INPUT_EVDEV and CONFIG_MOUSE_PS2 either on or available as modules.
Linux Kernel Configuration: Enable synaptics support

Device Drivers --->

   Input Device Support --->
       <*> Event Interface
       [*] Mouse --->
               <*> PS/2 mouse

Install your new kernel and reboot. If you built them as modules, run modprobe psmouse and modprobe evdev to load them. Add these module names to /etc/modules.autoload.d/kernel-2.6 in order to have them load on boot. Once the kernel is running with psmouse and evdev support, we're ready to install the Xorg driver.

---

### Post by rapattack1 on 2007-07-08
Hi I am having the same problem but my system was not fixed. I have these errors now and there for cannot boot into Ubuntu(6.10). I hope the attached images explain what is happening. After I said ok on each one of these things the last thing said something about correcting GDM. Good thing I had my digital camera to get a good pic. Carla

---

### Post by swarup on 2007-07-08
Could someone please take a look at this link which Zabien1970 has referred me to ([http://gentoo-wiki.com/HARDWARE_Syna...t-Installation](http://gentoo-wiki.com/HARDWARE_Syna...t-Installation)) and let me know if, having Ubuntu 7.04, I need to go through everything described there in order to get my Synaptics touchpad working? I would have thought this Touchpad should have worked out of the box with Ubuntu 7.04. Anyhow, the drag and drop function is not working.

For example, the above mentioned link says one has to do the below (plse see below) in order to move ahead with Synaptics Touchpad installation. Is it really the case that Ubuntu 7.04 would not have CONFIG_INPUT_EVDEV and CONFIG_MOUSE_PS2 ??

Thanks!

---

### Post by zabien1970 on 2007-07-08
When you click on the link it should take you to post install, there were some points there on fine tuning the touchpad further down and using synclient to see current settings, thats the part I was referring to, sorry I haven't been able to help more. 
Here is what I have in xorg

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
	Option		"HorizScrollDelta"	"0"
        Option          "MaxTapTime"            "0"
        Option          "SHMConfig"             "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Hopefully you figure this out

---

### Post by ugm6hr on 2007-07-08
Might be helpful if you paste your whole xorg.conf into here, so we can see where the problem is.

Although, I suspect it may be something to do with this:

```
Section "Module"
Load		"synaptics"
EndSection
```

Just add the *Load "synaptics"* in the Module section, then restart X (Ctrl-Alt-Backspace), and it should work.  I know the Gentoo wiki says it's not necessary - but I think it may be - can't make it any worse, can it?

The other relevant bits of my xorg.conf:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"	"on"
EndSection
```
```
Section "ServerLayout"
Inputdevice	"Synaptics Touchpad"
EndSection
```

---

### Post by swarup on 2007-07-08
As per the request of UGM6HR, I am posting my xorg.conf file below. Perhaps those of you who know more about this sort of thing than me could take a look at it and tell me what is wrong. You will notice below that I have the "SHMConfig" set to "true". I had it set to "on" earlier, but it didn't seem to make any difference. Thanks for all of your help!

And by the way, for the future, how do you all paste things in your postings so they get labeled as "code" with a different color background, and so it maintains all the proper formatting and indenting etc of the original file code?

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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
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
	Identifier	"ATI Technologies Inc Rage Mobility P/M AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility P/M AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
        InputDevice     "Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by swarup on 2007-07-08
Hey, ugm6hr: you are a genius.

"Just add the Load "synaptics" in the Module section, then restart X (Ctrl-Alt-Backspace), and it should work. I know the Gentoo wiki says it's not necessary - but I think it may be - can't make it any worse, can it?"

For two months, I've been struggling on and off to get this Touchpad working properly. And your suggestion here did the trick. It needed the command to "load"!!! Now the Touchpad is working perfectly. I can't believe it. I don't know what software it was working off before, but it was working somehow--it was very jittery, and hard to manage. And the drag and drop didn't work. But now, everything is solved. The cursor is stable and steady, and it drags and drops. Thanks so much!! And thanks so much also to the others who have contributed their suggestions also the past 2-3 days. With your help, I found out about this xorg.conf file and got it loaded with just about all the lines needed to get it working. Once again, thanks so much everyone! This is really great.

---

### Post by ugm6hr on 2007-07-08
Glad you got it working.  Gsynaptic will now work, if you want to edit the touchpad functions.

PS: To post as *Code*, just click on the *#* icon just above the reply box.

---

### Post by zabien1970 on 2007-07-09
That's awesome you got it working!  I kinda figured it was something simple we were all missing, I'm still kinda new to linux so was hoping someone would jump in with that final piece of the puzzle, but that's how we learn, work together and we all become a little more windoze independent, now back to my problems, (learning experience)

---

### Post by swarup on 2007-07-09
> **zabien1970 said:**
> That's awesome you got it working!  I kinda figured it was something simple we were all missing, I'm still kinda new to linux so was hoping someone would jump in with that final piece of the puzzle, but that's how we learn, work together and we all become a little more windoze independent, now back to my problems, (learning experience)

For someone new to linux, you sure had some good insight and were very, very helpful. And you are right, it sure is nice to be free of windows!

---

### Post by chudder on 2007-07-26
> **swarup said:**
> Actually the link you sent me was, I believe, very much needed. Because the Touchpad up till now was not even listed as an Input Device in the /etc/X11/xorg.conf file. And this link gives the instructions of how to add it. The link describes that this will need to be followed in Dapper in order to make the Touchpad work. Although it does not state anything there about 7.04, it seems obvious since my 7.04 did not have it either, that I should have to add it. And I did-- I added the below lines to the xorg.config file as directed:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection

And I also added

        InputDevice     "Synaptics Touchpad"

at the end of the xorg.config file, under the Section "ServerLayout", as directed. And then I saved the changes to the xorg.config file and closed out of the file.

But STILL, my touchpad is not working for drag and drop. Help!! This is the very problem I am trying to solve, and adding all the above doesn't seem to have made a bit of difference.

I've loaded GSynaptics to try and see if that will help, but when I try to start the application, it gives the below error message.

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

But I already did what it is saying to do (set SHMConfig to "true"). 

So how can I get my Synaptics Touchpad to start working right?? And how can I get GSynaptics to run???

I got my touchpad working between the first link and the contents of this post up to the point where I quote.  It was working before, just no settings or scroll could be changed.

---

