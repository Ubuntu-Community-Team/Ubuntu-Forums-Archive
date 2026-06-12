---
title: "G5 with ATI 9600 XT not possible to set..."
date: 2007-05-30
forum: Apple PPC Users
---

### Post by carontis on 2007-05-30
Hellò. We tried in many ways to configure the ATI video card but it looks as the G5 wan't work with Ubuntu 7.04.
We have Ubuntu on the first partition on 2nd hard disk; everything is fine till it stops the loading and shows the error 7 and asks for the terminal. In the terminal using lspci it shows the ATI correctly, but with a different value than the one asked with dpkg reconfigure xserver-xorg. How can I be sure these parameters are correct?

> 0000:210:10.0 VGA compatible controller: ATI Technologies Inc Radeon [Radeon XT 9600]

---

### Post by tgalati4 on 2007-05-30
I know that the ATI Mobility Radeon 9600 works under Dapper on a Powerbook G4.  Is it simply a resolution/display issue?  What is the monitor that you are driving?  It's possible that the xserver is using a default low resolution and your display can't deal with it.

Try a Dapper Live CD and see if the graphics card/display combo works then write down the settings for use in Feisty.  Also, print out xorg.conf for reference.

---

### Post by carontis on 2007-05-30
We are using an Alternate PPC 7.04 and I had a lot to do for configuring yaboot. At end it started to load everything, but when it arrives to the login it shows the data with errors and works only in temrinal. I tried to everything, but it looks really as it wan't see the graphic card...

With the live cd it sees a U3 (Unknown) card and everything works; with the installed system it sees the card correctly but it can't start gdm and there is not possible way to understand why... also after configuring many times the server and fixed all parameetrs in yaboot.conf

Monitor is seen correctly too (Apple Studio 17") with correct VertSync and HorSync. So why the server wan't work?

---

### Post by stmiller on 2007-05-30
Hi Carontis:

Does the machine boot completely? And then X doesn't start? Or are you saying that the kernel doesn't even properly boot?

You'll have to edit the file /etc/X11/xorg.conf

Login at a terminal and type

sudo nano /etc/X11/xorg.conf

and in the Device section look for 

Driver  "ati"

and

Option "UseFBDev" "false"


Or you may have to rather specify UseFBDev to "true" if that doesn't work.

---

### Post by carontis on 2007-05-30
yeah. X doesn't want to start. I checked for the ati xserrver and it say it doesn't exixsts, but in Synaptci is reported...

In the xorg.conf it's already as you wrote and I tried also those 2 ways (true and false), but ... nothing!
I don't have here tha Mac, and I will be using it sunday, so I'll try other ways, but I'm really sick. For 3 weeks we are searching the way for making it works, and reformated the disk 4 times...
Also > Driver "ati" is already there. 

Only before the login it goes to terminal showing the error n 7 (radeon.so). I don't really know what to do again, but I'll try something

---

### Post by tgalati4 on 2007-05-31
What is the native resolution of the 17" Studio Display?  Do you have that resolution specifically called out in xorg.conf?

You might need to add it in the 24-bit mode line.  Also what happens when you run:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by carontis on 2007-05-31
Well, I haven't yet tried to launch the entire command dpkg-reconfigure -phigh xserver-xorg but simply the usual dpkg-reconfigure xserver-xorg and it shows all correct parameters. I'll try also in that way, but I'm afraid there is something that doesn't works as it should.

But: if during boot it shows correctly the Ubuntu's logo and loads the bar, why after a while iit turns out in terminal? It could be done to a change of frequency, but it should report it...( thing that doesn't happens). After checked all log files it doesn't say has a too high frequency, so I can't understand...

---

### Post by tgalati4 on 2007-05-31
I experienced a similar problem with Dapper Alternate PPC on a Clamshell G3.  I got the Ubuntu logo but the gnome display manager (gdm) would not work.  I was screwing around, waiting for Mac OS X disks to arrive to perform a final install.


