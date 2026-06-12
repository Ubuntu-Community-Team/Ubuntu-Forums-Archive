---
title: "[SOLVED] Widescreen Resolutions and Xubuntu"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-05-25
I have Xubuntu feisty running on my just put together desktop.  My graphics card is a p.o.s. Intel GMA 945G which is supposed to support widescreen resolutions up to 2048x1536 at 75 Hz maximum resolution according to intel.

Now I have set up my xorg.conf file to handle resolutions up to 1440x900 because my monitor (Samsung SyncMaster 941BW) can only handle up to that.

It seems like all of my images are being stretched due to the incorrect resolution.  How can i fix this?

In the display menu my choices are:
Default -- selected
1024x768
800x600
640x800

Any guidance is appreciated.

---

### Post by lsalminen on 2007-05-25
I have the same problem...

---

### Post by icechen1 on 2007-05-25
Install 915resolution can fix the problem(at least for me)
sudo apt-get install 915resolution
If not,do a search on the forum about 915resolution.

---

### Post by kernel tom on 2007-05-25
> **icechen1 said:**
> Install 915resolution can fix the problem(at least for me)
sudo apt-get install 915resolution
If not,do a search on the forum about 915resolution.
I did that and then ran 

# 915resolution -l

getting an output of

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


and none of those are widescreen resolutions...

any more ideas?

---

### Post by ramjet_1953 on 2007-05-25
If you are using Feisty 7.04, you are much better off using the new Intel driver.

Copy and paste this command into a terminal:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

When it has finished its' thing just re-boot and all should be sweet.

Then have a look in [COLOR="Blue"]System>Preferences>Screen Resolution[/COLOR] to see all of the new options.

Regards,
Roger  :cool:

---

### Post by kernel tom on 2007-05-25
what exactly do i do after it installs?

I rebooted, and got no changes
then reconfigured xorg, and still no changes

is there something i am missing here?

---

### Post by ramjet_1953 on 2007-05-25
Did you have a look in [COLOR="Blue"]System>Preferences>Screen Resolution[/COLOR] ?

Regards,
Roger :cool:

---

### Post by kernel tom on 2007-05-26
I'm using xubuntu, and there is no System>Preferences menu option, unless this installation should have created one.

The only place I can adjust the resolution is
Settings>Display Settings
and nothing has changed there with new options or the like.

Do you know where to access this newly installed package in xubuntu? Can I get there from the terminal?

---

### Post by kernel tom on 2007-05-26
Ok i figured it out

after installing 
sudo apt-get install xserver-xorg-video-intel

open up ur xorg,conf file and change your Device>Driver from whatever it is to "intel"
don't rename your card though.

Then reboot, it should work fine... I renamed my card to "Intel 945G" and my xserver messed the bed, but after changing it to "Generic Video Card" it was fine.

---

### Post by veloce on 2007-05-26
> **kernel tom said:**
> Ok i figured it out

after installing 
sudo apt-get install xserver-xorg-video-intel

open up ur xorg,conf file and change your Device>Driver from whatever it is to "intel"
don't rename your card though.

Then reboot, it should work fine... I renamed my card to "Intel 945G" and my xserver messed the bed, but after changing it to "Generic Video Card" it was fine.

The card identifier is used in the "server layout" section - you would just need to change it there as well as in the "device" section.

Is 3d acceleration working for you?  Some people have had trouble with the intel driver.

---

### Post by kernel tom on 2007-05-27
It is now

When my x-server crashed because of the name of my video card, it was because I manually changed only that one line in the xorg.conf file.  If you do it through the set up manager in the terminal, "intel" should be a driver option, and after typing in "Intel GMA 945G" for the card name, everything works smoothly.


Side Note:
Doing this can cause you to loose video display in all of your media players, so go into the advanced options wherever video output is and change it to the following for each player...

VLC: X11
Xine: xshm
Totem: X Window (no vc) <-- I believe that's correct

Hopefully all of this helps

---

### Post by Ozeuss on 2007-05-27
when changing video drivers, it is sometimes preferable to run "sudo dpkg-reconfigure xserver-xorg". that help you create a new xorg file (you still have the old one, very useful to run diff to make sure nothing was lost)

---

