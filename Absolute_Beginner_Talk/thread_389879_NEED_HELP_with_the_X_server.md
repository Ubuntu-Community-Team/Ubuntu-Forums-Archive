---
title: "NEED HELP with the X server"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-21
OK! so i tried installing the ATI driver i think it was called using Envy... it asked me to reboot so I did.

Now, i have to work from the live cd cause my computer wont let me pass after this error shows up when my computer starts. I just wrote everything since this is Chinese to me.

FAILED TO START THE X SERVER (YOUR GRAPHICAL INTERFACE). IT IS LIKELY THAT IT IS NOT SET UP CORRECTLY. WOULD YOU LIKE TO VIEW THE X SERVER OUTPUT TO DIAGNOSE THE PROBLEM?

>>YES<<                    NO

X Window system version 7.1.1
Release date: 12 may 2006
X Protocol version 11, revision 0, release 7.1.1
Build operating system: Linux 2.6.15.7 i686
Current operation system: Linux julie 2.6.17-11-generic #2 SMP thu Feb
1 19:52:28 UTC 2007 i686
Build date: 07 july 2006

Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.

Module loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (ww) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) log file:"/var/log/xorg.0.log", time:wed mar 21 10:35:07 2007
(==) using config file:"etc/x11/xorg.conf

Then, it's only a black screen with a cursor that I can write in.... What can I do to get rid of this??

---

### Post by twikletoes on 2007-03-21
You must have installed your video driver incorrectly.

---

### Post by julie_lebou on 2007-03-21
yeah obviously... what i want to know is how to get out of that screen and uninstall whatever i did wrong (Oh and by the way... the setup for the driver did everything by itself... I didn't even do anything

---

### Post by julie_lebou on 2007-03-21
OK! so i tried installing the ATI driver i think it was called using Envy... it asked me to reboot so I did.

Now, i have to work from the live cd cause my computer wont let me pass after this error shows up when my computer starts. I just wrote everything since this is Chinese to me.

FAILED TO START THE X SERVER (YOUR GRAPHICAL INTERFACE). IT IS LIKELY THAT IT IS NOT SET UP CORRECTLY. WOULD YOU LIKE TO VIEW THE X SERVER OUTPUT TO DIAGNOSE THE PROBLEM?

>>YES<< NO

X Window system version 7.1.1
Release date: 12 may 2006
X Protocol version 11, revision 0, release 7.1.1
Build operating system: Linux 2.6.15.7 i686
Current operation system: Linux julie 2.6.17-11-generic #2 SMP thu Feb
1 19:52:28 UTC 2007 i686
Build date: 07 july 2006

Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.

Module loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (ww) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) log file:"/var/log/xorg.0.log", time:wed mar 21 10:35:07 2007
(==) using config file:"etc/x11/xorg.conf

Then, it's only a black screen with a cursor that I can write in.... What can I do to get rid of this??

---

### Post by lamalex on 2007-03-21
ok, so first say yes to veiw that output and post here any lines that start with (EE). when youre at that black screen, hit ctrl+alt+f1 to get to a terminal. imo never use anything but yourself to set up drivers. scripts work for some but totally eff others over. post your errors here and well help

---

### Post by julie_lebou on 2007-03-21
i did say yes.. thats that i posted after the yes or no option....

---

