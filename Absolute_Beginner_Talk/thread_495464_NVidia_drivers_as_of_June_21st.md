---
title: "NVidia drivers as of June 21st"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by MementoMori on 2007-07-08
I've been meaning to ask how safe it is to install the latest NVidia drivers in Ubuntu. I'm currently toting a GeForce 8600 in my system, but have been warned by a friend of mine that an erroneous install caused his Linux partition to be renered unusable except for a command line.

NVidia does recommend they be installed outside the X window system, but is it Ubuntu-safe to do this as far as anyone knows?

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

This page has a readme.

---

### Post by bodhi.zazen on 2007-07-08
I have been running that driver for some time without problems.

---

### Post by MementoMori on 2007-07-08
Totally off topic, but I have your icon on my wall! :D

Anyway. Did you do anything special to install it or did you just download and ./configure?

---

### Post by bodhi.zazen on 2007-07-08
Well, you have to install some headers first.

Then I installed with ```
sudo sh ./Nvidia*.run
```

As a part of that script allow the script to confgure X ;)

Here is a how to :

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```

Note you may want to cut and paste that command. those are single tics ` (located by the number 1 key) and not single quotes '

then ```
sudo sh ./NVIDIA*.run
```

Off Topic : Very cool wall/avatar ;)

---

### Post by abhijitkarmokar on 2007-07-08
> **MementoMori said:**
> I've been meaning to ask how safe it is to install the latest NVidia drivers in Ubuntu. I'm currently toting a GeForce 8600 in my system, but have been warned by a friend of mine that an erroneous install caused his Linux partition to be renered unusable except for a command line.

NVidia does recommend they be installed outside the X window system, but is it Ubuntu-safe to do this as far as anyone knows?

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

This page has a readme.

On a related note probably this thread might help. I used the Envy Utility / script and it worked a like a charm for me !! I am a complete newbie so did not go the compiling the driver means !!!

