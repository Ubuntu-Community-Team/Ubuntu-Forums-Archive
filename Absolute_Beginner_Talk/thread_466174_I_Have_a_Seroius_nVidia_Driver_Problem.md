---
title: "I Have a Seroius nVidia Driver Problem"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-06
I have now come to the conclusion that I must do something seroiusly wrong when I try and install nVidia drivers for my graphic cards.

I first tried to install my driver for my nVidia GeForce 7950GT under SUSE with no luck, then under Ubuntu with no luck where I got these screens:
[[IMG]http://img234.imageshack.us/img234/2235/01startupdo8.th.jpg[/IMG]](http://img234.imageshack.us/my.php?image=01startupdo8.jpg)

When I say no to view the server output (which I by the way understand nothing of) I get the following screen saying that X has been disabled:
[[IMG]http://img66.imageshack.us/img66/7339/02xdisabledzl0.th.jpg[/IMG]](http://img66.imageshack.us/my.php?image=02xdisabledzl0.jpg)

I then tried with a GeForce4 Ti 4200, Got exactly the same screens.

The last time I installed them the following way:

1. Backing up xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

2. Opened Synaptic, and installed:
```
nvidia-glx
```

3. Opened terminal and typed:
```
sudo nvidia-glx-config enable
```

4. Rebooted and got the same screen as above, I then reverted back to the old configuration and run the whole thing through again trying to install
```
nvidia-glx-new
```
instead with the same result.

Can anyone see where I'm making the mistake?

P.S. I posted about my initial problem with my nVidia 7950GT [here]("http://ubuntuforums.org/showthread.php?t=448505")

---

### Post by Songwind on 2007-06-06
Is there any particular reason you are doing a manual install instead of just installing the "nvidia-glx" package?

---

### Post by Nythain on 2007-06-06
umm... point a... to the responder, its pretty obvious they are trying to install via apt-get...

point b... im not sure if you have already tried this, but after making sure the drivers are installed, type
sudo dpkg-reconfigure xserver-xorg
answer the questions to the best of your knowledge, defaults are ok on some of them, make sure to select the nvidia driver...
then reboot and see if it works, if not, lets see what it says after that

---

### Post by Markybhoy on 2007-06-06
Wonder if its the same issue as I had with the 8800 card, could try this guide -

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by logos34 on 2007-06-06
I had the same problem installing nvidia-glx on feisty...nvidia-glx-config screwed up my xorg file and got the resulting x server error (gray screen of death is what I call it)...I then copied everything below 'modules' section on xorg file from my working edgy installation over to feisty and it booted up no prob.

Have you thought about using the 9755 driver (or maybe the 9746) straight from nvidia?  Just make sure you have build-essential pkg installed.  You'll have to do 'sh NVIDIA-Linux-x86--blah blah blah-pkg1.run' it from the cli (init 1).

---

### Post by kasperbs on 2007-06-09
Hi,
And thanks for all your replies. I have tried some of your ideas with no luck and same result.

> Wonder if its the same issue as I had with the 8800 card, could try this guide -

[http://www.ubuntugeek.com/how-to-fix...acy-users.html](http://www.ubuntugeek.com/how-to-fix...acy-users.html)
I tried this first got the message in the installer that my card was supported by the NVIDIA 1.0-96xx Legacy Linux Driver, I tried downloading that and ran the installer but with the same result as I got in the first place.

I then tried Nythain's suggestion
> type
sudo dpkg-reconfigure xserver-xorg
answer the questions to the best of your knowledge, defaults are ok on some of them, make sure to select the nvidia driver...
then reboot and see if it works, if not, lets see what it says after that

Again same result I got the error message!

have you got any idea of what I could try next, and logos34, could you elaborate on your suggestion, so that it's a bit more detailed. I'm not entirely sure what to do as I havent had edgy installed before!

Thanks

---

### Post by logos34 on 2007-06-09
> have you got any idea of what I could try next, and logos34, could you elaborate on your suggestion, so that it's a bit more detailed. I'm not entirely sure what to do as I havent had edgy installed before!

That is to say, use the official driver from nvidia website versus the binary glx in the repos.

There's actually a bleeding edge release that just came out that covers the geforce 7 series--
**[NVIDIA-Linux-x86-100.14.09-pkg1.run]("http://www.nvidia.com/object/linux_display_ia32_100.14.09.html")**.   Or you could use the [9755]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html") (although its listed only for the GeForce Go 7900 laptop series).  You could try that. For my 6.10 edgy installation I had to reinstall the graphics driver after a kernel update (to 2.6.17-11), but since I was never able to get the binary driver (8776 nvidia-glx) back in and X configured correctly I just downloaded and installed the official 9746 from the nvidia archive and everything works perfectly now.  

Read the [Latest NVIDIA Feisty]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html") step-by-step (i.e. Method 2).  But to tell the truth I didn't uninstall any of the glx stuff or specify kernel paths, etc, I even went through the interactive installation in recovery mode (~init 1)--not recommendeed by nvidia--and no problems whatsoever.

---

### Post by johnc4510 on 2007-06-09
kasperbs, can you select to show the output of the xserver output and post the results here please. They usually show where the problem is in the xserv-conf file.

---

### Post by logos34 on 2007-06-09
Or try Envy to automatically download and install the driver for you.  (haven't tried it yet)

**[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)**

---

### Post by Crafty Kisses on 2007-06-09
> **logos34 said:**
> Or try Envy to automatically download and install the driver for you.  (haven't tried it yet)

**[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)**

That didn't work all that well for me. :(

---

### Post by kasperbs on 2007-06-18
Hi again, I dont know how I can get the output in here, its a pretty long list. What I have managed to do was to install it again, and then I got that error message but I could then use nano to change the driver section of my xorg.conf file so it said nv instead of nvidia, and that was enough to let me startx. here is how my xorg.conf file looks like after installing the nvidia drivers.

remember it would ofcourse say nvidia instead of nv in the driver section.

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Option		"XkbLayout"	"dk"
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
	Identifier	"nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Driver		"nv"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"MD1998LK"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Monitor		"MD1998LK"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
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

Can anyone read anything out of that. This time I tried to install the driver the recommended way, by using [this tutorial]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") (using the feisty method), but it didnt seem to make a difference. still the same error messages

---

### Post by reset3x on 2007-06-18
If this is a fresh install of Ubuntu and you have no personal data that you need I would reinstall Ubuntu and install the nVidia drivers with Envy... I've been through the same thing as you quite a few times and this is how I go about it now.... Throw your  7950 back in and... Reinstall Ubuntu and do the Envy thing.... I have my two 7900 GT KO's running in SLi and had no problem with this method.... 

Good Luck!!!

---

### Post by timzak on 2007-06-18
Try this method:

[http://ubuntuforums.org/showpost.php?p=2837161&postcount=3](http://ubuntuforums.org/showpost.php?p=2837161&postcount=3)

Very important:  replace `uname -r` at the end of the last line of code with your kernel.  So if you're using the latest kernel, that last line would read:
```
linux-restricted-modules-2.6.20-16-generic
```

I would've posted the code directly here but I wanted to give credit to Cappy who helped me install the drivers.    The nvidia-glx-new drivers that the code above installs are the 9755 drivers.  They work fine on my 6800GS AGP.

I think the key part of this whole thing is not forgetting to also install the nvidia kernel module.

I'm a newb, so if I'm wrong, someone please chime in.

---

### Post by kasperbs on 2007-06-18
Woow I'm stunned seriuosly. I have been trying to fix this issue for nearly 1½month. And this was all that was needed. What I did was:

Running this as you suggested, just changed it to the legacy driver:
> sudo apt-get --purge remove nvidia-glx nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-legacy linux-restricted-modules-2.6.20-16-generic

And then I changed the xorg.conf so that it read nvidia in the driver section instead of nv. You should feel good today, you have made a Linux user very happy today. :)

Thanks timzak and Cappy

---

### Post by potnoodles on 2007-06-18
have a look at this also
[http://ubuntuforums.org/showthread.php?p=2869639#post2869639](http://ubuntuforums.org/showthread.php?p=2869639#post2869639)

regards.
potnoodles

---

### Post by timzak on 2007-06-18
I'm glad it worked for you!  I love it when that happens.

Take care.

---

### Post by BoredOutOfMyMind on 2007-06-24
> **timzak said:**
> I'm glad it worked for you!  I love it when that happens.

Take care.

Any suggestions for Kubuntu user now with Black Screen.....

reconfig -phigh... and then kde loading desktop...blue screen


:D

---

### Post by Vodkayum on 2007-06-24
Still new here but want to help.

If using ubuntu use envy like someone else posted

If using kubuntu use automatix
[http://www.getautomatix.com/](http://www.getautomatix.com/)

It will do it for you.

I had a hell of a time getting nvdia to work on kubuntu before gn2 pointed me at this app, good luck.

---

