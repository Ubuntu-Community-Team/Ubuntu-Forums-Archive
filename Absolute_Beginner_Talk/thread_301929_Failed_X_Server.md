---
title: "Failed X Server"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by xtothez on 2006-11-17
I just got home, for those responding to me earlier, and am trying the Dapper Ubuntu install CD. It says: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <YES> <NO>". Umm... what does this mean? Is it due to a PCI-E video card?

---

### Post by taurus on 2006-11-17
Yeah, it's probably your graphic card and you didn't configure it right the first time.  Reboot and at the GRUB menu, pick the recovery mode.  Wait for it to finish booting and see if you can configure your X again with

```
dpkg-reconfigure xserver-xorg
```
Save it and type "startx" (without the " ") to see if Gnome comes up or not.  If it does, log out and reboot...

---

### Post by xtothez on 2006-11-17
I'm not entirely sure what GRUB or Gnome is, but the menu comes backs for install, I tried F6 and typed in the code you typed. It brought up a screen with [ 68.112001] through [ 68.171697] and then blinks and underscore indefinitely...is there something I skipped?

---

### Post by taurus on 2006-11-17
Gnome is a window manager while GRUB handles booting Ubuntu and other OSes on your machine.  So, when you first turn on your computer, you see a menu with a few entries on it:  kernel, recovery mode, memtest, Windows (if you have Windows at all).  That's what GRUB menu is.  Use the arrow key to move down to recovery mode and hit enter to boot from it.  Wait for the whole thing to finish booting and at the prompt, type that command in to reconfigure your X again.  If you are not sure about a question, just use the default value and you should be good to at least get your X up and running again.

---

### Post by xtothez on 2006-11-17
I must not be doing this right...when I start my computer it goes straight to Windows XP. If I hit F8 to bring up the command menu, the only options are safe mode (plain, w/ command, w/ networking) and some other logging menu functions. If I boot into Ubuntu's install CD, the boot from first hard disk option says "Error loading OS", Install Ubuntu selection loads things at the bottom (drivers, file system, live CD user, fstab, swap, hostname, etc.) and even "ok"s the configuring X one...but then goes to a black screen w/ an underscore flashing. It brings up a black screen with some white lettering, but then quickly brings the blue screen with X server error...is there another way to install?

---

### Post by xtothez on 2006-11-17
If I hit "no" it brings that black screen back up, and has ubuntu@ubuntu:~$ <here is where I can enter things>

If I type that code it, it provides:
/usr/sbin/dpkg-reconfigure must be run as root

Any ideas?

---

### Post by taurus on 2006-11-17
My bad.  I somehow thought you already have Ubuntu running on your machine!!!  You ARE still trying to get the LiveCD to boot so you can install it on your computer.  

Try using the alternate CD instead...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by xtothez on 2006-11-17
hopefully you are still there Taurus. No dice, it didn't work either...this time it says the same thing but the Ubuntu install splash screen (with the menu for install, safe vga install, and such) is regular but the progress bar afterwards is black and white...any ideas?

---

### Post by xtothez on 2006-11-18
I don't think there is another version to run...anyone have an idea of what to do? or if there is a way around it?

---

### Post by taurus on 2006-11-18
So the alternate CD is a no go either!  What is the spec of your machine then?

---

### Post by xtothez on 2006-11-18
...Mobo: DFI Lan-Party nForce chipset
...CPU: AMD Athlon64 (either Newcastle or Clawhammer) 3000+
...RAM: 2GB (2x1GB) PC3200 DDR (Dual-Channel)
...GPU: ATI Radeon X850XTPE PCI-E (256MB GDDR-3)
...RAID: Promise TX2 Raid Card w/ 2x IDE WD ATA100 Drives
...The HDDs are setup in a RAID 2+0 Stripe with 2 partitions, each being 80GB totaling the 160GB formed by the two 80GB drives. XP is installed on the first partition while music/videos and such is on the second partition. I also have a Seagate SATA300 drive for backing up the music/videos, but would prefer installing Ubuntu on the 2nd partition of the raid drives. I have stuff plugged into the USB and such, but thats all thats in the internal quadrants, mostly to keep it cooler. (runs at 26 celsius w/ its coolant setup)