[http://ubuntuforums.org/showthread.php?t=432056&highlight=Howto%3A+Latest+Nvidia+Drivers](http://ubuntuforums.org/showthread.php?t=432056&highlight=Howto%3A+Latest+Nvidia+Drivers)

Let me know if this works !!

Here are my specs

DELL E510
Intel Dual core 3.20 GHz
2 GB RAM
Nvidia XFX GeForce 8500GT 450Mhz 256MB PCI Express x16 Video Card
Dual boot with Vista and Ubuntu Feisty 7.04
Beryl works like a charm on my machine too !!

Abhijit

---

### Post by abhijitkarmokar on 2007-07-08
> **MementoMori said:**
> *****, but have been warned by a friend of mine that an erroneous install caused his Linux partition to be renered unusable except for a command line.


It is not true that your desktop is rendered unusuable ..take a backup of xorg.conf file before installing your drivers. if things go bad ... simply restore your old xorg.conf file over the existing one and u will be back to normal .. you can then uninstall your Nvidia driver and start the process again !!

Let me know if you need more help !!

Abhijit

---

### Post by bodhi.zazen on 2007-07-08
> **abhijitkarmokar said:**
> On a related note probably this thread might help. I used the Envy Utility / script and it worked a like a charm for me !! I am a complete newbie so did not go the compiling the driver means !!!

[http://ubuntuforums.org/showthread.php?t=432056&highlight=Howto%3A+Latest+Nvidia+Drivers](http://ubuntuforums.org/showthread.php?t=432056&highlight=Howto%3A+Latest+Nvidia+Drivers)

Let me know if this works !!

Here are my specs

DELL E510
Intel Dual core 3.20 GHz
2 GB RAM
Nvidia XFX GeForce 8500GT 450Mhz 256MB PCI Express x16 Video Card
Dual boot with Vista and Ubuntu Feisty 7.04
Beryl works like a charm on my machine too !!

Abhijit

The envy script is great,  but it does not install the latest nvidia driver.

---

### Post by MementoMori on 2007-07-09
Okay, I did what you said in addition to a walkthrough on the Linux forums at nVidia. The drivers seem to have installed okay, but my card was detected as an "nVidia default" or somesuch in my xorg.conf file. This suggests a generic driver being used. Should I be seeing my card detected specifically?

---

### Post by bodhi.zazen on 2007-07-09
> **MementoMori said:**
> Okay, I did what you said in addition to a walkthrough on the Linux forums at nVidia. The drivers seem to have installed okay, but my card was detected as an "nVidia default" or somesuch in my xorg.conf file. This suggests a generic driver being used. Should I be seeing my card detected specifically?

If the driver is working, no worries.

If you like post the relevant section from /etc/xorg.conf and we will take a look.

---

### Post by MementoMori on 2007-07-09
Well, when I restarted, my system handed me a line about the module "nvidia" not being found, so it sent me straight to a command prompt. Gah.

I tried going to the xorg and changing the line to "nVidia", since I've learned that the system is case-sensitive, but it didn't work. I see that there's a xorg.conf.backup, but I'm not sure how to go back to it and try to fix the problem. Is there a simple way to fix this?

As to your request, it brought up the display and monitor as "nVidia Default Card".

---

### Post by bodhi.zazen on 2007-07-09
The driver line should read "nvidia"

To restore you can either :

sudo cp /ect/X11/xorg.conf.backup /etc/X11/xorg.conf[/code]

Or 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or use the vesa driver, change the driver line form "nVidia" to "vesa"

to fix your problem, re-install the nvidia driver ...

---

### Post by MementoMori on 2007-07-09
Well, the driver line -did- read "nvidia" the first time I restarted, but it told me it couldn't find it and I got dumped to a command line.

After installing the driver, what all should I check? The xorg for the driver and anything else?

---

### Post by bodhi.zazen on 2007-07-09
No. You just install the nvidia driver, durring the install let the nvidia driver configure X

Then start x

```
sudo /etc/init.d/gdm start
```

If you get an error message either 

modprobe nvidia

or reboot

Then to configure you settings, use nvidia-settings

open a terminal ```
gksu nvidia-settings
```

If you like what you see, choose save settings ;)

---

### Post by MementoMori on 2007-07-09
*head hit keyboard*

Okay. After that fiasco I was left with a generic video card input using an nvidia driver for some reason. Reinstalling everything seems to work fine, up until I reboot or go into console mode. 

On restart, I get an API mismatch error that sings the tune of it having version 100.14.11 but the nVidia kernel module's version doesn't match. Then I get dumped to a command line and have to start all over again with the reconfiguring and reinstalling.

When going to a command line after the install, it tells me that it can't init the following for some reason:

/usr/X11R6/lib/X11/fonts/misc
/usr/share/fonts/X11/cyrillic
/usr/X11R6/lib/X11/fonts/Type1

and then it does nothing but flash a cursor at me.

I'm sorry if I'm dumping on ya...

Edit: Minor correction.

---

### Post by MementoMori on 2007-07-09
Okay. I did some searching on my system and found the reason it's not initing those modules is because thems modules isn't there. Sigh. But I did find a misc and a Type1 in my usr/share/fonts/x11 directory. Just no cyrillic. Why, I don't know. Anyway, I looked in my xorg and can't see where it's calling for those fonts to make it crash this way.

(Yeah, I realize this is getting dangerously close to getting off topic, but the system is looking for them ever since I installed the drivers and not finding them at the specified directories.)

---

### Post by MementoMori on 2007-07-10
Meh. Well, no matter what I seem to do, I'm having to reinstall the drivers every time I restart Ubuntu because the kernel it compiles at setup doesn't match versions. I don't know why.

I think I'll pose this to the nVidia board. Apparently this isn't normal.

---

### Post by abhijitkarmokar on 2007-07-10
> **MementoMori said:**
> Meh. Well, no matter what I seem to do, I'm having to reinstall the drivers every time I restart Ubuntu because the kernel it compiles at setup doesn't match versions. I don't know why.

I think I'll pose this to the nVidia board. Apparently this isn't normal.

Hey ... I would like to know how did u install the drivers. My xorg.cong file also says Generic nvidia driver .. however it works simply perfect for me !! as said before i had used the envy tool to install the driver ... 
I am at work right now ... Ill go home and copy the part of my xorg.conf file showing the nvidia driver version !!

Abhijit

---

### Post by MementoMori on 2007-07-10
Well, I installed the headers as bodhi posted earlier on, and then followed this walkthrough:

[http://www.nvnews.net/vbulletin/showthread.php?t=94072](http://www.nvnews.net/vbulletin/showthread.php?t=94072)

---

### Post by stchman on 2007-07-10
> **MementoMori said:**
> I've been meaning to ask how safe it is to install the latest NVidia drivers in Ubuntu. I'm currently toting a GeForce 8600 in my system, but have been warned by a friend of mine that an erroneous install caused his Linux partition to be renered unusable except for a command line.

NVidia does recommend they be installed outside the X window system, but is it Ubuntu-safe to do this as far as anyone knows?

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

This page has a readme.

You have to ask yourself the question:  "What am I going to gain by installing the latest driver?".  I recommend the Restricted Driver.

---

### Post by MementoMori on 2007-07-10
No reply from the nVidia board yet. In the meantime I think I'll try and recti-ma-fy this with Envy as suggested before.

I see you have it, Mista stchman... *downloads*

---

### Post by abhijitkarmokar on 2007-07-10
> **MementoMori said:**
> No reply from the nVidia board yet. In the meantime I think I'll try and recti-ma-fy this with Envy as suggested before.

I see you have it, Mista stchman... *downloads*

I would strongly suggest you back up your xorg.conf file. Secondly before you use Envy set up video driver to vega. 

And let Envy do the rest. 

Here is my xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by NT4usB on 2007-07-10
If the install goes pear shaped using the envy skript, run it again but choose the 'uninstall' drivers option first. 
Then the install option. 
This cleaned up a borked install for me anyway...

ed: Remember, you can usually get back to a GUI by editing your xorg and changing the driver:```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```
to```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "vesa"
EndSection
```

Think of it as kinda' like VGA mode in Windows...

---

### Post by MementoMori on 2007-07-10
> **abhijitkarmokar said:**
> I would strongly suggest you back up your xorg.conf file. Secondly before you use Envy set up video driver to vega.

Done. And is it vega or vesa? I get conflicting viewpoints on some walkthroughs.

---

### Post by MementoMori on 2007-07-10
> **NT4usB said:**
> If the install goes pear shaped using the envy skript, run it again but choose the 'uninstall' drivers option first. 
Then the install option. 
This cleaned up a borked install for me anyway...

ed: Remember, you can usually get back to a GUI by editing your xorg and changing the driver:```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```
to```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "vesa"
EndSection
```

Think of it as kinda' like VGA mode in Windows...

Well, there is a backup of my xorg generated by the nVidia install, but using it takes me to a lower resolution. It works, though. Hopefully this won't b0rk the system any more than it already is, though. *leers at his arbitrarily-working Totem*

---

### Post by abhijitkarmokar on 2007-07-10
> **MementoMori said:**
> Well, there is a backup of my xorg generated by the nVidia install, but using it takes me to a lower resolution. It works, though. Hopefully this won't b0rk the system any more than it already is, though. *leers at his arbitrarily-working Totem*

That is not a problem most probably ... you can always increase your resolution later by adding them in conf file. Yes it is vesa ... not vega :) sorry for the typo ...

Abhijit

---

### Post by MementoMori on 2007-07-10
Yeah, but with the generic driver it boots me back to, none of my toys like Beryl work. ;_;

Anyway. Envy has crashed three times with errors, and on the fourth run it presented me with what I'm hoping is a progress bar. :/

---

### Post by MementoMori on 2007-07-10
Gah.

> ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.
 this might happen because either your card is not supported by the driver or Envy's hardware
 detection failed. You can try the manual installation at your risk.

Well that bites.

---

### Post by bodhi.zazen on 2007-07-11
Well, as a few points of order ...

1. The line " Identifier     "Generic Video Card" " is a great big nothing. It is a comment. You can change it to what ever you like. BUT if you change the name , you must use the same name later in the "Screen" section where it says "Device". This has nothing to do with which driver is used.

2. The line " Driver         "nvidia" " is the driver used.

[list][*]vesa = generic driver. Use this to get back to X if you need[*]nv = open source nvidia driver. For me the open source driver works "OK", it does not do dual monitors.[*]nvidia = propitiatory nvidia driver. This is what we are trying to install.[/list]

3. If you use the open source driver you want to install "nvidia-glx-new"

```
sudo apt-get install nvidia-glx-new
```

4. If you want the nVidia driver, you need to first remove the open source drivers :

```
sudo apt-get remove --purge nvidia-glx nvidia-glx-new
sudo rm /lib/linux-restricted-modules/.nvidia.new.installed
```

5. Then install the nvidia driver. You can not do this in X.

```
sudo /etc/init.d/gdm stop
wget http://us.download.nvidia.com/XFree86/Linux-x86/100.14.06/NVIDIA-Linux-x86-100.14.06-pkg1.run
chmod a+x NVIDIA-Linux-x86-100.14.06-pkg1.run
sudo sh NVIDIA-Linux-x86-100.14.06-pkg1.run
```

*That is for the 32 bit version. for the 64 bit version use :

wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.06/NVIDIA-Linux-x86_64-100.14.06-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.06/NVIDIA-Linux-x86_64-100.14.06-pkg2.run)

