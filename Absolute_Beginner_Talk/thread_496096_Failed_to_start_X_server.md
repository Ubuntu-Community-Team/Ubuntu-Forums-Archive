---
title: "Failed to start X server"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by cde on 2007-07-08
I just made a clean install via Alternatie CD of Xubuntu 6.06.

7.04 wouldn't work but 6.06 gets me a little farther. After the Xubuntu startup flash screen runs, I get the message:

Failed to start the X server

I can login my account and run:

sudo dpkg-reconfigure xserver-xorg

but I don't know much more to do for that other than allowing the defaults.

It seems to detect my Video Adapter pretty well. It's a Matrox MGA Ultima/Impression PCI.

Any responses appreciated. Please try to dumb down instructions for me if you can.

---

### Post by FleetAdmiral74 on 2007-07-08
If you choose recovery mode on startup, it will put you right into a root terminal where you can run the necessary commands.

---

### Post by cde on 2007-07-08
What necessary commands?

---

### Post by overdrank on 2007-07-08
> **cde said:**
> What necessary commands?

Hi I believe it is the command you reference in your first post, I might add just choose for the driver vesa and then if you don't know the answer then leave it at the default given. That way if it gets you to the desktop you can search for your driver. But I have a question the graphics worked when you used the live cd right?

---

### Post by cde on 2007-07-08
Okay, thank you, I'll try that.

7.04 Live CD did not work. I haven't tried 6.06.

---

### Post by cde on 2007-07-08
Alright so I selected vesa, ran the rest of the it on default, typed sudo reboot at the end and it still doesn't work.

Come to think of it, I think I have another old but different video adapter laying around. Should i switch it out and let the reconfigure thing autodetect it and try that?

---

### Post by AndyCooll on 2007-07-08
Setting your graphics card to "vesa" should work since it's a bog standard graphics card setting that works with pretty much everything. Once you're finished you type "startx".

:cool:

---

### Post by cde on 2007-07-08
Muah ha! I put in an old ATI card and it worked! 

Thank you!

---

### Post by heatpumpcontrol on 2007-07-08
READ THIS ALL FIRST BEFORE PERFORMING.....PLEASE

I have an idea,

use the live CD and once up type

gksudo gedit /etc/X11/xorg.conf

look to see what settings are being used by the live cd to activate your video.

Save a copy of this file onto your hd or an external usb and re-log back in to your pc's installation. 

Once you are back to your pc session, if you can't log in click on cnt+alt+f1and log in.

Enter
Sudo nano /etc/X11/xorg.conf

use your down arrow to get to the section where it describes your video card information. 
If you need to change it, DO NOT ERASE ANYTHING, just place a '#' sign without the ' ' (quotes) in front of the line that has the video card info and retype the command that you just placed # sign in front of and now replace the information with the information you copied earlier.

example:

Section "Device"
#      Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
        Identifier      "ATI Graphics"                           
#      Driver		"i810"
        Driver           "vesa"   <----- if this is what the CD showed that it was using.)
	BusID		"PCI:0:2:0"
	VideoRam	128000
	Option		"UseFBDev"		"true"

NOTE: to move the cursor to the next block just hit the 'tab' button. 

Once copied, type:
sudo /etc/init.d/gdm restart

or

sudo /etc/init.d/gdm stop

sudo /etc/init.d/gdm start

Your video should work

gl
hpc

---

