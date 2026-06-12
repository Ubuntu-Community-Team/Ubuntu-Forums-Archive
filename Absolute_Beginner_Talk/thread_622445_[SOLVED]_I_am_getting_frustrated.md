---
title: "[SOLVED] I am getting frustrated"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-24
I have installed various distros of Linux at least twice today. I have installed Ubuntu now for the second time today.

I have made tons of postings here. I have gone back and tried to research them and have gotten nowhere. 

I am starting now with a fresh install. I have installed the proprietary driver for my video card. ATI Radeon X1950Pro PCIe. I have gone to one of my previous threads to get the cube going and to enable desktop effects and tried stuff.

I don't know what is wrong. I cannot get the cube. I do not know if my video driver is installed correctly. In fact at this point I do not know anything about what to do. Perhaps this is the wrong way of looking at it, but the way I know if my video card is working properly is if the cube works. 

Please help this frustrated old guy.

---

### Post by dwhitney67 on 2007-11-24
Do you have Gnome (or other window manager) running successfully after installing Linux?  If so, I would say your video card is running.  It is at the desired resolution?

I hope that your efforts today were not expended just so that you can get the "cube".  It's nothing more than a novelty.

---

### Post by HermanAB on 2007-11-24
Yeah well, good luck with that.  The sad truth is that after you have spent countless hours getting Compiz to work, you'll likely get fed-up with in about 2 minutes later, but don't let me discourage you.  I'm sure that you have learned lots of other things already that you would not have learned otherwise...

Cheers,

Herman

---

### Post by bgast1 on 2007-11-24
I have Gnome running. I think. I believe that is what installs from the live CD. My screen resolution is at the default for my monitor. When I installed the restricted driver it set itself up that way. I have LG Flatron Wide 22" monitor. Don't recall the model number right now. 

Here is some output from glxgears:

50972 frames in 5.0 seconds = 10194.392 FPS
54729 frames in 5.0 seconds = 10945.667 FPS
54694 frames in 5.0 seconds = 10938.730 FPS
54334 frames in 5.0 seconds = 10866.741 FPS
54841 frames in 5.0 seconds = 10968.069 FPS
54843 frames in 5.0 seconds = 10968.428 FPS
54824 frames in 5.0 seconds = 10964.620 FPS
54374 frames in 5.0 seconds = 10874.705 FPS
54739 frames in 5.0 seconds = 10947.679 FPS
54718 frames in 5.0 seconds = 10943.539 FPS
54512 frames in 5.0 seconds = 10902.304 FPS
54822 frames in 5.0 seconds = 10964.244 FPS
54763 frames in 5.0 seconds = 10952.495 FPS
54706 frames in 5.0 seconds = 10938.826 FPS

I know that the cube is a novelty, but I had it before, My efforts today were to find the right distro for me. It would appear that Ubuntu is it.

---

### Post by nick_h on 2007-11-24
So what happens when you go to System->Preferences->Appearance and enable "Visual Effects"?

---

### Post by CatKiller on 2007-11-24
> **bgast1 said:**
> I don't know what is wrong. I cannot get the cube. I do not know if my video driver is installed correctly.

