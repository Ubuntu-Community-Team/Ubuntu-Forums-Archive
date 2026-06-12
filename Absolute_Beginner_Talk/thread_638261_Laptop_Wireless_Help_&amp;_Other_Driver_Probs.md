---
title: "Laptop Wireless Help &amp; Other Driver Probs"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by TheOnlyMerlin on 2007-12-11
I just installed Ubuntu off of a livecd order from Canonical.  It has properly partitioned and installed and is in general good order except I can't seem to get my wireless card working.  

I have an icon in the top right corner that tells me restricted drivers are available for my machine.  
I go to this menu, I see 3 items.  
I see* (Begin text rendition of a window panel)*:

[FONT="Arial"][SIZE="2"]
[CENTER]Restricted Drivers (Window title)[/CENTER]

[INDENT](Bunch of text I don't feel like writing) [/INDENT]

Component                                                                | Enabled  | Status
----------------------------------------------------------------------------------------------------
v Driver:
[INDENT]ATI accelerated graphics driver                           [RIGHT] [ ]             Not In Use[/RIGHT] [/INDENT][INDENT]Software modem driver                                        [RIGHT][ ]             Not In Use[/RIGHT][/INDENT]
v Firmware
[INDENT]Firmware for Broadcom 43xx chipset family        [RIGHT][ ]             Not In Use[/RIGHT][/INDENT]

-----------------------------------------------------------------------------------------------------

 ? Help                                                                                   [RIGHT] x Close[/RIGHT]
[/SIZE][/FONT]
[I]
(End Text rendition of software window)[/I]

I tried clicking on the graphics driver first and then it confirms that I want to do that, i say "enable driver" and then it gives me an error message saying:

[FONT="Arial"][SIZE="2"]
"The software source for the package

[INDENT]   xorg-driver-fglrx[/INDENT]

is not enabled"  
[/font][/size]

And it never gets enabled.  What happened here?

Next I tried the Software modem driver, it asks me to put in the ubuntu live cd, so I do.  it installs and works perfectly, and now it is checked as enabled (yay, it worked)

The last one is the big one.  I tried enabling the Broadcom firmware, it also asks for confirmation and then it gives me the following error:

[FONT="Arial"][SIZE="2"]
"The software source for the package

[INDENT]    bcm43xx-fwcutter[/INDENT]

is not enabled."
[/font][/size]

What happened here?  This is the important one to get working because my LAN port on my laptop is broken and so I cannot use ethernet for internet, leaving me only either wireless or dial up, and I don't have a dial up account anywhere, leaving me only with wireless.  

So you know it is a HP Pavilian zv6000 (6130us to be precise).  Any help would be greatly appreciated.  

Thanks,
***    -TheOnlyMerlin***

*PS I hope you liked my ascii renditions of the screens.*

---

### Post by wormser on 2007-12-11
First lets get your wireless working.

> "The software source for the package bcm43xx-fwcutter is not enabled."

It looks like you need to open up the universe and multiverse repositores.  System> Administration> Software Sources.  Check the universe and multiverse.  I would uncheck CD.  Now go to Restricted Drivers and install.  Then install your graphics card.  It usually requires a reboot,

Opps, I missed the part where your LAN was broken.  You are going to have to download the file then go to Restricted Hardware and select the location of the file.  I will take a look where bcm43xx-fwcutter can be found.

---

### Post by spiderbatdad on 2007-12-11
it's telling you, you are missing software packages. You can add these packages from the synaptic package manger under Application-->System-->Administration-->Synaptic Package Manager. The list you see at first may not include the packages you want. You will need to enable the universe and multiverse repositories under Settings, the hit "reload" button.

---

### Post by TheOnlyMerlin on 2007-12-11
I went to the software sources menu per your requests, and added the given locations, which appear to help me if I had internet access on that computer.  Now, I have internet access on the laptop thorugh windows, and I have internet access on this computer (my desktop) on both windows and ubuntu.  And If I can get my wireless working on my laptop in ubuntu I am pretty sure it would be a small step to get everything else working.  

BTW, thanks for the help

Thanks,
*   -TheOnlyMerlin*

---

### Post by wormser on 2007-12-11
It sounded like you were doing everything right but without internet it won't work.  Here is the [page]("http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter") to download the file assuming you are using Gusty.  Scroll to the bottom for the download link.  

PS Screen shots would have be nicer... but you had no internet so good job.

---

### Post by TheOnlyMerlin on 2007-12-11
Thank you for finding that file for me.  Much appreciated.  I downloaded "bcm43xx-fwcutter_006-3_i386.deb" onto my desktop, and I am going to put it onto a pen drive and move it to my laptop.  

Although I will be doing this when I get back home, right now I need to go meet my parents for a dinner for my dad's birthday.  

Hope it works (crosses fingers)

Thanks,
*-TheOnlyMerlin*

---

