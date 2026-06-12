---
title: "Help!!!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by fettster on 2008-02-17
I enabled the NVIDIA driver by using the Restricted Drivers Manager, and now when I boot up, the only way I can see my screen is to plug my laptop into an external monitor.  When I first start it up, everything works fine; it shows the Ubuntu logo while it loads, but once it goes to where I sign in, the laptop screen goes dark.  I can see everything just fine on an external monitor, but I can't just carry a monitor around with my laptop.  Someone please help me fix this, so I can use the laptop screen again. 

Yes, I know disabling the NVIDIA driver will fix it, but I really want to be able to use it for things like OpenGL and Desktop Effects.

Please help me...

---

### Post by JoshuaRL on 2008-02-17
Try Envy.  It will automatically install the nVidia driver for your computer.  Really easy, works very well.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by uberlube on 2008-02-17
Dont use the restricted drivers. Download ENVY and use it to install the linux drivers and then reboot. If then you still get at blank screen at login, reboot and in GRUB choose add VGA=791 to the startup sequence.

---

### Post by JoshuaRL on 2008-02-18
> **uberlube said:**
> Dont use the restricted drivers. Download ENVY and use it to install the linux drivers and then reboot. If then you still get at blank screen at login, reboot and in GRUB choose add VGA=791 to the startup sequence.

Just FYI, Envy uses the restricted proprietary drivers.  It will autodetect and install the appropriate ones for your system.  For nVidia and ATI that are supported it works really well.

---

### Post by uberlube on 2008-02-18
O my bad. I was always under the assumption that it downloaded the proper linux version of the drivers instead of using the ones that show up in the restricted driver manager.

---

### Post by kelbizzle on 2008-02-18
before gutsy I was never able to get compiz working on my gateway with a radeon 200m express. When Gutsy came along with the restricted I had no problems at all. It works great  . Even configured my broadcom wirless card with no problems.

---

### Post by JoshuaRL on 2008-02-18
Well, it does.  But only the proprietary ones, not the open source DRI stuff.  It just makes it really easy to figure out which one you need and install it correctly for your stuff.  But yeah, only the proprietary ones.  It'd be cool if one day it covered all graphics cards and included the DRI drivers.  But I'm sure that would be a huge amount of work to get that right.

---

### Post by fettster on 2008-02-18
I tried using Envy (after disabling the restricted driver i had enabled, and restarting my computer), but it didn't work. It gave me an error message

[IMG]http://sambofett.googlepages.com/ErrorMessage.jpg[/IMG]

---

### Post by JoshuaRL on 2008-02-18
Whoa that's a big picture.  You might try using the Manage Attachments button near the bottom when posting.

So what's the output of:
```

gedit /var/log/envy-installer.log

```

If it says you don't have the permissions to see it, try:
```

gksu gedit /var/log/envy-installer/log

```

Pretty desktop though.  What is that app bar?  I know it's not AWN.

---

### Post by fettster on 2008-02-18
Sorry about the giant picture. I'm kinda new here and don't know how everything works.

Anyways, the results of /var/log/envy-installer.log are 

python pulse.py nvidia
root@localhost:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.10
Ubuntu Gutsy 32bit
Your graphic card has been detected as a GeForce4 440 Go
Your graphic card is supported by the new legacy driver
OK: All the packages are installed
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
libqt3-mt-dev
kernel-wedge
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkjdsp-java python-opengl libmono-security1.0-cil libglitz-glx1 liboggz1
  libmono-system-web1.0-cil python-pygame libmp3spi-java libjlayer-java
  libcddb2 libsgutils1 libvorbisspi-java libmono-cairo2.0-cil boo
  libcommons-logging-java libakode2 python-imaging libtaglib2.0-cil
  libmono1.0-cil libmono-data-tds1.0-cil libbasicplayer-java
  libmono-system-data1.0-cil libipoddevice0 python-setuptools libtritonus-java
  cortado liblockfile1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  comerr-dev libatk1.0-dev libaudio-dev libcairo2-dev libcupsys2-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev
  libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgnutlsxx13
  libgpg-error-dev libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev
  liblzo2-dev libmng-dev libopencdk8-dev libpango1.0-dev libpng12-dev
  libpopt-dev libqt3-headers libsm-dev libtasn1-3-dev libx11-dev libxau-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxmu-dev libxmu-headers libxrandr-dev
  libxrender-dev libxt-dev mesa-common-dev qt3-dev-tools
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev zlib1g-dev
Suggested packages:
  libcairo2-doc libgcrypt11-doc libglib2.0-doc gnutls-doc gnutls-bin
  libgtk2.0-doc krb5-doc libpango1.0-doc libqt3-i18n qt3-doc mailx
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  comerr-dev kernel-wedge libatk1.0-dev libaudio-dev libcairo2-dev
  libcupsys2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgcrypt11-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev
  libgnutls-dev libgnutlsxx13 libgpg-error-dev libgtk2.0-dev libice-dev
  libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev liblzo2-dev libmng-dev
  libopencdk8-dev libpango1.0-dev libpng12-dev libpopt-dev libqt3-headers
  libqt3-mt-dev libsm-dev libtasn1-3-dev libx11-dev libxau-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers
  libxrandr-dev libxrender-dev libxt-dev libxtst-dev libxxf86misc-dev
  libxxf86vm-dev mesa-common-dev qt3-dev-tools sharutils
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xtrans-dev zlib1g-dev
0 upgraded, 69 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.5MB of archives.
After unpacking 69.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libcairo2-dev
E: There are problems and -y was used without --force-yes
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

