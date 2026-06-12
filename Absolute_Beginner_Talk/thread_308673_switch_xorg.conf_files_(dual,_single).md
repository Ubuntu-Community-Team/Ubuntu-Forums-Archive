---
title: "switch xorg.conf files (dual, single)"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by tocleora on 2006-11-28
I tried to search for this beforehand with no luck.  I have two xorg.conf files, one for a dual monitor set up at work (my laptop with a monitor plugged into it) and a single monitor set up for home (just my laptop).  Right now what I do is I have both backed up as xorg.bak (the single) and xorg.bakdual (the dual) and before I turn off my computer on friday I'll copy xorg.bak to xorg.conf, and before I turn off my computer on Sunday I'll copy xorg.bakdual to xorg.conf.  But I also need to switch the file when I'm playing games, for example enemy territory won't start when I have dual monitor mode.  Is there an easier way for me to switch between these two setups?  Is there maybe a way I can tell it to use these parameters if it detects a second monitor, use these parameters if it doesn't?  Or maybe a way I can detect the existance of the second monitor and run a script that does the copying at that point?  Or even just a menu that says "Ubuntu Dual Monitor", "Ubuntu Single Monitor"?  Thanks for any assistance.

---

### Post by bodhi.zazen on 2006-11-28
> **tocleora said:**
> I tried to search for this beforehand with no luck.  I have two xorg.conf files, 

Yes it is very easy.

What you do is set up two (or more) server sections in xorg.conf with different names.

See this thread: [Dual Monitors](http://ubuntuforums.org/showthread.php?t=240150)

In that thread I lay out an xorg.conf for dual monitors with 3 servers: twinview, dual, and fail. The fail is single monitor.

To select a server, use the -layout <server_name> option with start X.

For example: ```
startx /usr/bin/fluxbox -layout DUAL
```

See this link to my bash script for starting various monitors via the CLI [Dual Monitor Bash Script](http://ubuntuforums.org/showthread.php?t=271045) for further examples.

PM me if you have questions.

---

### Post by tocleora on 2006-11-29
Man I thought I had this figured out... I used the instructions above to set up a script that works for my situation, then I linked to the script in .bashrc... Worked perfectly I got to the login prompt, when I logged in it asked me if I wanted single or dual, I told it which one and it loaded perfectly!

However...

Now every time I open up a terminal window I get that menu as well. :)  Is there a way to only have it when I log in at first and not in the terminal windows?

---

### Post by bodhi.zazen on 2006-11-29
> **tocleora said:**
> Man I thought I had this figured out... I used the instructions above to set up a script that works for my situation, then I linked to the script in .bashrc... Worked perfectly I got to the login prompt, when I logged in it asked me if I wanted single or dual, I told it which one and it loaded perfectly!

However...

Now every time I open up a terminal window I get that menu as well. :)  Is there a way to only have it when I log in at first and not in the terminal windows?

Hey, glad it worked for you. When you get the kinks out would you be so kind as to post your solution ?

Yes, put the script somewhere else. ~/.bashrc is run every time you open a terminal.

Try .bash_profile (will be used only at login) or you could put your script in /etc/rc.local.

Or put your script in ~/.bashrc as a function...

General syntax is> 
() dual # this is the name of the function
{ 
insert script
}

Not you would run the script by typing **dual** in the terminal....

Or put your script in /usr/bin and call it what you will....


8)

---

### Post by onthink on 2006-11-29
I have several to change with you guys here,thanks[.]("http://www.china-cart.com/china.asp?aid=129&nid=1591")

---

### Post by tocleora on 2006-11-29
Ok, finally got it working, this is what I did.

First, I added my dual monitor settings to xorg.conf:

```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
	Option "MonitorLayout" "CRT,LFP"
	Option "DevicePresence" "true"
EndSection

Section "Device"
	Identifier	"1 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
	Option "DevicePresence" "true"
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DUALMONITORS"
	Screen		0 "Main Screen" 0 0
	Screen		1 "Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option "Xinerama" "true"
EndSection
```

Then I added the single monitor settings to xorg.conf:

```
Section "Device"
	Identifier	"0 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"0 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"SINGLEMONITOR"
	Screen          "Default Screen"
	InputDevice     "Generic Keyboard"
	InputDevice     "Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

For some reason, something in the "Intel Corporation..." Device caused errors with the Single Monitor so I had to create a separate Device for just single monitor.  I used the same Monitor entry though.  If there's a way to fix this I'd love to know.

Second, I turned off GDM.  For some reason System > Administration > Services turned it off temporarily but not permanently.  The way I got it to turn off permanently was through webmin.  I'm sure there's an easier way  for those who don't have webmin installed but me being very familiar with webmin I was able to do it that way quickly.

Third, I created a script called xmenu and stuck it in my home directory:

```
#!/bin/sh

echo -n "How many monitors? "
read monitorcount

case $monitorcount in
	1)
		exec /usr/bin/startx -- -layout SINGLEMONITOR
		exit 
		;;
	2)
		exec /usr/bin/startx -- -layout DUALMONITORS
		exit
		;;
	*)
		exit
		;;
esac
```

I made it executable:

```
chmod +x xmenu
```

Then added it to the bottom of my .bash_profile:

```
/home/tocleora/xmenu
```

I realize I could have just added it directly to the .bash_profile script but I felt this quicker, one line remark if it failed.  That did the trick, thanks for your help! :)

---

### Post by elektronaut on 2007-01-10
Thank you both a lot for your input, bodhi.zazen and tocleora! I got one step further to solving my monitor trouble now. Using tocleora's xorg.conf and the script, I can now use my laptop at home and on the road with a properly configured XServer all the time. That's cool. But there is one major annoyance left. At home I always use a second monitor. But during the boot process, the monitor cable has to be unplugged, otherwise the monitors become "exchanged". That means, the external monitor becomes the first monitor, and the laptop monitor the second. This also means that the external one is running with a wrong refresh rate and that I can't move the mouse between them both, the pointer has to leave the external monitor (which is to the left side of the laptop) at the left side and then it can enter the laptop monitor at the right side... Not really a good working environment :-? 
So, is there a way to end this stupid plugging/unplugging procedure?

---

### Post by bodhi.zazen on 2007-01-10
8)

Can you post you xorg.conf so that we might take a peek ?

---

### Post by elektronaut on 2007-01-10
Sure, although it's nearly the same as tocleora's.
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
        FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath "/usr/share/fonts/X11/Type1"
        FontPath "/usr/share/fonts/X11/100dpi"
        FontPath "/usr/share/fonts/X11/75dpi"
	FontPath "/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
	FontPath "/usr/local/share/fonts"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de,fr"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
	Option "MonitorLayout" "CRT,LFP"
	Option "DevicePresence" "true"
EndSection

Section "Device"
	Identifier	"1 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
	Option "DevicePresence" "true"
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
	HorizSync	28-81
	VertRefresh	48-75
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DUALMONITORS"
	Screen		0 "Main Screen" 0 0
	Screen		1 "Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "true"
EndSection

Section "Device"
	Identifier	"0 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"0 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"SINGLEMONITOR"
	Screen          "Default Screen"
	InputDevice     "Generic Keyboard"
	InputDevice     "Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite"	"true"
#EndSection

```
I managed to get i810switch working. The original version uses another pci id than the one which is used by the intel 945gm in my laptop, so I first installed from the repository, then I downloaded the sources and changed this line in i810switch.c:
```
#define I915STR			"8086:2592"
*to*
#define I915STR			"8086:27a2"
```
The pci id can be found by using 'lspci'. And then as usual 'make' and 'make install' (no checkinstall here as I'm tricking the update-notifier). I can switch off the external monitor now, not the laptop screen, but that's not necessary anyway. I'm wondering if it is possible to have this line ```
i810switch crt off lcd on
``` executed as the first command while booting, and then call ```
i810switch crt on lcd on
``` in the xmenu script if I choose 2 monitor setup?
The more I think about it, the less I'm positive there might be a possibility to solve this. When I boot with the external monitor attached, already the BIOS shows up on the external monitor, which is not as it should be.

[EDIT: updated procedure for installing i810switch]

---

### Post by tocleora on 2007-01-11
So if I understand correctly (and to clarify for anyone that might actually be able to help), The device at "Screen 0" is showing up on your external monitor and the device at "Screen 1" is showing up on your laptop screen?   This is more likely too simple (as I too made my version from copied versions I'm not sure) but have you tried just making screen 1 your primary?  I would think something like this:

```

Section "ServerLayout"
	Identifier	"DUALMONITORS"
	Screen		1 "Second Screen" 0 0
	Screen		0 "Main Screen" LeftOf "Second Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "true"
EndSection

```

Or if you'd prefer to relabel everything your call, but in my honestly minimal experience and knowledge of how this works, that seems like that might, worth a try at least until someone who knows more of what they are talking about chimes in. :)

---

### Post by bodhi.zazen on 2007-01-11
First, of course make a back up of your xorg.conf

Not only is this good practice, but I might break your xorg.conf :)

Second, not to ask the obvious, but on some laptops when you have an external screen connected you select a screen with a keyboard combination, Alt-F5

Can you change screens this way ?

Last, try changing:

> Section "ServerLayout"
	Identifier	"SINGLEMONITOR"
	Screen          "Default Screen"
	InputDevice     "Generic Keyboard"
	InputDevice     "Configured Mouse"
EndSection

To

> Section "ServerLayout"
	Identifier	"SINGLEMONITOR"
	Screen 0       "Main Screen"
	InputDevice     "Generic Keyboard"
	InputDevice     "Configured Mouse"
EndSection

HTH

---

### Post by tocleora on 2007-01-11
Well his single monitor is working correctly, right?  It's when he uses the dual monitors that they are switched.  Does that help/matter?

---

### Post by bodhi.zazen on 2007-01-11
> **tocleora said:**
> Well his single monitor is working correctly, right?  It's when he uses the dual monitors that they are switched.  Does that help/matter?

Oh, sorry I missed that :redface:

For your second monitor add in the HorizSync and VertRefresh rates for the monitor to the monitor section (right now they are blank).

> Section "Monitor"
	Identifier	"Second Monitor"
	HorizSync	**???**
	VertRefresh	**???**
	Option		"DPMS"
EndSection

And change:> 	Screen		1 "Second Screen" LeftOf "Main Screen"

To

> 	Screen		1 "Second Screen" **RightOf** "Main Screen"

---

### Post by elektronaut on 2007-01-11
> **bodhi.zazen said:**
> 
For your second monitor add in the HorizSync and VertRefresh rates for the monitor to the monitor section (right now they are blank).
Unfortunately I don't know them, there is nothing neither in the documentation nor on the net.
> 
And change:
```
Screen 1 "Second Screen" LeftOf "Main Screen"
```
To
```
Screen 1 "Second Screen" RightOf "Main Screen"
```

I guess I wasn't explaining clearly. If I don't plug in the external monitor during boot, but just afterwards, everything works fine. So there is no need to change the way the two monitors are arranged. The problem only comes up if I have the external monitor plugged in during the boot process. The more I think about it, the less I think it has anything to do with the XServer, because already the boot menu and the console are displayed on the "wrong" screen, and these two are displayed before the XServer is started. I should have started a new thread probably, as this hasn't got much to do with the original topic. I'm just wondering why it works for tocleora, but not for me. Apparently laptops are built differently, even if they have an Intel graphics device in common?

---

### Post by tocleora on 2007-01-11
Well, that's why I suggested what I did, I'm wondering if when you have a monitor plugged in, your laptop identifies it as 0 and your laptop screen as 1 where when it's not plugged in it only sees one and therefore identifies your laptop screen as 0.  In that case the fix I suggested should work for you.  

```

Section "ServerLayout"
	Identifier	"DUALMONITORS"
	Screen		1 "Second Screen" 0 0
	Screen		0 "Main Screen" LeftOf "Second Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "true"
EndSection

```

Making what it sees as your Second Screen (which is actually your laptop screen) the primary screen and then making what it sees as your Main Screen (which is actually your external monitor) secondary and what's "LeftOf" your laptop screen.  Make sense?  No guarantees it will work, but again, worth a try. ;)

Why it works for me is more than likely just brand, my laptop is a Fujitsu. :)

---

### Post by tocleora on 2007-01-11
Also, if it's happening before you ever boot into X Windows, you should try what someone else suggested before you ever go into X Windows, the button on your keyboard that allows you to switch monitors.  then when you go into X Windows it might be right.  Sorry I don't know the official terms for these things hopefully you understand what I'm talking about. :)

---

### Post by tocleora on 2007-01-11
Oh one more thing - I wasn't saying fujitsu is better than yours by any means, just saying that configuration may just be what works on my brand.  wanted to clarify. ;)

---

### Post by elektronaut on 2007-01-11
Changing the screen numbering in the ServerLayout section resulted in a Xserver crash. I really don't think xorg.conf takes part in this story at all, I fear it might be hardware related. Though I will try to put the i810switch call in a low runlevel and see if that helps. Thanks for your input again, tocleora and bodhi.zazen!

---

### Post by elektronaut on 2007-01-11
> **tocleora said:**
> Also, if it's happening before you ever boot into X Windows, you should try what someone else suggested before you ever go into X Windows, the button on your keyboard that allows you to switch monitors.  then when you go into X Windows it might be right.  Sorry I don't know the official terms for these things hopefully you understand what I'm talking about. :)
Unfortunately that button is not working :-|

---

### Post by WangWeiLin on 2007-01-14
Hi guys I saw your posts and just wanted to let you know what I did.

First of all I might be able tp help one of you the guy who was talking about how he had to unplugg is monitor all the time. I sorry if somebody postet an answer to this point but I got sick of reading the whole thread.

You should put
 ```
Option "UseDisplayDevice" "CRT"        or          Option "UseDisplayDevice" "DFP"
```
in your Device section. This sets what Display the Device will be using.

The 2nd part: You guys where talking about using a small script to change between single and dual monitor use and as far as I could see you did that when you where already logged in (I might be wrong with that) so you restart your x everytime you change between 1 monitor and 2 monitor use. I have to do the same thing and if you know a way to not having to do that, tell me. But my way of doing it is a litte different. I added a little startup script 

```
#!/bin/sh
case $XORG in
    single)
        # if PARAM== single
        cp /etc/X11/backup.single.xorg.conf /etc/X11/xorg.conf
        echo "Single Screen Setup for KDE : Enabled"
    ;;
    dual)
        # if PARAM== dual
        cp /etc/X11/backup.dual.xorg.conf /etc/X11/xorg.conf
        echo "Dual Screen Setup for KDE : Enabled"
    ;;
    *)
        #default conf here
    ;;