* I always go for the latest driver as I have a newer nvidia card as well. I have never had a problem with any nvidia beta driver.

As the nvidia driver installs, allow it to configure X.

6. Either reboot or ```
sudo modprobe nvidia
```

7. Start X :```
sudo /etc/init.d/gdm start
```

viola

8. Use ```
gksudo nvidia-settings
``` to set your monitor resolution or set up dual monitors if needed.

9. Post any error messages.

---

### Post by MementoMori on 2007-07-11
Before I begin, I need to ask if it's the .06 or the .11 (the newest) that I need to be getting?

Edit: Or, uh, does it matter?

---

### Post by bodhi.zazen on 2007-07-11
Those links I gave were from the nvidia site and are the beta drivers.

Personally I do not think it matters a great deal which version you go with.

---

### Post by MementoMori on 2007-07-11
Okay. The latest is NVIDIA-Linux-x86-100.14.11-pkg1.run, which I have a copy of right now. I'm gonna assume you want me to go from scratch and re-download, which will take some time as I'm on dial-up and it's a lot slower in Linux because my modem is a Conexant.  Unless it's kosher to give you a run-through with the installer I have?

I can go ahead and tell you this much: I didn't have the open-source nvidia drivers. ^^; So when I did the uninstall thing, it returned the no such file or directory line.