---

### Post by JoshuaRL on 2008-02-18
Okay, try this:
```

sudo apt-get install --fix libcairo2-dev libqt3-mt-dev kernel-wedge sharutils libgtk2.0-dev libxxf86misc-dev libxtst-dev libxxf86vm-dev libxinerama-dev

```

What I'm trying to do is to install those things it said it needed but couldn't get.  What happens then?

---

### Post by fettster on 2008-02-18
The root terminal gave me this 
```

root@localhost:/home/fettster# sudo apt-get install --fix libcairo2-dev libqt3-mt-dev kernel-wedge sharutils libgtk2.0-dev libxxf86misc-dev libxtst-dev libxxf86vm-dev libxinerama-dev
E: Command line option --fix is not understood
root@localhost:/home/fettster#
```

---

### Post by JoshuaRL on 2008-02-18
Okay, sorry.  Try this:
```

sudo apt-get install libcairo2-dev libqt3-mt-dev kernel-wedge sharutils libgtk2.0-dev libxxf86misc-dev libxtst-dev libxxf86vm-dev libxinerama-dev

```

---

### Post by fettster on 2008-02-18
Wow, that was a long list...

Now what? Try to run Envy again?

---

### Post by JoshuaRL on 2008-02-18
Yep, see if it works this time.

---

### Post by fettster on 2008-02-18
It finished and now it's asking if I want my xorg.conf to be automatically configured. It recommends yes. What would you say? yes or no?

---

### Post by JoshuaRL on 2008-02-18
Yes.  That will allow the script to change that file so it runs correctly for your system. 

 If you're not aware, Xserver is the GUI you're used to seeing in Ubuntu and indeed most of Linux.  Many things in Linux use plain text configuration files, often labelled with ".conf" or ".list" to handle configuration. 

Letting Envy automatically configure that will be exactly what you want.

---

### Post by fettster on 2008-02-18
Okay, I did that and it came up with the same problem i had originally.  Envy had re-enabled the smae restricted driver which made the screen go out at the login screen.  I disabled the driver, restarted, and it said that the X server had a fatal server error and that no screens could be found. I recovered this with a command I looked up ```

dpkg-reconfigure -phigh xserver-xorg
```
So now, I'm back and really confused.

---

### Post by fettster on 2008-02-18
Sorry it took me so long on my response as well.  It took me a bit to recover from the X server error.

---

### Post by fettster on 2008-02-18
What about using Envy to do a manual install of the driver.  When I clicked that, it gave me three options: 

version 169.09
version 96.43.01
version 71.86.01

---

### Post by JoshuaRL on 2008-02-18
I probably should have asked this right off, but what kind of nVidia card do you have?

---

### Post by fettster on 2008-02-18
This is what I could gather from the Device Manager

[IMG]http://sambofett.googlepages.com/Screenshot-DeviceManager.png[/IMG]

---

### Post by JoshuaRL on 2008-02-18
Alright, it seems that your card needs the legacy driver.

I found this thread on doing it manually:

[http://ubuntuforums.org/showthread.php?t=666478](http://ubuntuforums.org/showthread.php?t=666478)

But can you try Envy again, this time using the Legacy driver and see if that works?

---

### Post by fettster on 2008-02-18
Okay, so I tried to use the link you gave me, but my xorg.conf doesn't match his.  I tried to follow his directions, but ended up with the same fatal server error where it could not find any screens.  Thankfully, this time I knew how to recover it, and was able to do so fairly quickly.

---

### Post by JoshuaRL on 2008-02-18
Okay, can you try the Legacy driver in Envy?

---

### Post by fettster on 2008-02-18
How would I do that. 
These are the options it gives me
[IMG]http://sambofett.googlepages.com/Screenshot-Envy.png[/IMG]


Sorry for the delay, my laptop locked up and I had to start a new session.

---

### Post by JoshuaRL on 2008-02-18
Alright, try this page:

[http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)

Three easy steps to installation:

1).  Download the file on that page