From your glxgears scores, I think you've got your graphics working OK. I would do a ```
sudo aptitude install compizconfig-settings-manager
``` to get the "Advanced Desktop Effects Settings" tool that lets you configure the plugins and then play with that. The "Desktop Effects" that get turned on with the System -> Preferences -> Appearance tool use a "Desktop Wall" instead of the cube to change workspaces.

---

### Post by Vadi on 2007-11-24
Or just try **compiz --replace** in the terminal, what does it say?

---

### Post by bgast1 on 2007-11-24
> **Vadi said:**
> Or just try **compiz --replace** in the terminal, what does it say?

This is the output:
bob@bob-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Xavieran on 2007-11-24
Stay tuned :-)...
I'll google it.

please post your /etc/X11/xorg.conf file just open it up with gedit and copy-paste wrap it in CODE tags please thx...

P.S. were you using Gutsy before...? from what I can tell it is a Problem with feisty...

Have a look at this [http://ubuntuforums.org/showthread.php?t=593348&page=3]("http://ubuntuforums.org/showthread.php?t=593348&page=3")

---

### Post by Vadi on 2007-11-24
Yeah, I'm not much versed in driver issues - my card works well with the open source radeon driver, and I'm happy. Lets home someone who has a better card will help you.

---

### Post by bgast1 on 2007-11-24
How do I wrap something in CODE tags?

---

### Post by Xavieran on 2007-11-24
Perhaps try this:

back up that file before you do anything to it(just copy it and end it with .bak)

command: sudo gedit /usr/bin/compiz-manager

gedit will open up and then add this to the bottom

```
#Trying to get Desktop Effects to work
WHITELIST = "fglrx"
```

if WHITELIST is already there just add fglrx to it.

---

### Post by bgast1 on 2007-11-24
> **Xavieran said:**
> Stay tuned :-)...
I'll google it.

please post your /etc/X11/xorg.conf file just open it up with gedit and copy-paste wrap it in CODE tags please thx...

P.S. were you using Gutsy before...? from what I can tell it is a Problem with feisty...

Have a look at this [http://ubuntuforums.org/showthread.php?t=593348&page=3]("http://ubuntuforums.org/showthread.php?t=593348&page=3")

Please forgive my ignorance I don't know how to post that file.

---

### Post by overdrank on 2007-11-24
> **bgast1 said:**
> How do I wrap something in CODE tags?

HI this is a screen shot of the code tags and click on the comment # as shown in the pic and insert text between the tags

[[IMG]http://img77.imageshack.us/img77/7548/codetagsjr8.th.png[/IMG]](http://img77.imageshack.us/my.php?image=codetagsjr8.png)

---

### Post by Xavieran on 2007-11-24
I understand...type this command in (no it wont rm anything! ;-))

gedit /etc/X11/xorg.conf

then copy and paste the text into your ubuntu forums post...to wrap CODE tags around it click the hash in the top right area of the reply to thread thing...

Hope I'm being helpful :-)

---

### Post by NightCrawler03X on 2007-11-24
> *Originally posted by bgast1*
I am getting frustrated
I have installed various distros of Linux at least twice today. I have installed Ubuntu now for the second time today.

I have made tons of postings here. I have gone back and tried to research them and have gotten nowhere.

I am starting now with a fresh install. I have installed the proprietary driver for my video card. ATI Radeon X1950Pro PCIe. I have gone to one of my previous threads to get the cube going and to enable desktop effects and tried stuff.

I don't know what is wrong. I cannot get the cube. I do not know if my video driver is installed correctly. In fact at this point I do not know anything about what to do. Perhaps this is the wrong way of looking at it, but the way I know if my video card is working properly is if the cube works.

Please help this frustrated old guy.

Dude, judging from your posts it looks like your new to Linux.

You need to pace yourself, no one learns everything in a day. :)

---

### Post by Xavieran on 2007-11-24
Perhaps try this:

back up that file before you do anything to it (just copy it and end it with .bak)

command: 1.sudo cp /usr/bin/compiz-manager /usr/bin/compiz-manager.bak
                    then...
                  2.sudo gedit /usr/bin/compiz-manager
 
gedit will open up and then add this to the bottom

Code:

#Trying to get Desktop Effects to work
WHITELIST = "fglrx"

if WHITELIST is already there just add fglrx to it.

---

### Post by bgast1 on 2007-11-24
[HTML]# xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"L226WT"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"L226WT"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1440x1440"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection[/HTML]

---

### Post by bgast1 on 2007-11-24
> **NightCrawler03X said:**
> Dude, judging from your posts it looks like your new to Linux.

You need to pace yourself, no one learns everything in a day. :)


Yes I am very new. If I can just get this video driver working properly tonight I will be in heaven.

---

### Post by Xavieran on 2007-11-24
This bit:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection
```
Looks fine but try following my instructions above. /\

I think I may have found the problem!
back up /etc/X11/xorg.conf as detailed above then...

command :sudo gedit /etc/X11/xorg.conf

gedit will open up 

```
now go to this part:
Section "Module"
	Load		"glx"
EndSection
```

and change "glx"
to "fglrx"

save and restart X (ctrl-alt-backspace)

---

### Post by KIAaze on 2007-11-24
> **bgast1 said:**
> I know that the cube is a novelty, but I had it before.

Then you're in the same situation as me: I had it before and now it doesn't work anymore. :/

What I find strange is that in all this thread, you never gave any info about your graphics card.
What's your graphics card? ATI? Nvidia?

How did it run before? What distro? What did you do to make it work?

I don't have time right now to try to get compiz working right now, but I think there are mainly to things to play around with:
-driver: open source or proprietary
-AiGLX or XGL

