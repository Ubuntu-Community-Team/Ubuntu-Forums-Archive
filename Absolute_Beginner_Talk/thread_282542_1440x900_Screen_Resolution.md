---
title: "1440x900 Screen Resolution"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-22
I was wondering how I can enable the 1440x900 screen resolution for my widescreen resolution. Currently, my screen is just streched. But I want the true resolution that my laptop was designed for. I have the Dell Inspiron E1405. What should I do? Thanks!

---

### Post by SendDerek on 2006-10-22
There was another fellow having about the same issue as you are now.  I'm going to link to his thread and maybe that will help you to figure out how to get the resolution you want.

[http://ubuntuforums.org/showthread.php?t=280742](http://ubuntuforums.org/showthread.php?t=280742)

---

### Post by amitroy5 on 2006-10-22
When I was first installing Ubuntu, when I ran it form CD, I had to use "Safe Mode" because when I ran through "regular," the screen would not come up and I would get an error. So I am not sure what to do that will be safe.

---

### Post by amitroy5 on 2006-10-23
bump - still need an answer. Thanks!

---

### Post by Marsolin on 2006-10-23
I'm running that resolution in Kubuntu. To enable it I had to go into System Settings and adjust the monitor to that resolution. Gnome should have something similar, but I don't know the exact steps.

---

### Post by amitroy5 on 2006-10-23
I have Gnome on a Dell Inspiron E1405. When I go to change the screen resolution, I get the following resolution options:

640x480
800x600
1024x768

I have it set to 1024x768, which makes the image stretched.
I have no option for 1440x900. Any ideas on how I can fix this? Thanks!

I get this stretched look right now. :(

---

### Post by Henry Rayker on 2006-10-23
You need to first check to see what chipset your display is running.

Mine uses an SiS chipset.

Next, open a terminal and run this:
sudo dpkg-reconfigure xserver-xorg

When you get to a question about your graphics chipset, choose whatever your system has (I chose SiS) I believe the default is Vesa.

When you get to the resolution selection, make sure you enable the one you want.

That should work. If you have trouble understanding this, let me know. I'm not at my Ubuntu machine and can't give a perfect explaination. (RedHat at work =\  )

---

### Post by Marsolin on 2006-10-23
> **amitroy5 said:**
> I have Gnome on a Dell Inspiron E1405. When I go to change the screen resolution

It's not screen resolution that you need to change. That's the second step. The first is changing what your monitor is being listed as. Check for a monitor tab or description somewhere near where you are changing resolution.

Hopefully someone will post with the specific Gnome instructions for this. The problem you are experiencing is one of my biggest frustrations with Ubuntu (and other distros) right now. It's a capability that exists, but no one is combining the settings into a single tool.

---

### Post by amitroy5 on 2006-10-23
I cannot find a "Monitor Tab" near where I change the screen resolution. Also, how do I check if I am using a SiS chipset.

---

### Post by Henry Rayker on 2006-10-23
I'll post better instructions when I get home, but you can get to a hardware list, of sorts from the main menu...In the main menu (the one on the right of Places...System, I believe it is called) has 2 sections. In the Administration menu, there is a hardware list or something similar. You can check your display adapter in there.

Then you need to run the line I mentioned above to get it changed.

---

### Post by TrinitronX on 2006-10-23
I've got this running at home on my LCD widescreen.  I had to edit my xorg.conf file and add an entry for 1440x900 in my screen's section.

Here's the appropriate section where you should add the resolution:
```
Section "Screen"
	Identifier "LCD Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "LCD Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Simply open up your /etc/X11/xorg.conf file, and add ```
"1440x900"
``` as the first resolution under each subsection for each different display depth under "Modes".

Then just restart your Xserver or reboot, and it should hopefully work.

---

### Post by Henry Rayker on 2006-10-23
TrinitronX, that will only work if he/she has used the right display adapter.

---

### Post by TrinitronX on 2006-10-23
Yes, this is true.  My monitor was not one which I could choose from gnome or kde from what I remember, so I had to customize my xorg.conf to fix it.

Assuming your "Monitor" section has the right settings for your monitor (hsync and vrefresh, etc..), and your video card device is running correctly and is pointed to by the "Device" part in the above xorg.conf snippet, then this should be the only change needed.

However, if you are having problems with either the monitor's settings not being correct in the "Monitor" section, or your video card device is not configured correctly in the "Device" section, then that could be causing problems as well.  If that's the case, be sure to check that all your settings are correct.

---

### Post by amitroy5 on 2006-10-23
Thanks for all your help. I'll wait until Henry Rayker makes a guide. Thanks so much!

---

### Post by Henry Rayker on 2006-10-23
In the main menu (similar to the Windows start menu) click the System menu, then go to administration and click "Device Manager".

Scour through there until you find something that says display adapter or something similar (it may very well be different on your system, so I don't know the specifics).

When you find it, take note of the information. You might want to write it down or something. Something in there will be the brandname (if it is an SiS chipset, you'll see SiS. If it's a Vesa chipset, you'll see that.)

Let me know if you can find that information.

---

### Post by amitroy5 on 2006-10-23
Does "Mobile Integrated Graphics Controller" count as a display? I get the following:

Vendor: Intel Coorperation
Device: Mobile Integrated Graphics Controller
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

---

### Post by Henry Rayker on 2006-10-23
That should be it. I'd give the reconfigure a shot and select intel as the display driver to load.

---

### Post by amitroy5 on 2006-10-23
For xserver-org, I cannot find "intel," but I can find others such as SiS. But Intel is not there. :(

---

### Post by Henry Rayker on 2006-10-23
I think I remember intel chipsets using another program, but I don't have any experience with it.

I believe it is called 855resolution, though.

[This thread]("http://ubuntuforums.org/showthread.php?t=27029&highlight=i810") might help you out. I'm not certain.

I'm sorry i couldn't be of more help.](*,)

---

### Post by amitroy5 on 2006-10-23
Is this something that might be fixed in the next version of Ubuntu? Or at least easier to configure? This way, I will not have to fiddle around a few days before the new Ubuntu.

---

### Post by amitroy5 on 2006-10-23
I just configured xserver. How do I run xserver to use the settings I entered?

---

### Post by Marsolin on 2006-10-23
You just need to reboot.

---

### Post by amitroy5 on 2006-10-23
I did a restart, but I do not see teh 1440x900 resolution. How do I get that to come up?

---

### Post by DarkWulf on 2006-11-03
Depending on what model intel GMA you have you may also want to try 915resolution

---

### Post by amitroy5 on 2006-11-07
Do you have a guide to the 915resolution?

Here is my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel 915GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        65536
Option "ForceBIOS" "1920x1440=1440x900"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       28-72
        VertRefresh     59.0 - 75.0
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 915GM"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I still cannot see the 1440x900 when I try to change screen resolutions. It worked for a while but all of a sudden, it doesn't wokr anymore. I don't want to switch back to Windows over this issue. :(

---

### Post by amitroy5 on 2006-11-07
I am getting very close to a solution! For some reason, whenever I restart the computer, the resolution goes back to the old one. I have to type "sudo 915resolution 5c 1440 900 32" and then I press "control + alt + back" to reset gnome.  Finally, the new resolution that I want is here.

However, if I restart my computer. It goes back to the old one. How can I fix that problem?

---

### Post by gn2 on 2006-11-07
> **amitroy5 said:**
> I am getting very close to a solution! For some reason, whenever I restart the computer, the resolution goes back to the old one. I have to type "sudo 5c 1440 900 32" and then I press "control + alt + back" to reset gnome.  Finally, the new resolution that I want is here.

However, if I restart my computer. It goes back to the old one. How can I fix that problem?

I believe there is a package in Synaptic specifically for widescreen Intel display adapters, 915 resolution.

---

### Post by amitroy5 on 2006-11-07
gn2, that is what I am using right now. I'm using 915resolution right now. (that is how I ran that command).

How do I have these settings come at the time of booting?

> 
I am getting very close to a solution! For some reason, whenever I restart the computer, the resolution goes back to the old one. I have to type "sudo 915resolution 5c 1440 900 32" and then I press "control + alt + back" to reset gnome. Finally, the new resolution that I want is here.

However, if I restart my computer. It goes back to the old one. How can I fix that problem?

---

### Post by gn2 on 2006-11-07
> **amitroy5 said:**
> gn2, that is what I am using right now. I'm using 915resolution right now. (that is how I ran that command).

How do I have these settings come at the time of booting?

You could manually edit xorg.conf so that the only resolution available is the one you want.

---

### Post by JayTee on 2006-11-07
> **amitroy5 said:**
> gn2, that is what I am using right now. I'm using 915resolution right now. (that is how I ran that command).

How do I have these settings come at the time of booting?

Try this, it's from another thread on using the 915resolution tool.

> Your new resolution should work when you reboot as well. If your resolution reverts to an undesired, lower resolution on reboot:

Code:

sudo gedit /etc/rc.local

Add the desired 915resolution {sudo 915resolution 5c 1280 800 24} above the "exit 0" line.

Save /etc/rc.local and exit gedit.


---