2).  Put the following into terminal:
```

cd ~/Desktop

```

3).  Put the following into the terminal:
```

sh NVIDIA-Linux-x86-96.43.05-pkg1.run

```

How does that work?

---

### Post by fettster on 2008-02-18
Wat do I do for this?

[IMG]http://sambofett.googlepages.com/Screenshot-rootlocalhost-home-fettst.png[/IMG]

---

### Post by JoshuaRL on 2008-02-18
Okay, im sorry.

Try logging out and booting into the Rescue Mode in the Grub Menu.  You'll need to hit Escape when the Loading Grub thing comes up.  It'll do a bunch of stuff on the screen loading the OS and then dump you at the terminal as root.

Write down the exact three steps as spelled and try them again.

---

### Post by fettster on 2008-02-18
Oh, thank you.  I know exactly what you're talking about.  I see it every time I boot up, because I have a dual boot.

---

### Post by hyper_ch on 2008-02-18
next time use a descriptive topic title and not a generic "need help" one.

---

### Post by JoshuaRL on 2008-02-18
Hey, don't horn in Hyper_ch!  This nooby is mine!

:p

---

### Post by fettster on 2008-02-18
Thank You JoshuaRL

Anyways, I tried installing it in recovery mode as the administrator, but it gave me this error message.