For me, the cube that worked was Beryl in Debian. I think it was the open driver+AiGLX, but I'm not sure. (video card: ATI Radeon IGP 345M)
Compiz never worked well for me (only in OpenSUSE and not fluid).

Maybe you should try Beryl instead of Compiz-fusion. :/

---

### Post by bgast1 on 2007-11-24
I feel really dumb here. I was able to use a DOS machine once upon a time and I do know a little bit about file structure but I don't understand why I am getting this output.
[HTML]bob@bob-desktop:~$ sudo cp /usr/bin/compiz manager /usr/bin/compiz-manager.bak
[sudo] password for bob:
cp: target `/usr/bin/compiz-manager.bak' is not a directory
bob@bob-desktop:~$ cp /usr/bin/compiz-manager.bak
cp: missing destination file operand after `/usr/bin/compiz-manager.bak'
Try `cp --help' for more information.
bob@bob-desktop:~$ 

[/HTML]

---

### Post by bgast1 on 2007-11-24
> **KIAaze said:**
> Then you're in the same situation as me: I had it before and now it doesn't work anymore. :/

What I find strange is that in all this thread, you never gave any info about your graphics card.
What's your graphics card? ATI? Nvidia?

How did it run before? What distro? What did you do to make it work?

I don't have time right now to try to get compiz working right now, but I think there are mainly to things to play around with:
-driver: open source or proprietary
-AiGLX or XGL

For me, the cube that worked was Beryl in Debian. I think it was the open driver+AiGLX, but I'm not sure. (video card: ATI Radeon IGP 345M)
Compiz never worked well for me (only in OpenSUSE and not fluid).

Maybe you should try Beryl instead of Compiz-fusion. :/

ATI Radeo X1950 Pro, PCIe , I used Ubuntu 7.10 before. I installed PCLOS today and had no trouble with my driver, or the cube. That was in Beryl though.  I know that there is an ATI driver at the website. I can download it to the desktop, but I can't get it installed, because I don't understand what they want me to do there.

---

### Post by Xavieran on 2007-11-24
KIAze-
> I have installed various distros of Linux at least twice today. I have installed Ubuntu now for the second time today.

I am starting now with a fresh install. I have installed the proprietary driver for my video card. ATI Radeon X1950Pro PCIe. I have gone to one of my previous threads to get the cube going and to enable desktop effects and tried stuff.

I don't know what is wrong. I cannot get the cube. I do not know if my video driver is installed correctly. In fact at this point I do not know anything about what to do. Perhaps this is the wrong way of looking at it, but the way I know if my video card is working properly is if the cube works.



Anyway back to the thread just do gksu nautilus and navigate to /usr/bin locate compiz-manager and then double copy and paste it.I am not currently working at a linux computer so bear with me!

---

### Post by bgast1 on 2007-11-24
> **Xavieran said:**
> This bit:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection
```
Looks fine but try following my instructions above. /\

I think I may have found the problem!
back up /etc/X11/xorg.conf as detailed above then...

command :sudo gedit /etc/X11/xorg.conf

gedit will open up 

```
now go to this part:
Section "Module"
	Load		"glx"
EndSection
```

and change "glx"
to "fglrx"

save and restart X (ctrl-alt-backspace)

Alright. I managed to get this done.

---

### Post by Xavieran on 2007-11-24
Is it working? :-D

---

### Post by bgast1 on 2007-11-24
No. Going to System ->Appearance -> Preferences won't let me change to any of the other settings except none either.

---

### Post by Xavieran on 2007-11-24
Try running compiz --replace again.
if it still says something about the WHITELIST do this.


command: sudo gedit /usr/bin/compiz-manager

gedit will open up and then add this to the bottom

Code:

#Trying to get Desktop Effects to work
WHITELIST = "fglrx"

if WHITELIST is already there just add fglrx to it.

---

### Post by bgast1 on 2007-11-24
I think that I may have screwed up those files you asked me to edit. Do I have to do another install?

---

### Post by Xavieran on 2007-11-24
Did you back them up?

Can you run compiz --replace and post the output?

Could you post the current versions of the files you think you have screwed up?

if so just replace the new files with the old files.

---

### Post by bgast1 on 2007-11-24
I think I backed the ones you told me to and I replaced it, but it doesn't look right to me.

 [HTML]# xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"L226WT"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"L226WT"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"	"1440x1440"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"fglx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection[/HTML]

