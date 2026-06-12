---
title: "help with xserver fails to start"
date: 2007-07-27
forum: Apple PPC Users
---

### Post by gvigorus on 2007-07-27
Just installed Feisty Fawn (chose Xubuntu) last night on Powerbook G3 Lombard.
At boot time the boot process stops at the point:
Local boot scripts (/etc/rc.local)
then it goes to blue screen and says the following:
"Failed to start the  X Server (Your Graphical Interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the proble? Yes No"
I click Yes and another blue screen shows a bunch of weird characters with Yes at the bottom. I hit enter and get "The X Server is now disabled. Restart GDM when it is configured correctly".

What I've tried so far:
------------------------------------------------------------
sudo dpkg-reconfigure xserver-xorg
i get "xserver-xorg is broken or not fully installed"
------------------------------------------------------------
sudo apt-get install xubuntu-desktop
i get "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"
-----------------------------------------------------------------------------------------------------------------------
commands like sudo apt-get remove x-window-system-core or sudo aptitude update also get "E:dpkg was interrupted" message as above.

My video driver is: (as per lspci | grep VGA)
00:11.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro (rev dc)

Can someone help please?! :(

---

### Post by gvigorus on 2007-07-27
So, i entered 
sudo dpkg --configure -a
and a bunch of stuff got loaded. Took maybe 15 minutes etc.
Then I had this message come up during the install process:
"E: /var/lib/defoma/locked exists Another defoma process seems running, or you aren't root.
It is possible that defoma might have aborted. PLease run defoma-configure -f to fix it's broken status"

Then once all the loadings were finished i got the following write out at the end:
"Errors were encountered while processing
ttf -lao
ttf -freefont
xfonts -scalable
ttf -gentium
xubuntu-desktop
x -tlcidform -conf
ttf -tlai -tling
xorg

Now, when I boot or startx i get black screen with cursor at top left corner. Is it fixable?! Please, help!!!

---

### Post by tonyr on 2007-07-27
To reinstall *xserver-xorg* you can try the command
```
 apt-get --reinstall install xserver-xorg
```
if you are connected to the network or have the install CD in the drive,
or you can look in /var/cache/apt/archive find the actual *xserver-xorg* .deb file
and try
```
 sudo dpkg -i /var/cache/apt/archive/<actual-package-name>
```


This post [http://ubuntuforums.org/showthread.php?t=418301]("http://ubuntuforums.org/showthread.php?t=418301")
talks about xorg/video problems with Feisty on Pismo, not Lombard, but it might be worth a shot.

I installed Feisty (Ubuntu not Xubuntu) on Pismo, which also has video problems  with the
standard install,  and added the line
```
 Modeline "1024x768" 78.741 1024 1058 1154 1312 768 769 772 800 +HSync +VSync
```
 as mentioned in that post, to */etc/X11/xorg.conf* in the Monitor section, and it worked.

The recommended way to change *xorg.conf* is from one of the virtual consoles.  After 
booting, when the Xorg failure screen pops up, or maybe when nothing pops up, try keying
CTL+ALT+F1, which should get you to a text-only console and a login prompt.  Login  to your account and enter
```
 sudo /etc/init.d/gdm stop
```
It may ask for your password.

You should see a response about stopping the display manager.  Then edit the *xorg.conf*
file as root (I use *vi*; *nano* is also good) and add the Modeline mentioned above.  Save
and quit the editor, then restart the display manager with
>  sudo /etc/init.d/gdm start
and you might see a response about starting the display manager.  At best the display
manager will start normally; at worst it will do the same thing it did before.  Good luck.

---

### Post by gvigorus on 2007-07-27
...well, now I can't get to the console. I wanted to modify the xorg.conf file. From my black screen i hit CTRL+ALT+F1 to get to the console text, but nothing happened. I tried halting GNOME from booting and at some point during boot when all the lines scroll up, if I hit enter or space, i get login prompt, but then GNOME starts booting and I get black screen again. Hitting CTRL+ALT+F1 does not work. How can I get to my console now? Can I halt the boot somehow?

---

### Post by gvigorus on 2007-07-27
okay, i've got to the console again:) at boot i entered help, then i entered to load Linux with parameter video=ofonly and everything booted, though my screen resolution is all messed up still. I'll have to troubleshoot that.

---

### Post by ajmctaggart on 2007-07-27
gvigorus, 


This is my working xorg.conf on a Powerbook Pismo, Im almost certain it'll work for you...

Here's what to do 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.screweddisplay

Then 

sudo rm -r /etc/X11/xorg.conf

Then 

sudo nano /etc/X11/xorg.conf

and Paste (Shift+Ctrl+V)

```
Below is my working Feisty PISMO xorg.conf file
HTH

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
# SubSection "Display"
# Depth 24
# Modes "1024x768" "800x600" "640x480"
# EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection
```

THAT'LL get ya going, you can edit from there as you see fit...by the way it doesn't hurt to back this one up as /etc/X11/xorg.conf.ubuntuforums 

Or whatever you wish to name it-

Good Luck, Let us know how it turns out!
ajm

---

### Post by ajmctaggart on 2007-07-27
***Take out the first two lines of my xorg.conf, or comment (#) them out...


Sorry-ajm

---

### Post by gvigorus on 2007-07-27
Thank you so much for the post! Just disovered your post. But I already got my screen work work properly with the following:

sudo dpkg-reconfigure xserver-xorg

That opened a configuration tool that walked me through asking questions about this and that, like video driver manufacturer (Lombard uses ATI 3D Rage LT Pro) with max resolution of 1024x768 and 24bith colour depth. Can't believe how small the monitor only 14 inch, but still works great now!

Thanks again. I'd never figure out how to put Linux on PPC without this forum. I'd wanted to run linux on my Lombard for 1/2 year actually, just couldn't go through with the process. I've got it all working, time to party!!!!

---