I'm running the 32-bit version.

---

### Post by bodhi.zazen on 2007-07-11
Just checking because if you had the drivers you would have problems.

Install away ;)

---

### Post by MementoMori on 2007-07-11
Well, I expected to be handed the same line about there being no screens found. Unfortunately, with just a routine install I seem to have achieved an unprecedented level of failage. It has rendered my X server completely disabled and will not let me back into a desktop even if I reset the xorg. I am only able to go into recovery mode. The x server output doesn't return any error messages except for the directory "/usr/share/fonts/X11/cyrillic" not being found.

This has never happened before but it certainly is disastrous.

Edit: Of course all this had to happen last night when the server was down.

---

### Post by MementoMori on 2007-07-11
I tried resetting my disabled modules in the restricted modules file, but it didn't fix anything; Ubuntu still won't load except for in recovery mode.

---

### Post by bodhi.zazen on 2007-07-11
reboot

---

### Post by MementoMori on 2007-07-11
I tried, many times. All I get is a blank screen, and tossed to a screen that tells me the X failed to load. Viewing the output doesn't tell me anything except that it can't find the cyrillic font. After exiting that, all I get is a flashing cursor.

Edit: Here is what happens. I will see ubuntu's progress bar fill, then the screen will go blank. Hitting enter will let me view the X output. Only when looking at the detailed output do I see the error about the cyrillic font, which probably has nothing to do with anything. Then it will tell me, "The X server is disabled. Please reload GDE when it is properly configured" or something to that effect. Then I get sent to flashy cursor land.

---

### Post by MementoMori on 2007-07-12
Well, I seem to have gotten things temporarily workable. 

I went into recovery mode, removed everything from the restricted modules file, reset the drivers and modules in the xorg back to "vesa" and "dri" (as opposed to nvidia and glx), and commented out the entry to look for a cyrillic font. That let me back into GNOME. Then, after a restart, it gave me a "no screens found" error as well as pointing to three missing modules and saying that at least one "Drivers" section should be in the xorg.

Sigh. So I reinstalled the nvidia drivers, and have grabbed another nvidia-bug-report.log. I can't find any blatant error messages in it, but that doesn't mean squat.

The heart of the matter is, whenever I restart with them, the kernel version doesn't match the driver version and so it is halting everything. I'm going out on a limb here and saying this is because my card, a GeForce 8600 GT, is expecting something a bit higher-end than what's already in the restricted drivers for Ubuntu. (I dunno where to find them.) 

I think I'll post at nVidia again in the meantime. Thanks for the patience, everyone... of course, your insight will still be welcome as I'm probably not done with this yet.

---

### Post by abhijitkarmokar on 2007-07-12
Well ... sorry for the off-on help I have managed ... 
I am pretty sure you have been here ... but just wanted to confirm 