---

### Post by Xavieran on 2007-11-24
Typo here I think ```
Section "Module"
	Load		"fglx"
EndSection
```

change the fglx to fglrx

Then try compiz --replace and post the output

---

### Post by mc4man on 2007-11-24
@bgast1 I don't see that you've confirmed compiz-manager has been installed
when you tried to back it up you left out the  -    
Which package did you install?

---

### Post by bgast1 on 2007-11-24
[HTML]bob@bob-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity [/HTML]

This is what I got. Also though because I was afraid that I had screwed up, I uninstalled the restricted driver, then reinstalled it. Before it was really simple to solve this problem. I just can't remember what I did.

---

### Post by bgast1 on 2007-11-24
compiz manager has been installed.  When I try to change my Appearance Preferences I get a pop up that says 'The Composite Extension is not available.' Then the screen locks up and I can't do anything in Appearance Preferences

---

### Post by tiachopvutru on 2007-11-24
> **bgast1 said:**
> [HTML]bob@bob-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity [/HTML]

This is what I got. Also though because I was afraid that I had screwed up, I uninstalled the restricted driver, then reinstalled it. Before it was really simple to solve this problem. I just can't remember what I did.

The driver in Restricted Driver Manager doesn't have AIGLX support, so you would need XGL installed. For that:

```
sudo apt-get install xserver-xgl
```

You won't need XGL if you get the latest driver from ATI site.

---

### Post by bgast1 on 2007-11-24
I downloaded the driver from the ATI site to my desktop. How do I go about installing it. I seem to be learning a lot, but still don't know how to do even the most basic things. :confused:

---

### Post by tiachopvutru on 2007-11-24
> **bgast1 said:**
> I downloaded the driver from the ATI site to my desktop. How do I go about installing it. I seem to be learning a lot, but still don't know how to do even the most basic things. :confused:

You could have kept the driver from Restricted Driver Manager and use it alongside with XGL, or you can try the latest driver available from ati website. In this case, it looks like you want to try the latest driver.

Make sure you've downloaded the latest one, which is 7.11 Catalyst (or 8.43). If you happen to get 8.42, which is a month older, you can get 7.11 Catalyst here: [http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

Make sure you uninstall the driver from Restricted Driver Manager first (just for as a precaution). Now, go to the terminal and type

```
sudo sh driver_name
```

Replace driver_name with whatever the driver name is. Alternatively, you can just drag the file onto the terminal. A GUI installer will pop up so just follow the instruction. After you're done, restart. It may work right away or you may need to do some configuration to /etc/X11/xorg.conf. If the latter is the case, go here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Configure_the_Driver]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Configure_the_Driver"). Simply follow the instruction there.

---

### Post by bgast1 on 2007-11-24
> **tiachopvutru said:**
> The driver in Restricted Driver Manager doesn't have AIGLX support, so you would need XGL installed. For that:

```
sudo apt-get install xserver-xgl
```

You won't need XGL if you get the latest driver from ATI site.
 
I kept the restricted driver. I typed in the code you suggested, changed my Appearance Preferences, went to Advanced Desktop Effects Settings, checked the appropriate boxes and it works

![SIZE="7"]Thank You![/SIZE] Now how do we mark this one solved.? You have no idea how frustrated I was. That cube was the most beautiful site I've seen all day.

---

### Post by tiachopvutru on 2007-11-24
> **bgast1 said:**
> I kept the restricted driver. I typed in the code you suggested, changed my Appearance Preferences, went to Advanced Desktop Effects Settings, checked the appropriate boxes and it works

![SIZE="7"]Thank You![/SIZE] Now how do we mark this one solved.?

You're welcome. If you want to try AIGLX, you can follow my previous post, although you may run into more headache so DON'T if you do not want to experience it.

To mark the thread as solve, look on the top right on the first post of the page, you'll see the words **Thread Tools**, click on it and choose the last option.

---

### Post by bgast1 on 2007-11-24
Thanks. I going to mark it solved. Also, I don't need anymore headaches today. This has been quite enough, and it works I'm not about to break it.

---

### Post by overdrank on 2007-11-24
> **bgast1 said:**
> Thanks. I going to mark it solved. Also, I don't need anymore headaches today. This has been quite enough, and it works I'm not about to break it.

Good luck and if you break it the best part is you get to keep both pieces ! :)

---