esac
exit 1

```

and added the variable "XORG=single" or "XORG=dual" to the grub menu.lst just to the end of kernel line.

Last thing to do was to make symlink in /etc/rc#.d to the script we created above (/etc/init.d/xorg). The # you have to exchange to the number you think is the best runlevel for your script to fireup. 
When you create the symlink just look that you create one that does not exist already and it looks something like this

```
lrwxrwxrwx 1 root root  19 2007-01-08 15:17 S01xorg -> ../init.d/xorg
```

S=start <- you have to use S

Some of you might ask ok whats the point of all this. Simply that: 
You can now create different monitor layouts just by creating different boot options in the /boot/grub/menu.lst this way you don't have to restart your x, you just select it when you start your computer.

For example my menu.lst looks like this:

```

title		Single Monitor - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro quiet splash XORG=single
initrd		/initrd.img-2.6.17-10-386
savedefault
boot

title		Dual Monitor - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=dual
initrd		/initrd.img-2.6.17-10-386
boot

title		Home - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=dual NET=home
initrd		/initrd.img-2.6.17-10-386
boot

title		Uni - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=single NET=uni
initrd		/initrd.img-2.6.17-10-386
boot

title		Work - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=dual NET=work
initrd		/initrd.img-2.6.17-10-386
boot


