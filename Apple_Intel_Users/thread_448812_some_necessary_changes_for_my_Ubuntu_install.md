---
title: "some necessary changes for my Ubuntu install"
date: 2007-05-19
forum: Apple Intel Users
---

### Post by l0rdn1k0n on 2007-05-19
I love Ubuntu so far, easy to use and understand but there are a few things form OS X that i miss. I'm using a MacBook, and I REALLY need wireless. Absolute necessity at this point. I can't sit here in front of my router all die hardwired in. Normally i was using a desktop PC so it wasn't an issue but now it's dual booting with my mac (rEFIt working great with OS X) and needs wireless to install all the applications I'll need.

There are a few questions I have. Many  of which have easy answers, some most likely don't. So here they are:

1) Getting my wireless card to work, I have a 1st gen MacBook (so it doesn't have the 802.11n card)

2) screen resolution to the native 1200x800 instead of 1024x768

3) installing various packages to run flash, mp3s, mp4 video 

4) possibly some compatibility with my iSight camera? (not necessary, would be nice though :))

5) hopefully this one is possible, remapping the control button to the Apple button (next to spacebar)? macs use it instead of control (ex. Apple+S for save instead of Ctrl+S) not as necessary as the first and second ones though

6) install the dock replacement (sorry linux fans, i NEED a dock)

7) ENABLE RIGHT CLICK! GOOD GOD I NEED THIS ONE!! just realized it trying to add "linux" to the dictionary. why the hell isn't linux in ubuntu's dictionary? :P (macs only have one mouse button how am i supposed to do this?!)

8) install other mac-like replacements similar to #6, including two finger scrolling or right clicking (PLEASE EXIST)

anybody else with a macbook or " pro who can add in some advice?

thanks a lot!
l0rdn1k0n

---

### Post by benanzo on 2007-05-19
I have the same MacBook as you and everything you describe works great for me.

1)  Wireless - It should work out of the box if you're using Feisty.  The revision of the madwifi drivers that ship include full support (wep, wpa, wpa2) for the wireless chip in the MacBooks.  What specific problem are you having?  Do you see any networks in NetworkManager?

2) Screen resolution - Install 915resolution to get 1280x800.  Unfortunately this is required until we get an  X server update that properly identifies the BIOS modelines to get proper resolution out of the box.

```
sudo apt-get install 915resolution
```
then reboot.

3) Playing media codecs/flash - 

Go to Applications >> Add/Remove
Click Preferences in the lower left corner.
Under the Ubuntu Software tab, make sure that the top 4 check boxes are checked. (you don't need to enable the source code repositories for this.)

It will prompt you to reload your repository information, do it.

Now in the main Add/Remove Applications window open the "Show" drop-down menu in the top right and select "All available applications"

then search for "gstreamer plugins"

put a checkbox next to:
GStreamer extra plugins
GStreamer plugins for aac, xvid, mpeg2, faad
GStreamer plugins for mms, wavpack, quicktime ...

Now search for "flashplugin"
Put a checkbox next to Macromedia Flash plugin
click apply.

5) iSight - [http://ubuntuforums.org/showthread.php?t=225621&highlight=macbook+isight](http://ubuntuforums.org/showthread.php?t=225621&highlight=macbook+isight)

6) Dock replacement - [http://awn.wetpaint.com/](http://awn.wetpaint.com/)

7) By default Ubuntu sets F12 as Right-click and F11 as middle click.  This is not very intuitive, I know.  I made a script that runs whenever I login  that sets the right Apple key to right-click and the lower enter key as delete:
```

#!/bin/bash
#
# Configures Macbook's right apple key to be right mouse-click
# and lower enter key to be delete.
# Install xkbset (sudo apt-get install xkbset).
# Copy this script to ${HOME}/bin/macbook (or wherever you keep your scripts)
# Make it executable:
# ( Right-click -> Properties - > Permissions -> "Allow executing file as Program"
# set GNOME to run it at login ( System -> Preferences -> Sessions )

xmodmap -e 'keycode 116 = Pointer_Button3'
xmodmap -e 'keycode 108 = Delete'
xkbset m

```
There are other ways to do this too.

8) advanced scrolling - You need to tinker with your /etc/X11/xorg.conf file.  You need to be sure there is a section for Input Devices that uses "synaptics" as the driver.

here's mine:
```

# Advanced configuration for the Apple MacBook Core Duo touchpad
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SHMConfig" "on"
        Option          "CorePointer"
        Option          "SendCoreEvents" "true"
        Option          "Device" "/dev/psaux"
        Option          "Protocol" "auto-dev"
        Option          "LeftEdge" "100"
        Option          "RightEdge" "1120"
        Option          "TopEdge" "50"
        Option          "BottomEdge" "310"
        Option          "FingerLow" "20"
        Option          "FingerHigh" "30"
        Option          "MaxTapTime" "150"
        Option          "MaxTapMove" "220"
        Option          "MaxDoubleTapTime" "180"
        Option          "VertScrollDelta" "25"
        #Option         "HorizScrollDelta" "30"
        Option          "VertTwoFingerScroll" "true"
        #Option         "HorizTwoFingerScroll" "true"
        #Option         "FastTaps" "true"
        Option          "TapButton2" "2"
        Option          "TapButton3" "3"
        Option          "MinSpeed" "0.79"
        Option          "MaxSpeed" "0.88"
        Option          "AccelFactor" "0.015"
EndSection

```

More info here: [http://ubuntuforums.org/showthread.php?t=397327](http://ubuntuforums.org/showthread.php?t=397327)

---

### Post by RobgBne on 2007-05-21
Regarding 915resolution, when I ran it, I got a "Couldn't find package" error.  So I first ran:

  dpkg-reconfigure xserver-xorg -phigh

to get the extra resolutions, then followed the instructions here:

  <URL: [http://www.ubuntux.org/node/25](http://www.ubuntux.org/node/25) >

to install gcc and Linux headers, then run the vmtools install.

Now I'm running Ubuntu on Mac OS X with VMWare Fusion Beta3 and life is very sweet!

-- 
Rob

---

### Post by Lovely Baby on 2007-05-21
Spam.

---

### Post by amritkaur on 2007-05-23
gtdfgdfg

---

### Post by ivesjd on 2007-05-24
I used your script on my previous install (yesterday, I broke it) and it worked. Now, it wont work. I really like having the right click and delete buttons there but Idk what happened.



UPDATE
Idk, I got it working now. Also moved some other keys around. benanzo, your posts have helped me so much. Thanks alot!

---