---

### Post by junglepeanut on 2006-11-18
Have you tried running it root as it asked you too?
> 
If I type that code it, it provides:
/usr/sbin/dpkg-reconfigure must be run as root

sudo dpkg-reconfigure xserver-xorg

---

### Post by xtothez on 2006-11-18
also, would it be ok to install it to the 2nd partition of the raid? and able to load both linux and windows when I start up?... I've had ME and XP (way back when) on two partitions before and it prompted me for which I wanted to load, would it be the case if so?

---

### Post by xtothez on 2006-11-18
that did work Junglepeanut, however when I finished the lengthy exam, or so it seemed, I restarted and it came back...any suggestions?

---

### Post by xtothez on 2006-11-18
If I don't restart after the X Server configurating it leaves a command style prompt..what do I enter to continue into the LiveCD screen to install?

---

### Post by junglepeanut on 2006-11-18
When you took the "lengthy exam" did you choose vesa? Please try this instead of ati or fglrx to start. Then once you do this since you are doing this with a live cd I think yo9u must now type startx in the terminal to see if it works

therefore just to make sure do 


```
sudo dpkg-reconfigure xserver-xorg
``` 

once more to be sure we try vesa first (as it is most likely to work).
then 



```
startx
```



If this does not workplease post what it says it should not be to difficult to get it to start if we do this correctly. Then you can see what it is like. Finally, when you install it to your hardrive you will not have to do this as much as then you can look into the forums on how to install the ati driver and it will be much nicer. Otherwise, there are other routes like the ati open source driver the open source radeon driver, and the opensource fglrx driver. I personally like ati's propiertary driver, but you have to go through this reconfiguring everytime you upgrade the kernel.

Good luck
Jp

---

### Post by xtothez on 2006-11-21
Ok, I tried the code you supplied JP but no go...it now goes to a blank screen for about 5 minutes (before I turn it off manually) after startx is typed...any ideas? or does anyone have AIM to help me?

---

### Post by xtothez on 2006-11-21
Just in case, each line will be what I entered in the X Server reconfig "exam":
Ex. "Question?" <My Answer>

"Would you like to view the X server output to diagnose?" <No>
"X server is now disabled. Restart GDM when configured correctly."

I now enter the "sudo dpkg-reconfigure xserver-xorg"

"Attempt to autodetect video hardware?" <Yes>
"Select the desired X server driver." <VESA> (per JP)
"Enter an identifier for your vid card." <ATItech R480 X850XT PCIE>
"Please enter the video card's bus identifier." <PCI:5:0:0>
"Enter amount of memory (in kB) used by vid card." <256000>
"Use kernel framebuffer device interface?" <YES>
"Autodetect keyboard layout?" <YES>
"Keyboard layout." <US>
"Select the XKB rule set to use." <XORG> (its already there, and I have no idea what it honestly is, but mine is plain, not Sun)
"Please select your keyboard model." <PC104>
"Please select your keyboard variant." < > (left blank)
"Please select your keyboard options." < > (left blank)
"Choose best which describes your mouse." <IMPS/2>
"Emulate 3 button mouse?" <YES>
"Select X.Org server modules that should be loaded by default." < > (I didn't select any, left it default.)
"Write default Files section to configuration file?" <YES>
"Attempt monitor autodetection?" <YES>
"Enter an identifier for your monitor." <Generic Monitor>
"Select video modes for X Server." <640x480 800x600 1024x768>
"Select method for selecting monitor characteristics." <Medium>
"Select monitor's best video mode." <1024x768 @ 60Hz>
"Write monitor sync ranges for config file?" <YES>
"Select desired default color depth in bits." <24bits>

Exam is done!!
now, dos style prompt appears
"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20061120230334
ubuntu@ubuntu:~$"

now I can enter code...if I use <startx> monitor turns off and computer keeps going...don't know what it is doing though, just a blank black screen... any help, please let me know?

---

### Post by junglepeanut on 2006-11-21
I am going to try some of the stuff you have and see what happens if I switch mine to it, as I have never tried entering memory for my video card, in fact I don't even remember the option....maybe this will help me out..OK

Just as sec...hope mine doesn't crash too bad.

---

### Post by junglepeanut on 2006-11-21
OK, mine still worked but, I barely have any memory so my computer went much slower. One thing is the memory call (if I read correctly) is for how much memory you would like dedicated to your video stuff and this is for only if you do not have a video card with memory already (as we do). This did not make mine crash though. 

I have an idea, but I want to read through the whole thread again, just to recall everything we have done before saying this as we may have already done it.

---

### Post by junglepeanut on 2006-11-21
Three questions.

1.) When it goes blank can you <ctrl><alt><+> through where it flashes through resolutions? That key combo is no good for me anymore but maybe it still works...