title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
boot
```

I did the same thing for my network this way my connection already exists when kde starts and I don't get any errors about not having an internet connection.

Unix 4 Ever
wangweilin

p.s. I forgot to tell you guys, as you might see in the script I too use different xorg files and with the script I just copy them to the /etc/X11/xorg.conf

---

### Post by tocleora on 2007-01-14
The problem with making the switch in Grub is that if you want to switch between dual and single, like if you are dual and you decide you want to kick up a quick multiplayer game of OpenArena with your coworkers, you'd have to completely reboot.  With my (our?) way, we just exit out of X and run the script selecting single mode.  Unless there's something I'm missing?

---

### Post by elektronaut on 2007-01-15
Putting the line ```
"UseDisplayDevice" "LFP"
``` didn't change anything, the external monitor was still used as the primary screen if it was plugged in during boot. So I decided to let the graphics card have it's way and changed xorg.conf accordingly, inspirated by bodhi.zazens and tocleora's suggestions. Now the Gnome panels are on the external monitor, and I don't have to unplug it anymore! This is the display part of my xorg.conf:
```
######################################################################
########### DUALSCREEN SETUP

Section "Device"
	Identifier	"GMA950"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
	Option "MonitorLayout" "CRT,LFP"
	Option "DevicePresence" "true"
