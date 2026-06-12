---
title: "Worried about installing ATI drivers..."
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-30
I have noticed a lot of threads about installing ATI drivers and most of them have run into some problem. The thing is I have 2 17" TFT's and I want dual screen so I guess I have to install the ATI drivers. Which thread is the best one to follow? Is there a foolproof way?

---

### Post by rachii on 2005-06-30
deffinately check this howto out

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

good luck, if you read later on in that thread you'll learn that its good to install the drivers with x off.  so just hit ctrl+alt+F1   , then ```
sudo /etc/init.d/gdm stop
```  then copy in the commands he gives to install the drivers, then start x and you should be good!

also after the drivers are installed, make you sure configure your xorg.conf fully, or else X might crash, maybe find another howto on dual display first

---

### Post by gammyhand on 2005-06-30
[QUOTE=rachii]deffinately check this howto out

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

good luck, if you read later on in that thread you'll learn that its good to install the drivers with x off.  so just hit ctrl+alt+F1   , then ```
sudo /etc/init.d/gdm stop
```  then copy in the commands he gives to install the drivers, then start x and you should be good!

also after the drivers are installed, make you sure configure your xorg.conf fully, or else X might crash, maybe find another howto on dual display first[/QUOTE]
 Hmm...x? = graphics server? How can I copy stuff to the terminal if I am only using command line? Or have I got the wrong end of the stick. Is it possible to dual screen without the ATI drivers?

---

### Post by rachii on 2005-06-30
[QUOTE=gammyhand]Hmm...x? = graphics server? How can I copy stuff to the terminal if I am only using command line? Or have I got the wrong end of the stick. Is it possible to dual screen without the ATI drivers?[/QUOTE]

yes, x is the graphics server (gdm referring to X).  i know you can dual screen with the ATI drivers.  without them i am not sure, havent done it myself.  i think you might need the drivers to do it, not sure though?  
***what is your video card, and other system specs (makes/models)?  are you going to be playing games? or trying other graphic intensive work?***

---

### Post by gammyhand on 2005-06-30
[QUOTE=rachii]yes, x is the graphics server (gdm referring to X).  i know you can dual screen with the ATI drivers.  without them i am not sure, havent done it myself.  i think you might need the drivers to do it, not sure though?  
***what is your video card, and other system specs (makes/models)?  are you going to be playing games? or trying other graphic intensive work?***[/QUOTE]
 My graphics card is a 9800pro. rest of system is athlon64 3400+, 1gb pc3200 ram, 250gb sata disk, nec 2500a dvd-rw, 2x iiyama e431s 17" tft's @ 1280x1024.  I am not really bothered about playing games at the moment although a little light gaming never hurt anyone.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=gammyhand]I have noticed a lot of threads about installing ATI drivers and most of them have run into some problem. The thing is I have 2 17" TFT's and I want dual screen so I guess I have to install the ATI drivers. Which thread is the best one to follow? Is there a foolproof way?[/QUOTE]


This IS the easiest way:

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

It won't get you the newest drivers but you don't need um.

When you are done, use this command:

fglrxconfig

to set up dual monitors.

---

### Post by gammyhand on 2005-06-30
[QUOTE=poofyhairguy]This IS the easiest way:

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

It won't get you the newest drivers but you don't need um.

When you are done, use this command:

fglrxconfig

to set up dual monitors.[/QUOTE]
 How do I find out my kernel version?

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=gammyhand]How do I find out my kernel version?[/QUOTE]


Well...search for the word "kernel" in synaptic. See what is installed.

---

### Post by gammyhand on 2005-06-30
[QUOTE=poofyhairguy]Well...search for the word "kernel" in synaptic. See what is installed.[/QUOTE]
 linux kernel headers: 2.5.999-test7-bk-17

nvidia-kernel-common: 1.0.7174+1

which one is it? Presumably the nvidia one?

---

### Post by gammyhand on 2005-07-01
[QUOTE=gammyhand]linux kernel headers: 2.5.999-test7-bk-17

nvidia-kernel-common: 1.0.7174+1

which one is it? Presumably the nvidia one?[/QUOTE]
 I can't get it to work. It says unknown file if I try to enter what I think is my kernel name as part of the filename to run.

---

### Post by Knome_fan on 2005-07-01
Open up a terminal and type uname -a
This will give you your kernel version.

But the easiest way is probably to simply fire up synaptic and search for linux image. This will also tell you which kernel is installed.

Now search for linux restricted and simply install the corresponding linux-restricted-modules package. (and of course, as the howto mentions xorg-driver-fglrx after that.

Hope this helps.

---

### Post by gammyhand on 2005-07-01
[QUOTE=Knome_fan]Open up a terminal and type uname -a
This will give you your kernel version.

But the easiest way is probably to simply fire up synaptic and search for linux image. This will also tell you which kernel is installed.

Now search for linux restricted and simply install the corresponding linux-restricted-modules package. (and of course, as the howto mentions xorg-driver-fglrx after that.

Hope this helps.[/QUOTE]
 Cheers, will give that a go when I get back from work tonight :)

---

### Post by gammyhand on 2005-07-03
OK I think I have it configured...could someone tell me if this file is ok in principle before I restart startx?

Also - what command do I need to revert to the old file if it cocks up and only loads into the command prompt?

---

### Post by rachii on 2005-07-03
if it doesnt work and you dont want to mess wiht it anymore and just want your video back.  you can always just change your driver in your xorg.conf from "fglrx" to "ati", the default one you started with.  but before you do that, make sure you have it all configured right.  all the extra modules are loaded, you arent missing any quotes or anything.  also (i dont remember if i posted this here or not) mine would not work no matter what i did, until i put in the monitor HorizSync and VertRefresh rates

if your stuck in the command prompt and dont know how to edit the xorg.conf, just type ```
sudo nano /etc/X11/xorg.conf
```   nano being a simple to use text mode text editor (when it opens all you can just type what you want to change, and all of the commands to operate it like save and exit are all listed at the bottom of the screen.  the ^ means hold down ctrl.  so to exit you hold down "ctrl + X") that way you dont have to learn how to use a program to do it, its all right there so you dont get stuck.

---

### Post by f1dave on 2005-07-04
Hey everyone,

I've followed the howto, but fglrxinfo still states that I have mesa installed instead of the ati stuff. i've noticed similar problems in the howto from other people, but they seemed to fix it themselves at some point. Unfortunately, I haven't :(

Any ideas?

---

### Post by gammyhand on 2005-07-05
[QUOTE=f1dave]Hey everyone,

I've followed the howto, but fglrxinfo still states that I have mesa installed instead of the ati stuff. i've noticed similar problems in the howto from other people, but they seemed to fix it themselves at some point. Unfortunately, I haven't :(

Any ideas?[/QUOTE]
 I am starting to get really fed up of the ATI drivers to be honest. I NEED 3d accelaration. I have a radeon 9800pro and I am sick of watching the on screen animations (like the shut down effect) chugging. What drivers do I need to 3d accelaration? :'(

---

### Post by gammyhand on 2005-07-05
[QUOTE=gammyhand]I am starting to get really fed up of the ATI drivers to be honest. I NEED 3d accelaration. I have a radeon 9800pro and I am sick of watching the on screen animations (like the shut down effect) chugging. What drivers do I need to 3d accelaration? :'([/QUOTE]
 OK I AM really fed up now. I edited my xorg.conf as suggested in the howto and after restarting the xserver it said it could not load. So I copied back my backed up xorg.conf file and I am back where I started. What the hell are the 

...'s all about in the example of how to configure the xorg.conf?

as in:

...
mod1
mod2
...
subsection
...
end subsection

etc etc....

---

### Post by f1dave on 2005-07-06
Sorry, but I totally don't understand that post.

---

### Post by gammyhand on 2005-07-06
[QUOTE=f1dave]Sorry, but I totally don't understand that post.[/QUOTE]
 I don't know how to set up my xorg.conf file properly is the gist of it.

I don't understand the instructions given in the how to.

---

### Post by rachii on 2005-07-06
gammyhand, why dont you post your xorg.conf file, and then maybe the community can find some sort of typo, or something that has been left out.  none of this has messed up your computer in anyway, you just have to get the file configured properly.

---

### Post by gammyhand on 2005-07-06
[QUOTE=rachii]gammyhand, why dont you post your xorg.conf file, and then maybe the community can find some sort of typo, or something that has been left out.  none of this has messed up your computer in anyway, you just have to get the file configured properly.[/QUOTE]
 Last time I did that some kind soul deleted it from my post. It must have been too large a file or something.

---

### Post by gammyhand on 2005-07-06
OK...here is my new.conf...please whoever deleted it last time leave it up!

I don't know what is wrong with this.

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
  ...
  Load "GLcore"
  Load "glx"
  Load "dri"
  ...
  # Load "extmod" but omit DGA extension
  # (the DGA extension is broken in the fglrx driver)
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection
  ...
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
  Identifier "ATI"
  Driver     "fglrx" # this is the important bit

# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC"

# === Video Overlay for the Xv extension ===
  Option "VideoOverlay" "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  Option "UseInternalAGPGART" "no"
EndSection

Section "Monitor"
	Identifier	"PLE431"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"PLE431"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by poofyhairguy on 2005-07-06
OK. I got mine to work. Here is how:

[http://ubuntuforums.org/showpost.php?p=122362&postcount=6](http://ubuntuforums.org/showpost.php?p=122362&postcount=6)

Use this RPM:

[http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.14.13-1.i386.rpm](http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.14.13-1.i386.rpm)

---

### Post by gammyhand on 2005-07-06
[QUOTE=poofyhairguy]OK. I got mine to work. Here is how:

[http://ubuntuforums.org/showpost.php?p=122362&postcount=6](http://ubuntuforums.org/showpost.php?p=122362&postcount=6)

Use this RPM:

[http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.14.13-1.i386.rpm](http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.14.13-1.i386.rpm)[/QUOTE]
 
> Note: before you start check if you have installed the linux-headers for your kernel and gcc (Synaptic)

What are the packages I am looking for in synaptic? Although I am pretty sure they are on there!

Also this line:

> 7. sudo dpkg --force-overwrite -i fglrx- ... .deb
What is the .deb file name? How am I supposed to know that?

---

### Post by poofyhairguy on 2005-07-06
Good questions.

[QUOTE=gammyhand]What are the packages I am looking for in synaptic? Although I am pretty sure they are on there![/QUOTE]

I have these installed:

linux-686

linux-headers-686

thats that.

> 
What is the .deb file name? How am I supposed to know that?

Alien will tell you when its done. keep looking at the command line- it will say "_.deb made." Use that.

---

### Post by gammyhand on 2005-07-06
[QUOTE=poofyhairguy]Good questions.



I have these installed:

linux-686

linux-headers-686

thats that.



Alien will tell you when its done. keep looking at the command line- it will say "_.deb made." Use that.[/QUOTE]
 Great thanks...one last thing....what do I do apart from cry if this all goes pete tong? Can I just restore a backed up xorg.conf and all will be well?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=gammyhand]Great thanks...one last thing....what do I do apart from cry if this all goes pete tong? Can I just restore a backed up xorg.conf and all will be well?[/QUOTE]

yep. I used the xorg config the ati thing made. But back up yours in case it doesn't work.

---

### Post by gammyhand on 2005-07-06
[QUOTE=poofyhairguy]yep. I used the xorg config the ati thing made. But back up yours in case it doesn't work.[/QUOTE]
 OK I am about 70% through the instructions and I did the sudo make sh...and this is what I got:

ralph@ralph:~/downloads/drivers/ati$ sudo dpkg --force-overwrite -i fglrx-6-8-0_8.14.13-2_i386.deb
Selecting previously deselected package fglrx-6-8-0.
(Reading database ... 75169 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.14.13-2_i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
Setting up fglrx-6-8-0 (8.14.13-2) ...

ralph@ralph:~/downloads/drivers/ati$ cd /lib/modules/fglrx/build_mod
ralph@ralph:/lib/modules/fglrx/build_mod$ sudo sh make.sh
make.sh: line 46: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
ralph@ralph:/lib/modules/fglrx/build_mod$

---

### Post by gammyhand on 2005-07-06
[QUOTE=gammyhand]OK I am about 70% through the instructions and I did the sudo make sh...and this is what I got:

ralph@ralph:~/downloads/drivers/ati$ sudo dpkg --force-overwrite -i fglrx-6-8-0_8.14.13-2_i386.deb
Selecting previously deselected package fglrx-6-8-0.
(Reading database ... 75169 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.14.13-2_i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
Setting up fglrx-6-8-0 (8.14.13-2) ...

ralph@ralph:~/downloads/drivers/ati$ cd /lib/modules/fglrx/build_mod
ralph@ralph:/lib/modules/fglrx/build_mod$ sudo sh make.sh
make.sh: line 46: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
ralph@ralph:/lib/modules/fglrx/build_mod$[/QUOTE]
 I got around the GCC problem by installing GCC 5 as well as 6...but I have no idea how to solve the kernel includes error.....

My bad - I was missing linux headers (I thought I had it installed). I now have dual screen! woooo! at long last. But I don't seem to have any hardware accelaration as the fade out when you click shut down still chugs very badly...can I rectify this?

Thanks for all your help :)

---

### Post by gammyhand on 2005-07-07
[QUOTE=gammyhand]I got around the GCC problem by installing GCC 5 as well as 6...but I have no idea how to solve the kernel includes error.....

My bad - I was missing linux headers (I thought I had it installed). I now have dual screen! woooo! at long last. But I don't seem to have any hardware accelaration as the fade out when you click shut down still chugs very badly...can I rectify this?

Thanks for all your help :)[/QUOTE]
 OK my fglrx gears score is about 4xxx so obviously 3d accelaration is working. So how come when I click on "log out" it really really chugs when the screen fades out?

---