In a terminal report the results of the following:

gnome-wm &
gnome-panel &

---

### Post by carontis on 2007-06-01
I'll post it on sunday, 'cause it's not my pc and it's not here, so only in that day I'll be able to try and see if it works (hope so). As my friend is a newbie I have to install all for him and after I'll explain how to use Ubuntu... but before all I have to install it.

---

### Post by tgalati4 on 2007-06-01
In a terminal:

xcalc &

If a calculator pops up then you are running the X server, it's the window manager that's not running.

gnome-wm & 

will start the window manager.  This allows you to drag windows around and close them.

gnome-panel &

will start the display manager which are the application bars and docks.  I was getting errors on an iBook clamshell, but you don't need it, you can still run any program, you just have to know the name of the program.  Try a different window manager--there are several.

Good luck.

---

### Post by kudzugarden on 2007-06-07
i have a related problem:

im running (only) kubuntu 6.06 on a blue/white g3 with a 17" sony monitor. everything used to work fine until i plugged the monitor into a windows machine (which i couldnt make work). when i reattached the monitor to the g3 and booted it, suddenly everything is much larger, even the yaboot prompt. when x starts, the monitor only displays 1/4 of the screen. moving the cursor to the edges scrolls across the giant desktop. 

does anyone know how to correct this? i checked "man yaboot" and "man yaboot.conf" to see if there are parameters to enter to change the display settings (like with grub), but i couldnt find any. is this a problem with yaboot or with xorg.conf or something else altogether?

xorg.conf has this to say:
```
Section "Device"
  identifier "ATI Technologies, Inc. Rage 128 PF/PRO AGP 4x TMDS"
  boardname "ati"
  busid "PCI:0:16:0"
  driver "ati"
  screen 0
  option "MergedFB" "off"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  gamma 0.5 0.7 0.9
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. Rage 128 PF/PRO AGP 4x TMDS"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1280 854
    modes "1024x768@60" "1152x768@54" "800x600@60" "1280x854" "800x600@56" "640x480@60"
  EndSubSection
EndSection
```

thanks!

---

### Post by kudzugarden on 2007-06-07
actually it was an xorg.conf problem. something about a "vitual" screen size. i replaced it with the backup file. no idea why that happened though.

should i enter the command at the beginning of the file to allow for automatic updates? im guessing that's what caused the problem. or does it matter?

---

### Post by tcrroadie on 2007-06-07
Carontis,

You are seeing a working Ubuntu splash screen because the system is configured to use the framebuffer capabilities of your video card during initial boot.  A different display driver is used during boot, hence the fact that you see the Ubuntu boot splash, but not the Gnome log-in manager.  

Before we try to get you a working xserver display, make a copy of your Xorg.log file that is generated when you try booting to Gnome using the ati driver.  Please post this file. The Xorg.log file will contain information that will tell us why it is failing.  After X fails to start and you are dropped to the command line run

```
cp /var/log/Xorg.0.log Xorg.0.log 
```

There is also another file called .xsession-errors that will give us some information.  It is a hidden file located in your home directory.  Again in your home directory run this command and post your xsession-errors file.
```

cp .xsession-errors xsession-errors
```

Lets see if you can get a working xserver using the fbdev graphics driver.  Change the display driver used in your xorg.conf file from "ati" to "fbdev" and make sure the option "UseFBDev" is set to "true".  That should at least get GDM and Gnome up for you. 

```
Driver   "fbdev"
Option   "UseFBDev" "true"
```

You may also want to try setting the display driver used to "radeon".  The driver "ati" is written to detect the graphics card used in your system and set the correct driver for that card.  For example, when the xserver starts up the ati module "ati", and the ati driver detects a radeon graphics card in the system, it will automatically start the "radeon" driver module for that card.  It is possible in your case that the ati driver is not setting the correct driver.  

Try changing your driver from "ati to "radeon".

```
Driver    "radeon"
```

---