#	Option "UseDisplayDevice" "LFP"
EndSection

Section "Device"
	Identifier	"1 GMA950"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
	Option "DevicePresence" "true"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	HorizSync	28-81
	VertRefresh	48-75
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"GMA950"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 GMA950"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DUALMONITORS"
	Screen		0 "Main Screen" 0 0
	Screen		1 "Second Screen" RightOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "true"
EndSection

######################################################################
########### SINGLESCREEN SETUP

Section "Device"
	Identifier	"0 GMA950"
	Driver		"i810"
	BusID		"PCI:0:2:0"
#	Option "UseDisplayDevice" "LFP"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"0 GMA950"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"SINGLEMONITOR"
	Screen          "Default Screen"
	InputDevice     "Generic Keyboard"
	InputDevice     "Configured Mouse"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite"	"true"
#EndSection

```

---

### Post by morningcoffeee on 2007-02-08
I'm impressed by the interface of the forum and i just want to creat a poll, asking you guys for your experiences. 
Please check out the poll and give me your comments. 
 
 
 
 
_______________________________________ 
180 000 FREE songs - [http://music.genterist.net](http://music.genterist.net)

---

### Post by a5benwillis on 2007-02-08
Wang,

Hopefully you're still checking this thread. I can't seem to get your example to work. When I add the XORG to the menu.lst file i boot up to a root console instead of gnome.

Can you tell me what Im doing wrong by following your example?

Thanks,

Ben


> **WangWeiLin said:**
> Hi guys I saw your posts and just wanted to let you know what I did.

First of all I might be able tp help one of you the guy who was talking about how he had to unplugg is monitor all the time. I sorry if somebody postet an answer to this point but I got sick of reading the whole thread.

You should put
 ```
Option "UseDisplayDevice" "CRT"        or          Option "UseDisplayDevice" "DFP"
```
in your Device section. This sets what Display the Device will be using.

The 2nd part: You guys where talking about using a small script to change between single and dual monitor use and as far as I could see you did that when you where already logged in (I might be wrong with that) so you restart your x everytime you change between 1 monitor and 2 monitor use. I have to do the same thing and if you know a way to not having to do that, tell me. But my way of doing it is a litte different. I added a little startup script 

```
#!/bin/sh
case $XORG in
    single)
        # if PARAM== single
        cp /etc/X11/backup.single.xorg.conf /etc/X11/xorg.conf
        echo "Single Screen Setup for KDE : Enabled"
    ;;
    dual)
        # if PARAM== dual
        cp /etc/X11/backup.dual.xorg.conf /etc/X11/xorg.conf
        echo "Dual Screen Setup for KDE : Enabled"
    ;;
    *)
        #default conf here
    ;;
esac
exit 1

```

and added the variable "XORG=single" or "XORG=dual" to the grub menu.lst just to the end of kernel line.

Last thing to do was to make symlink in /etc/rc#.d to the script we created above (/etc/init.d/xorg). The # you have to exchange to the number you think is the best runlevel for your script to fireup. 
When you create the symlink just look that you create one that does not exist already and it looks something like this

```
lrwxrwxrwx 1 root root  19 2007-01-08 15:17 S01xorg -> ../init.d/xorg
```

S=start <- you have to use S

Some of you might ask ok whats the point of all this. Simply that: 
You can now create different monitor layouts just by creating different boot options in the /boot/grub/menu.lst this way you don't have to restart your x, you just select it when you start your computer.

For example my menu.lst looks like this:

```

title		Single Monitor - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro quiet splash XORG=single
initrd		/initrd.img-2.6.17-10-386
savedefault
boot

title		Dual Monitor - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=dual
initrd		/initrd.img-2.6.17-10-386
boot

