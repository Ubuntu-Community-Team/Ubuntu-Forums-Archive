---
title: "After installation graphical problems"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by Mr_J_ on 2005-08-15
I installed Ubuntu 5.04. A few times now.... All to try and get my sistem running.

I install and everything goes OK, until it has to start Gnome.

I've installed this sistem for the first time yesterday, and tried to re-install in order to make it work...
 The real problem is that after all those lines of decompacting files, when it asks me what resolution I want, I didn't modify it at first.

2nd- Added the max res for my **[COLOR=Red]Geforce 6600 GT 128MB PCI- E[/COLOR]**, which is 1280x1024.
3rd- I tried nothing but the 640x480

So far all I can to with the sistem is Ctrl+Alt+F* and go to shell.
The F7 which is supposed to be Gnome, just stands there with these squares and lines of color, like a dam jigsaw puzzle...

I'm starting to think it's not the resolution I choose, but some other problem I can't detect.

[COLOR=SandyBrown]What can I do to make Gnome Start correctly?[/COLOR]

Is it something I can fix within a shell?
Do I have to install the correct drivers for my Graphic Board?
Unforseen problems?! ](*,)

---

### Post by PeP on 2005-08-15
the official non free nvidia drivers are not installed by default, cos' it's not open source: 
to install the officila nvidia drivers take a look at this:
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by tseliot on 2005-08-15
Ok, I've had the same problem with my Geforce 6200 PCI-E.

1) This a temporary fix:

when in Ubuntu press CTRL+ALT+F1 so as to get to the command line and type

/etc/init.d/gdm stop (or "kdm stop" if you use KDE)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf

scroll the file down (with your keyboard) until you find the line with the section Device and make sure the word I put in red is “vesa”:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR=Red]nvidia[/COLOR]"
BusID "PCI:1:0:0"

Press:
CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

/etc/init.d/gdm start (or "kdm start" if you use KDE)

Now you won't have graphic corruptions but the quality of your videos won't be excellent.

2) If you want a permanent fix install Nvidia drivers. You can follow my HOWTO but REMEMBER of skipping these steps (as their needed only in Ubuntu Breezy)

[COLOR=Blue]CC=gcc-3.4 (here you have to put the number of the gcc you used to compile your kernel, which is 3.4 in my case*)

export CC[/COLOR]

This is the link:
 [http://www.ubuntuforums.org/search.php?searchid=1414016](http://www.ubuntuforums.org/search.php?searchid=1414016)

---

### Post by poofyhairguy on 2005-08-16
For the 6600 GT, you HAVE to install the Nvidia drivers. The free ones don't work well.

---

### Post by Mr_J_ on 2005-08-16
I already had given up hope to make it work!

 :grin: 

I can try to make it work, and see how it goes!

*Thanks to you all!*


-_-_-_-


I decided to try and install the nvidia drivers instead of anything else...

This is due to me having a wi-fi conection I haven't setup yet!
So no net on linux yet!

I'll just put it into a pen drive I got, and I'll install from there!
Now all I gotta do is use the pendrive in shell, which I believe means mounting the little bugger on my own. Right?

Which I'm non too sure I know how to do, but I got 2 noobie manuals on hand if I need to! ...None are too good tho!


....I was going to install fedora instead of Ubuntu, but I'll stay with Ubuntu if I can!
I happen to like the apt-get thingy! It sounds awesome!

---

### Post by Mr_J_ on 2005-08-16
Thats another thing I need!

I have a MSI PC54G2, which falls under RaLink 2500 driver.
I need to configure it to run with WPA... Preferably!

I'd change to WEP if needs be!


Anyway! :wink: 

[COLOR=SlateGray]How do I set it up in shell mode?[/COLOR]

Is there a way? I kow it's a st00pid question, 'cause everything can be done threw shell! The problem is how I do it. I have no idea what to do in order to make it work...

Within GUI in Warty Live CD I looked at the tools to make it work, but I have no such thing at the time. The weird thing was I wen't to the Wi-Fi setup wizard and the card I found the card with "lspci" was not there under the drop-down menu...

Do i need another driver? :|

---