2.)Are you connected to the internet during this process? i.e. You have gone through a lot just to get it working and nothing seems to be working, but you are not afraid to input commands, so what if we just install the ati proprietary driver from the command line. I do not know if we can even do this with a live cd, it may be easier to build a small testing partition do an install and get it to work from that than do it from the live cd but hey we can try.

3.) If you want to go the livecd install ati closed source drivers which version of ubuntu did you download? 6.06 (dapper), 6.10(edgy), or 7.04(feisty).

Also would somebody really smart like aysiu or something please lend some advice, I feel that this is very close to being resolved. We are just missing one thing since his card is pretty new.

---

### Post by junglepeanut on 2006-11-21
also since vesa is not working we can try in its place. Vesa is like the old one that is supposed to wrok for everybody. 

vga

ati

radeon

fglrx

some of these may not be installed yet since it is the livecd. But I do not know.

Also are you sure it is PCI:5:0:0?

---

### Post by junglepeanut on 2006-11-21
hmm, I read the thread again. It sounds like you may actually have a full install and not be working off the cd anymore, it is just that your xserver is not configured properly? I.e. when you start now you choose either windows or ubuntu, but ubuntu is a tty (terminal) instead of the gdm (a graphical interface). And if you are connected to the net we may be able to get this running.

---

### Post by rutgerw on 2006-11-21
Are you still working on the liveCD? Or do you already have Ubuntu installed to a partition on your hard drive?

Try installing from the alternate install cd, chosing the save graphics option.

You will then get into the setup program which will most certainly work regardless of your videocard.

After you've installed ubuntu on your hard drive you may still not be able to go into your graphical environment. You should be able to get to a command-line by pressing crt-alt-f6. From their you should be able to get your X server running by installing the ATI drivers. There are numerous HOWTO's on that subject; search google for "ATI drivers Ubuntu". However all of this is of later concern, you should get to install Ubuntu first.

Hope this doesn't scare you off...

---

### Post by xtothez on 2006-11-22
sorry for the delay, but for rutgerw: I have not installed Ubuntu yet, I'm still trying to get it installed from the LiveCD.

I tried the ATI driver instead of Vesa, it provided a new message:
"Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
ubuntu@ubuntu:~$ <cursor is here>"

if I type <startx> it repeats the above...

the CD is 6.06 I believe, the 6.10 did not work correctly, it had the orange tinted Ubuntu install screen in black and white; and did not show the menu, just the Ubuntu logo and Ubuntu word...

is there any way to try it from Windows, or a different way? I don't have much experience with Linux.  or is there a way to install it from windows? like an image? I wish it would just install and then worry about graphics later, just so I can get it installed and running

