---
title: "Trying to configure Xserver-xorg to include ATI PCI 16MB Card"
date: 2007-05-23
forum: Apple PPC Users
---

### Post by joshjani on 2007-05-23
I can't seem to get a regular-old ATI Rage128 Card to work in my Beige G3 under Ubuntu. It works just fine under OS 9.

I have tried removing the PCI card, booting to Ubuntu, and reconfiguring Xserver-xorg. Partway through that, I am asked for the PCI ID for the card. How do I know what that is so I can input it in the proper format? 

When I boot to OS 9, system profiler tells me that the card is in Slot A1. The format xserver is looking for is something like PCI 00:16:00 

So I don't know what to do here. Please help, as I cannot get resolution above 800x600 with the 2MB of onboard video RAM the Mac has. I need to use this card!

Thanks for any further info you might be able to share regarding configuring this pretty standard (I thought!) ATI card.

JC

---

### Post by rondackcpu on 2007-05-30
JC,

I have an old Blueberry G3 that I have been playing with, but I am far from an expert on things relating to ATI cards.  As X-windows is starting each time the computer is booted, there is a log file created detailing the start of X-windows.  It is located at "/var/log/xorg.O.log".  There is one backup copy kept from the last time the computer was booted.  You can examine these with a text editor like gedit.  The log file will say why each resolution option failed.  Sometimes the Horizontal and Vertical range values in "etc/X11/xorg.conf" are too narrow to allow the resolution to be accepted.

On my machine, I have played around with those Horizontal and Vertical values by editing the "etc/X11/xorg.conf" file with gedit.  In a terminal you will need to type "sudo gedit /etc/X11/xorg.conf" to get write permission to make any changes.  It would be good practice to make a backup copy of the file before you start playing, so that you can get back to square-one if something goes bad.

The values that my machine started with were Horizontal 60-60, and vertical 75-117.  Using those I got only 1024x768 resolution on the screen.  My notes say that when I changed to Horiz 50-70 and Vert 55-117, I got higher resolution, maybe 1200x900, but I judged that too small for my tired eyes.

Also, in "/etc/X11/xorg.conf" there are listings of resolutions that X-windows will try to use for each of several "depths".  I think that it's a sort of "if you don't ask, you won't get it" thing.  So check, while you are editing "xorg.conf" if any higher resolutions are asked for.  You might try adding "1024x768" and "1200x900" if they are not there.  Some posts here at the Forum have suggested changing the default depth to 16 from 24.  That didn't do anything for me.

Have fun trying these ideas.

CRS

---