```

Linux Display Driver - x86

Version: 100.14.09
Operating System: Linux x86
Release Date: June 8, 2007

Release Highlights

    * Adds support for new GPUs:
          o GeForce 8600 GTS
          o GeForce 8600 GT
          o GeForce 8600M GT
          o GeForce 8600M GS
          o GeForce 8500 GT
          o GeForce 8400 GS
          o GeForce 8400M GT
          o GeForce 8400M GS
          o GeForce 8400M G
          o GeForce 8300 GS
          o Quadro FX 1600M
          o Quadro FX 570M
          o Quadro FX 360M
          o Quadro NVS 320M
          o Quadro NVS 140M
          o Quadro NVS 135M
          o Quadro NVS 130M
    * Adds support for Quadro FX 4600 G-Sync and Quadro FX 5600 G-Sync boards.
    * Improved notebook GPU support.
    * Improved RenderAccel support for subpixel antialiased fonts.
    * Added XV brightness and contrast controls for GeForce 8 GPUs.
    * Improved interaction with newer Linux kernels.
    * Fixed a locale-interaction issue in the nvidia-settings configuration file parser.

```

[ http://www.nvidia.com/object/linux_display_ia32_100.14.09.html ]( http://www.nvidia.com/object/linux_display_ia32_100.14.09.html )

So by this i get .14 is the latest version which has support for your card ..

Just an FYI ... i think the penultimate solution would be compiling the driver the hard way !! However I would like to point out that ... when you follow the stps on the Nvidia web site you will find that it does not have a precompiled version of the Kernel (.20) in my case ... and being a terrible newbie that I am .. I did not venture into compiling the driver. ENVY worked for me .. Sorry to know it didnt for you ... 

Please let me know if you would need help with compiling the driver ... I would try to give it my best shot !!


Abhijit

---

### Post by abhijitkarmokar on 2007-07-12
Just curious ... probably bodhi.zazen would be able answer this question ... does having AMD CPU have anything to do with this ?? It may be a stupid doubt .. but I would like to know !!

Abhijit

---

### Post by bodhi.zazen on 2007-07-12
> **abhijitkarmokar said:**
> Just curious ... probably bodhi.zazen would be able answer this question ... does having AMD CPU have anything to do with this ?? It may be a stupid doubt .. but I would like to know !!

Abhijit

Only if it is a 64 bit , in which case download the nvidia 64 bit driver :

[http://www.nvidia.com/object/linux_display_amd64_100.14.06.html](http://www.nvidia.com/object/linux_display_amd64_100.14.06.html)

---

### Post by rybu on 2007-09-08
> **bodhi.zazen said:**
> Well, as a few points of order ...

9. Post any error messages.

Wow, bodhi.zazen, your post was bang-on.  I've been trying to figure out how to get the NVidia drivers working on Ubuntu 7.10 for a few days now.  Your post is the first to relaly explain the process clearly.  I have the nvidia drivers with direct rendering working now.  

The only problem I have is that some programs that use direct rendering crash the X server.  As of this posting, I'm totally up to date on the latest Ubuntu 7.10 updates.  glxgears crashes, but many of the DRI screensavers work fine, like the regular 4d polytopes works fine, but polyhedra crashes...  Curious.  

Does anyone have an idea of whether or not this is a problem with the drivers or one of the components of Ubuntu 7.10?

---

### Post by javeer on 2007-09-20
> **MementoMori said:**
> *head hit keyboard*

Okay. After that fiasco I was left with a generic video card input using an nvidia driver for some reason. Reinstalling everything seems to work fine, up until I reboot or go into console mode. 

On restart, I get an API mismatch error that sings the tune of it having version 100.14.11 but the nVidia kernel module's version doesn't match. Then I get dumped to a command line and have to start all over again with the reconfiguring and reinstalling.

When going to a command line after the install, it tells me that it can't init the following for some reason:

/usr/X11R6/lib/X11/fonts/misc
/usr/share/fonts/X11/cyrillic
/usr/X11R6/lib/X11/fonts/Type1

and then it does nothing but flash a cursor at me.

I'm sorry if I'm dumping on ya...

Edit: Minor correction.

Hi, MementoMori, i have the exactly same problem as you. My video card is XFX Geforce 8600GTS, i installed driver 100.14.11. it works fine first time, but when i reboot, i met the same problem as you descript above.Even i reinstall driver it still no work.

Did you fix the problem now? could you give me some help?

---