the <ctrl><alt><+> did not work as hoped, it seemed to do nothing.. :(

I am not connected to the internet, my Wi-Fi card is plugged in, but not connection since it has not yet boot....

the PCI:5:0:0 is the default, I'm not sure what it is... (this could be the problem, if it is looking in the wrong location for the vid card)

also, not sure what TTY or GDM is.... sorry for being vague with my answers, but its as accurate as I can answer...

---

### Post by junglepeanut on 2006-11-22
Before continuing if you really just want to try it out I am going to suggest we try downloading the alternate cd image. The livecd has always just been problematic with certain peoples setups. When you are in windows and insert the cd, it doesn't work inside windows, sort of like looking at another computer on your computer? That is funny too, I have had my cds work inside windows that would not work on installs.

We may just need to go alternate method, I do almost all of the install I have done this way. It is quicker in my opinion and easy.

No internet means we can not get the drivers unless you put the package on a usb etc. but this is a whole ordeal too. Then you got to mount it etc etc.

I want to ask you to post lots of stuff but because it is not installed I doubt you are interested in typing lines of code (as most people have internet and something slightly working so they can just cut and paste.)

Can you look at the file /etc/X11/xorg.conf and make sure were it says drivers you see vesa.

To do this just

vim /etc/X11/xorg.conf

if you want to make changes to things in there make a back up of the original

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.confold

then 

sudo vim /etc/X11/xorg.conf

using vim is not fun for those new to it, but I like it. To make changes
hit "i" as in insert text, to stop editing hit "esc" then if you have made a mistake and are drastically messed up you dont want to save those changes you just want to start over so make sure you are outside editing by hitting escape and then ":q!" this means quit no matter the complaint.
If you want to try your changes ":wq" will save then you can startx. maybe it is just calling the wrong screen display and you can see it easily...I barely understand that file so YMMV.

I been looking in the bugs and the X850 has a lot of them, one is this but many people have theirs working so I think it is more of a "its to hard to configure this way kind of bug."

Also in the bugs as a few others have posted in this thread, almost everyone has gotten it working by using the alternate cd install. (most say it was easy too).

Sorry if that is still not what you want to hear and you still want to try and get it to work this way. If so I think we are going to have to set up your internet and get the drivers you need from ati since even vesa wont work.

---

### Post by Bealer on 2006-11-22
I've got the same problem too.

I believe it's due to my monitor. I've tried running the Live CD, but get a thin green line across the screen, whilst the loading bar is showing (it's about 90% done). 

So, I tried unplugging my monitor just as Ubuntu started loading, and it booted up no problem (I heard the startup sound). Of course I couldn't see, and plugging my tft back in, I just got a "no signal" message.

Any ideas? I've tried installing off the alternate cd. Still the same. I've tried reconfiguring xorg. Still the same. 

It's a widescreen 20" tft (Philips 200W6) with an ATI X1950GT.

---

### Post by xtothez on 2006-11-22
well Bealer, I had that same issue but the CD didn't burn properly...try that if it won't work...Ill try installing it later when I get home

---

### Post by Bealer on 2006-11-22
I've had it running previously though, and from the live disc I currently have.

When I originally installed it I had a 17" tft. I've recently changed to a 20" tft, for which the already installed Ubuntu worked fine. I then decided to do a fresh install, and upon doing so can no longer get it to work. Something's not working, or it's not configured correctly out of the box.

I've tried a number of manual settings (ati, vesa, vga), but none of them worked. This applies for both the live cd and the install I have from the alternate cd.

---

### Post by junglepeanut on 2006-11-23
Bealer : I believe you should search for changing resolutions in xorg.conf. The monitor change just needs to be fixed, more than likely to its settings which you can find online. As long as everything esle is set-up the way it was before.

Xtothez:

I was able to reproduce your error by removing everything on my install that had to do with fglrx ati etc etc. (yes I did remove everything on my daily usage computer). And I get a nice blank screen. In fact mine was worse than yours in regular user mode I could not use anything.(My keyboard was non-functioning as well.) So I had a blank screen and I could not do anything about it. I rebooted into root.

Cool same thing, but now I have some control. (Key board works.) Screen is black if I startx etc.

I followed normal driver install and was able to get everything up and running in about thirty seconds, reboot and up and running.

So if we can connect you to the internet I think we will be up and running, if not I am going to say install with the alternate and when you get to this same procedure after it is on your hard drive let me know and I or any wiki can walk you through the driver install.

So I know you say you have a wireless connection, but just because wireless drivers are also sometimes an issue and I do not have much experience with them, is there any possibility you can connect with an ethernet cord. Just have it plugged in on reboot, it should automatically be registered.
Then quickest check we can do is 

```
ping google.com
```

See if that works
Hit <ctrl>+<C> to stop it and see results.

Then if it is configured you are good to go, just follow the wiki of your choice to install the ati driver.

If not lets see what you have do 
```
ifconfig
iwconfig
```
Then if you see something that is obviously your internet connection (eth0 or ath0<= not sure on the last one mine have always been eth0 for hard line) eth1 is your wireless or something else like that etc..

You can always read the manual on any of the commands by 
```
man ifconfig
```

If you do see eth0 and ping did not work then try 

```
 sudo ifup eth0 
``` NOte up brings it up and down brings it down, ie. ifdown eth1, I sometimes have to run the sequence two or three times if I am having issues.

If you want to do your wireless you can read the manual pages on iwconfig and ifconfig, or post it and I will look up the order for wep and essid for each not really interested now, I just man it when ever I am stuck to a terminal. (hey, that is what a T.O. is for right?)

---

### Post by Bealer on 2006-11-23
> **junglepeanut said:**
> Bealer : I believe you should search for changing resolutions in xorg.conf. The monitor change just needs to be fixed, more than likely to its settings which you can find online. As long as everything esle is set-up the way it was before.

Ok, how can I do that though?

During the install, I've tried setting the display to numerous resolutions. But to no avail. 

I've also tried the "sudo dkpg-reconfig...." but you can't set the resolution in that. You can select the available resolutions, but not which one it'll use when loading.

It was definitely running on "vesa" before, I can remember that much (as I was trying to setup beryl). Surely there must be a failsafe mode for the monitor to work.

I'm guessing I need to edit xorg.conf. How can I do that from the recovery/command mode?

---

### Post by junglepeanut on 2006-11-23
Bealer: I think if you only give it one resolution it can only open under that one. Two, I meant look up your monitors specifications online, some people have monitors that are not so general and they need to enter manually the vertical and horizontal refresh rate. Earlier I posted in this thread how to use vim to make changes to files. Play with it on a file first before you use it to actually mess with important files. There are many tutorials online about vim. I reread your post also, you may want to just try reinstalling the drivers as well, this may fix your issue. 

One thing of note is a lot of things changed recently, I am not a developer and I am very new to Linux. One of these is xorg.conf, I recall my old xorg.conf looked like this

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
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
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

Section "Extensions"
        Option  "Composite" "0"
EndSection

```




[BOLD]BUT[/BOLD]





My new xorg.conf looks like
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "disable"
EndSection


```


Notice how much shorter the second is. Roughly 15-20 lines, basically all my screen resolutions gone...then again that was the first xorg.conf I got to work before the driver was installed once it was installed I then had this, remember the middle one i how it looks now.

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Option "DRI" "true" 
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	Option "AGPFastWrite" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

Section "Extensions"
	Option	"Composite" "false"
EndSection

Section "Extensions"
	Option	"Composite" "disable"
EndSection

```

And that was even longer so everything would work with beryl, compared to everything working now with a much smaller footprint.

---

### Post by junglepeanut on 2006-11-23
Early I posted to try > lso since vesa is not working we can try in its place. Vesa is like the old one that is supposed to wrok for everybody.

vga

ati

radeon

fglrx

some of these may not be installed yet since it is the livecd.
I was wondering how did the radeon work out? I found a bug that said that worked for some, did you try that one?

---

### Post by xtothez on 2006-11-27
thx JP, I'll try that hopefully this week when I have a few... it's been finals week and thxgiving and I've been short on time... I'll try that later this week and hopefully get it working...I'll keep in touch

---

### Post by junglepeanut on 2006-11-29
Also there is a good chance as I don't remember that the ati propietary driver is on the cd so even if you dont have internet you could just 
```

sudo apt-get update 
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

```
then edit /etc/X11/xorg.conf
```

sudo vim /etc/X11/xorg.con

```
 adding this comment in.
```

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

I think Shuttleworth et al said on a video I watched that they have been sneaking it on CD's for a while now, if not when Feisty comes out on CD it will definitely be there.

So that could be a work around to the internet issue. Also some of the bug reports (very few) reported the trident driver getting them up and running.

---