title		Home - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=dual NET=home
initrd		/initrd.img-2.6.17-10-386
boot

title		Uni - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=single NET=uni
initrd		/initrd.img-2.6.17-10-386
boot

title		Work - Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-386  ro single XORG=dual NET=work
initrd		/initrd.img-2.6.17-10-386
boot


title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
boot
```

I did the same thing for my network this way my connection already exists when kde starts and I don't get any errors about not having an internet connection.

Unix 4 Ever
wangweilin

p.s. I forgot to tell you guys, as you might see in the script I too use different xorg files and with the script I just copy them to the /etc/X11/xorg.conf

---

### Post by nalberda on 2007-03-14
I though of a way that works better for me (not trying to hijack the thread, just giving ideas to searchers out there because I was stumped for a while till I thought of this).  I don't do dual display as my vid card can't run beryl on dual display (i945).  Instead I do external at the office, and internal every where else. I figure out where I am via a wireless scan, although i could find it by determining my ip address or subnet if it was wired etc.  Any how, here is my init script.  I also setup my wireless via this script as I already know where I am, so may as well connect.  I static my IP for my home lan, dhcp at work, and I fallback to internal and wireless network if I don't see either (perhaps on the road).  I call this before kdm with S07checkwifi in rc2.d (I use kde, not gdm and gnome).

```


#! /bin/sh
wlan_name=wlan1
wlan_2_name=wlan2
enc_key=I_dont_think_so
enc_2_key=I_dont_think_so
logfile=/var/log/wifistatus.log
PATH=/sbin:/bin
. /lib/init/vars.sh

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start() {
		log_action_begin_msg "Scanning for Wireless networks"
		iwlist eth1 scan |grep $wlan_name > /dev/null
		if [ $? -eq 0 ]; then
			{
			cp /etc/X11/xorg.conf.internal /etc/X11/xorg.conf
			iwconfig eth1 essid $wlan_name
			iwconfig eth1 enc s:$enc_key
			ifconfig eth1 1.2.3.4 netmask 255.255.255.0
			route add default gw 1.2.3.1
			echo "nameserver 1.2.3.1" > /etc/resolv.conf
			echo int > $logfile
			iwconfig >> $logfile
			ifconfig eth1 >> $logfile
			log_success_msg "Home WIFI Detected, Copied Internal Xorg.conf"
			}
		else
			{
			iwlist eth1 scan |grep $wlan_2_name > /dev/null
			if [ $? -eq 0 ]; then
				{
				cp /etc/X11/xorg.conf.ext /etc/X11/xorg.conf
				iwconfig eth1 essid $wlan_2_name
				iwconfig eth1 enc s:$enc_2_key
				dhclient eth1 
				echo int > $logfile
				iwconfig >> $logfile
				ifconfig eth1 >> $logfile
				log_success_msg "Work WIFI Detected, Copied Internal Xorg.conf"
				}
			else
				{
				cp /etc/X11/xorg.conf.internal /etc/X11/xorg.conf
				log_failure_msg "No recognised WIFI Detected, Copied Internal Xorg.conf"
				echo ext > $logfile
				}
			fi
			}
		fi
}

case "$1" in
  start|"")
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: checkwifi.sh [start|stop]" >&2
	exit 3
	;;
esac

:



```

---

### Post by tocleora on 2007-03-15
That's not a bad idea at all... I never thought of checking my ip, because I use 192.168.* at home and 10.10.* at work... I'm having a weird problem since upgrading to Edgy though where sometimes my external monitor comes in at 800 x 600 or 640 x 480 (I know it's just smaller, not sure the exact size), if I try more than 3 times, X just craps out and I have to reboot, so sometimes it will take up more than 3 (but never more then 6) to finally get it in the right screen resolution.  So I've gotten lately to where I don't always run that second monitor because I just don't want to mess with it.  But if I ever figure that problem out, I'm doing this ip thing! :)

---

### Post by zibletop on 2007-08-10
Dear,

Thanks for your interresting method. However I have some problem to transfer the parameter XORG from Grub to init: when the script to select the xorg.conf file is launched, the variable $XORG is empty.

yours

PS: I'm running Ubuntu edgy and the startup is managed by upstart and not init.

---