### Post by lamalex on 2007-03-21
oh wow that's it? it doesnt give any errors huh? try this ```
dpkg-reconfigure xserver-xorg
``` as root.

---

### Post by Smuve on 2007-03-21
I know this isn't going to make you feel any better, but envy borked my system as well.  I was trying to get to a point where I could do a:

sudo dpkg-reconfigure xserver-xorg

but I couldn't figure it out and had to do a complete reinstall.

I did not use envy on round 2, but if you do, I think my problem had something to do with matching kernel headers.

If you have to reinstall, I'm sure that live cd can help you backup your /home directory.

Sorry I wasn't much help, but maybe this will help somebody help you.

---

### Post by twikletoes on 2007-03-21
have you tried ctrl + alt + F1?

then you can go to your x-org config file and change you video driver back to what it was and try to reinstall the driver correctly.

---

### Post by julie_lebou on 2007-03-21
OUPS! I had to scrool down for the error! 

It says

(EE) No devices detected.
Fatal server error:
No screens found

And when i tried to be root, i types gksudo nautilus, it said this:

(gksud:4566):Gtk-WARNING**:cannot open display

---

### Post by julie_lebou on 2007-03-21
OUPS! I had to scrool down for the error!

It says

(EE) No devices detected.
Fatal server error:
No screens found

And when i tried to be root, i types gksudo nautilus, it said this:

(gksud:4566):Gtk-WARNING**:cannot open display

---

### Post by julie_lebou on 2007-03-21
:-s Please Help!!! :-(

---

### Post by lamalex on 2007-03-21
nautilus is in display, just do ```
sudo su
``` or run the dpkg command with sudo before it

---

### Post by julie_lebou on 2007-03-21
hey...my god im so lost! Trying to reconfigure my xserver... When it aks me what kind of video card i have... i dont know what to answer cause i think I have a AGP... but its not in the choices.. my mother board is a ASRock K7VM3

And if i try another one... it asks me for info i dont know.. like bus and blahblah... my god i dunno what to do

---

### Post by julie_lebou on 2007-03-21
hey...my god im so lost! Trying to reconfigure my xserver... When it aks me what kind of video card i have... i dont know what to answer cause i think I have a AGP... but its not in the choices.. my mother board is a ASRock K7VM3

And if i try another one... it asks me for info i dont know.. like bus and blahblah... my god i dunno what to do

---

### Post by julie_lebou on 2007-03-21
OK I'm trying to reconfigure my xserver like I'm explaining in my other post  	
NEED HELP with the X server... the thing is:

I don't know what my type of video card is
I don't know anything about what is my bus...
All the questions that the reconfiguration is asking me is pure Chinese to me
Could someone help me... give me instructions?

All i know is that i have a ASRock K7VM3 mother board

So far, I went in dpkg-reconfigure xserver-xorg

After that... HELP!

Thanks a lot!

---

### Post by lamalex on 2007-03-21
give me all of your info, card, mobo, all of that good stuff. i'll see what i can do

---

### Post by dracomordag on 2007-03-21
do you still have windows as a partition? if you do, boot into that, check control panel->system->hardware to see what the name of your Video Card is, and then post it here (or, to make it a little easier on us, google the name of it with some words like "Linux" and "driver" tacked on to see what the name of the driver is).

if you don't have another OS partition, youre gonna have to somehow guess what video card you have. perhaps tell us what make computer you have?


oh, and the selecting of the video driver is all you need to actually manually do in the sudo dpkg-reconfigure xserver-xorg. everything else it gets right, so just hit enter/OK through everything.

---

### Post by julie_lebou on 2007-03-21
the thing is: i dont know where to get these info.. i dont know what info you need, like i said, all i know is the mother i use is ASROCK K7VM3

:S

---

### Post by lamalex on 2007-03-21
how are you getting to the forums? do you have aim/icq/msn on that computer? This might be easier via-realtime. irc works too if you prefer that.

---

### Post by julie_lebou on 2007-03-21
ok talk to me on msn, [email]julie_lebou@hotmail.com[/email]

---

### Post by dracomordag on 2007-03-21
> **julie_lebou said:**
> the thing is: i dont know where to get these info.. i dont know what info you need, like i said, all i know is the mother i use is ASROCK K7VM3

:S
all we need to know is the name of your video card.


like i explained in my other post, you can look it up while booted in your other OS (if you have one), OR you can just tell us where you bought your computer from/who made it.

---

### Post by confused57 on 2007-03-21
> **julie_lebou said:**
> OK I'm trying to reconfigure my xserver like I'm explaining in my other post  	
NEED HELP with the X server... the thing is:

I don't know what my type of video card is
I don't know anything about what is my bus...
All the questions that the reconfiguration is asking me is pure Chinese to me
Could someone help me... give me instructions?

All i know is that i have a ASRock K7VM3 mother board

So far, I went in dpkg-reconfigure xserver-xorg

After that... HELP!

Thanks a lot!

Maybe this will help:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Also, boot the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
lspci
```

this should identify your video card & bus id

---

### Post by tomchuk on 2007-03-21
By chance is there a backup of your xorg.conf in /etc/X11? To find out press Ctrl+Alt+F1 to go to the first virtual console. Log in using the same username and password you use to log in normally. Type: 'ls /etc/X11/xorg*' which should list your current xorg.conf and hopefully a backup will be there as well. It could be called /etc/X11/xorg.conf~ or /etc/X11/xorg.conf.backup or something along those lines. If it is there, you want to use it to overwrite the xorg.conf that isn't working. So if the backup was xorg.conf.backup, you would type: 'sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf'. This command should have copied your working xorg.conf over the crappy envy one. Now issue the command 'sudo /etc/init.d/gdm restart' to attempt to restart the xserver.

Let me know how that goes

---

### Post by lamalex on 2007-03-21
lspci will output your hardware, look for an entry with vga compatible controller and post it here

---

### Post by julie_lebou on 2007-03-21
hey alex... im trying to talk to you on gaim... but for some reason, you have the block sign on ur name, and i cant send any messages... i see what ur saying tho, how can i unblock you^ i send you an email too

---

### Post by Smuve on 2007-03-21
Good call tomchuck, that would be ideal.

If that doesn't work, maybe you could try to get it working with your integrated video first.  I'm not sure what option that is, but you would probably choose the 'vesa' driver in the next screen.

---

### Post by bapoumba on 2007-03-21
@ julie_lebou: merged your other thread in "Server and Security" forum in this one.

---

### Post by julie_lebou on 2007-03-21
x is really slow... especially when i skrool a page up and down

This is my xorg.conf file

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbVariant"	"fr-legacy"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
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
	Device		"Generic Video Card"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by overdrank on 2007-03-21
Hi this would be the cause of you problem


Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection


this is out of you x config and you are using the vesa driver. If you go to the teminal and type the command  lspci  it will tell you the type of video card you have then you can install the correct drivers. Hope this helps  good luck!

---

### Post by JasonWard on 2007-03-21
I've got the exact same problem.

Following the advice gives```
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 11)
```

What now?

---

### Post by lamalex on 2007-03-21
your problem is x is broken? or x is slow?

---

### Post by gingin on 2007-03-21
ATI links:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

It will save you from a lots of time .

---

### Post by JasonWard on 2007-03-21
For me, it is that scrolling in particular is slow, so much so that on occasions I can actually see the screen being repainted.

Jason

---

### Post by JasonWard on 2007-03-21
So I followed this advice

> **gingin said:**
> ATI links:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

It will save you from a lots of time .

And now X server refuses to start saying my video card is not configured properly.

And I've followed the advice in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) which says if X server doesn't start, no problem use Vim.

Really?  So I got the file open in Vim...  now what?

Jason
:confused:

---

### Post by JasonWard on 2007-03-21
Help?:confused:

---

### Post by dimadee on 2007-03-23
I am having exactly the same problem with mybrand new MSI L720 Megabook laptop.  I cannot get past this, so I have not suceeded in actually loading Ubuntu to this machine.

I had high hopes for loading Ubuntu to this machine, but I am starting to have doubts.

I am realy looking forward to some answers here.......it shouldn't be this frustrating should it?

---