> You appear to be running in runlevel 1; this may cause problems. For example: some distributions that use devfs do not run the devfs daemon in runlevel 1; making it difficult for 'nvidia-installer' to correctly set up the kernel module configuration files. It is recommended that you quit installation now and switch to runlevel 3 ('telinit' 3') before installing
Quit installation now (select 'No' to continue installation')
      Yes        No


I don't have the slightest idea what that means

---

### Post by JoshuaRL on 2008-02-18
Alright, try this

```

login

```

It will allow you to login to your profile in the CLI system.  Try that and then the same three steps.

---

### Post by fettster on 2008-02-18
It gave me the same error message...

---

### Post by JoshuaRL on 2008-02-18
Alright, not sure how to fix that.

Try this:

```

sudo apt-get install nvidia-glx-legacy

```

It's the open-source driver I found in Synaptic.  Thought we'd give it a try since there's some issues with installing the proprietary one.

---

### Post by fettster on 2008-02-18
Thank you so much for all your help. I have to get off for now, but will be back on to hopefully get this finished Tomorrow or Tuesday.

---

### Post by JoshuaRL on 2008-02-18
Cool, because I need some sleep.  I'll check back later.

---

### Post by fettster on 2008-02-18
> **JoshuaRL said:**
> Alright, not sure how to fix that.

Try this:

```

sudo apt-get install nvidia-glx-legacy

```

It's the open-source driver I found in Synaptic.  Thought we'd give it a try since there's some issues with installing the proprietary one.

Okay, so now what?  I did that and nothing changed that I can tell.

---

### Post by Sceiron on 2008-02-18
Can u type: glxinfo
in terminal and paste the output here?

---

### Post by fettster on 2008-02-18
> **Sceiron said:**
> Can u type: glxinfo
in terminal and paste the output here?

root@localhost:/home/fettster# glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)
root@localhost:/home/fettster# 
root@localhost:/home/fettster#

---

### Post by Sceiron on 2008-02-18
[http://ubuntuforums.org/showthread.php?t=697629&highlight=wrong+output+from+glxinfo](http://ubuntuforums.org/showthread.php?t=697629&highlight=wrong+output+from+glxinfo)

Looks like u got the same problems as i have in this thread....
Not found a solution yet, ill let u know if i discover anything...But there a some links on this thread with soulutions that have worked for others.'
Did not work for me, but maybe for you :)

Hope this dont make it more confusing.

Sceiron

---

### Post by JoshuaRL on 2008-02-18
Could you post your xorg.conf?

---

### Post by fettster on 2008-02-18
> **JoshuaRL said:**
> Could you post your xorg.conf?

Here it is...
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
	Identifier	"nVidia Corporation NV17 [GeForce4 440 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
```

---

### Post by JoshuaRL on 2008-02-18
Okay, the open source driver is installed.

Try:
```

sudo apt-get install glx

```
That will install the GLX package.  I'm not sure if it is installed with nvidia-glx-info, so I thought I'd try.

Then after that finishes try the following and let that run without messing with it for five lines:
```

glxgears

```
That is a poor benchmark, but works well enough to give us some ideas for how the system is running.

Then:
```

glxinfo | grep direct

```
Same code as Sceiron posted, but with an arguement looking for direct rendering (3D hardware acceleration),

---

### Post by ayenack on 2008-02-18
> **JoshuaRL said:**
> Alright, try this page:

[http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)

Three easy steps to installation:

1).  Download the file on that page

2).  Put the following into terminal:
```

cd ~/Desktop

```

3).  Put the following into the terminal:
```

sh NVIDIA-Linux-x86-96.43.05-pkg1.run

```

How does that work?

JoshuaRL hope you don't mind me butting in.

To do the above you'll need to stop GDM by using Ctrl+Alt+F1 then.

[B]cd ~/Desktop
sudo sh NVIDIA-Linux-x86-96.43.05-pkg1.run[/B]

Then when it's all done.

**sudo reboot**

Not sure that's the correct driver for his card though.

---

### Post by JoshuaRL on 2008-02-18
Yeah, we ran into that.  I forgot you needed to stop GDM.  Thanks man.

---

### Post by ayenack on 2008-02-19
No probs. I think that there's a problem with older nvidia cards on 7.10 for some reason it never seems to install the correct driver or the driver won't config properly. Feisty seems to be fine though and there's not that much difference between the two. Might even be better to try Xubuntu Feisty lighter so will be better for an older system and similar to gnome in looks.

---

### Post by JoshuaRL on 2008-02-19
That's a good idea.  I'm about out of ideas if this doesn't work.

It really suprised me when Envy couldn't install and config the right driver.

---

### Post by ayenack on 2008-02-19
You know what people rave about Envy but it's really just an example of not knowing how to install your graphics card. In most cases if the nvidia installer won't work or the Restricted Drivers Manager won't then Envy isn't going to make it work either.

I think that it's something to do with the 2.6.22-14.21/52  kernel in 7.10. If you were absolutely desperate I suppose you could compile the kernel or search the repo's for whatever is missing.

Just a thought but might not have the correct headers.... although Envy should have been able to sort that out I think.

I'd go for Feisty and see if that works or just not bother with fancy graphics. It's a pretty old card anyway.

BTW 1600x1200 in fettster xorg.conf seems way to high for this card. And this doesn't look good either HorizSync 28-80 VertRefresh 43-60. Maybe should take a look at the monitors manual to see what refresh rates it supports or do a search on the net for a tech sheet on it.

---

### Post by fettster on 2008-02-19
Thank you everyone for all your advice, especially you JoshuaRL, for taking so much time to help me out.  Unfortunately, nothing fixed my NVIDIA driver problem.  The command with glx returned some error that glx could not be found. The command with the NVIDIA driver downloaded to my desktop only enabled another proprietary drive, as did Envy.  Both of these ended up causing the same problem I originally reported.  That is, my laptop screen would go black at the login screen, and I could only see my desktop when I plugged it into an external monitor.  

Oh well, I guess I'll just have to live without OpenGL, Beryl-Compiz, and Desktop Effects...     :frown:

---

### Post by JoshuaRL on 2008-02-19
You might try the other option mentioned here and try installing Feisty.  It may work a little better in detecting and configuring your older card.

---

### Post by ayenack on 2008-02-19
Just to make life a bit easier. Before you try to install any new graphics drivers on a fresh install of Ubuntu whatever version do this so you can recover your xorg.conf if you end up at the command line.

In Terminal.

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup** (cp stands for copy and all this will do is copy your xorg.conf file and rename it xorg.conf_backup leaving the original in place.)

Then if you end up at the command line you can do this to restore your original xorg.conf and GUI.

In Terminal.

**sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf**

Make sure to use capitol "X" in all instances of "X11" or it won't work.

IMO you should install feisty I'm think that it recognises your card and will install the drivers from Restricted Drivers Manager.

Another thought occurs have tried tis. In Terminal.

**gksu nvidia-settings**

And try to set up dual screen from there?

You'll have to copy and paste the settings from **Save to X Configuration File** in the nvidia settings menu to xorg.conf because it doesn't seem to do it otherwise. If this doesn't work there maybe a setting in your BIOS to turn off the external monitor.

If it all goes wrong do what I suggested previously above to recover your xorg.conf & GUI.

---

