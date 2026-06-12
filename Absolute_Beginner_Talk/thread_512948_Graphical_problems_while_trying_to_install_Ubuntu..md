---
title: "Graphical problems while trying to install Ubuntu..."
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Turkish Hijinks on 2007-07-29
Hi folks...

I have been reading fantastic things about Ubuntu (about how it's incredibly user friendly compared to various other versions of Linux), so I decided to give it a try. It was going to be my first time working with anything other than Windows so I was excited.

I had already installed Windows Vista Home Premium on the drive, and I had found a guide explaining how to dual boot Ubuntu and Vista. So I downloaded Ubuntu but ran into an error... I tried both the 64 and 32 bit versions, both gave the same problem.

What happens is, I put the CD into the drive, the Ubuntu boot screen comes up (the one that has the 30 sec countdown and offers a few different options). The first thing to notice is that my keyboard and mouse are frozen while this screen is up (could this be because they are both connected through the USB?), so I actually have to wait for the 30 second countdown to pass and the installer to go the next step by on its own. Anyways, once the 30 seconds are up I get the screen with the Ubuntu logo and the orange bar that bounces back and forth. Once that screen is gone, the install screen comes up but I can't see anything aside from vertical lines that are flashing in different colors. Then the monitor switches to analog mode and gives me an error (something along the lines of "ideal resolution is 1280 x 1024"). I try to change the resolution with ctrl - alt - <+> but its all the same.

I have no idea what to do. I would appreciate any help.

Just some notes that might help:

Processor: AMD Athlon 64 X2 6000+
Motherboard: Gigabyte S Series
Graphics Card: nVidia GEFORCE 6800 GS

I know my way around the hardware, but not so much the software. So I would need extra help (detailed instructions) if I have to edit some files.

Thanks in advance.

---

### Post by splintercellguy on 2007-07-29
Strange. Looks like X did not properly detect your monitor. Try the alternate CD, install it, and then we will take it from there. I wouldn't know about the mouse/keyboard issue though :(.

---

### Post by Turkish Hijinks on 2007-07-29
Hey man, thanks a lot for the quick response.

I'm now downloading the alternate desktop CD. Once I burn it onto a disk, I'll try the installation again with that.

If all goes well (my fingers are crossed), I'll report back via Firefox on my Ubuntu partition :)

If not, I'll come back here asking for more help :(

---

### Post by alienexplorers on 2007-07-29
Have you tried using the alternative install CD where the whole CD install is done in text mode with no graphical pages.  This might help.

---

### Post by the.phantom on 2007-07-29
not a expert but 
think you are right on the usb mouse and keyboard. do you have ps2 plugs on the motherboard? if so you could do it the old fashioned way ;-D

what version of U are yo using?
if fiesty  then i think you can look in add/remove and you will find "restricted drivers"
and you can install the ones for nvidia. but don't know if you can on a live cd?
that part didn't work for me

have you tried the resolution in system>preferences>screen resolution?

---

### Post by Turkish Hijinks on 2007-07-30
> **alienexplorers said:**
> Have you tried using the alternative install CD where the whole CD install is done in text mode with no graphical pages.  This might help.

I'm about to try this. I just downloaded the alternate version, hopefully I don't screw anything up.

[QUOTE=the.phantom] 	not a expert but
think you are right on the usb mouse and keyboard. do you have ps2 plugs on the motherboard? if so you could do it the old fashioned way ;-D

what version of U are yo using?
if fiesty then i think you can look in add/remove and you will find "restricted drivers"
and you can install the ones for nvidia. but don't know if you can on a live cd?
that part didn't work for me

have you tried the resolution in system>preferences>screen resolution?[/QUOTE]

Yeah... I thought about using a PS2 keyboard and mouse, so if all else fails I'll have to look around for one of those (or maybe a USB to PS2 adapter).

I'm trying to install the latest version for fiesty (I think it's 7.04).

Thanks for all the help... I'll keep you all updated.

---

### Post by Turkish Hijinks on 2007-07-30
Well, folks... I come bearing bad news.

I couldn't install the text only version either. Because, much like the graphical version, the text only version also doesn't recognize my keyboard and mouse during the boot screen. The text only version doesn't even have a 30 sec countdown, so I was stuck at that stage. 

For the past hour I've been searching for a 24 hour WalMart, but I couldn't find one. I guess I'll try again tomorrow after I get a PS2 keyboard.

---

### Post by BrockLanders on 2007-07-30
im a relative Linux newb myself, but ill try to help if i can.

I installed Ubuntu 7.04 the other day from the bootable CD and initially ran into similar problems (as far as the graphical glitches) - i encountered the flashing vertical bars.

I booted from the cd again and selected "install in VGA safe mode", and the install seemed to work fine.

As far as your lack of USB keyboard and mouse support - not sure if this is the issue, but ive seen BIOS's in the past with "USB mouse support: enable/disable" options that can be tweaked.  Im unsure if its common for a USB keyboard to have such a setting, but i would double check ur BIOS to see if u need adjust anything to enable native USB input.

hope u can figure it out

---

### Post by splintercellguy on 2007-07-30
BrockLanders, if you have any issues with screen res, sudo dpkg-reconfigure xserver-xorg, and backup /etc/X11/xorg.conf before doing that.

---

### Post by iPirates on 2007-07-30
hey, i was experiancing a similar problem with trying to help my friend install ubuntu on his machine.
ubuntu live cd wasn't recognizing his monitor, or graphics card or something, and wouldn't show anything after the ubuntu live cd loading screen.  All i got was a bunch of funky colored bars that occasionally changed colours when i move the mouse around...

the alternate worked, but i experienced the same problem when i tried booting into regular ubuntu...

someone suggested i try install an earlier version of ubuntu, like edgy or something...  maybe that'll work?  i never did try it myself.

---

### Post by dondad on 2007-07-30
> **Turkish Hijinks said:**
> Hi folks...

I have been reading fantastic things about Ubuntu (about how it's incredibly user friendly compared to various other versions of Linux), so I decided to give it a try. It was going to be my first time working with anything other than Windows so I was excited.

I had already installed Windows Vista Home Premium on the drive, and I had found a guide explaining how to dual boot Ubuntu and Vista. So I downloaded Ubuntu but ran into an error... I tried both the 64 and 32 bit versions, both gave the same problem.

What happens is, I put the CD into the drive, the Ubuntu boot screen comes up (the one that has the 30 sec countdown and offers a few different options). The first thing to notice is that my keyboard and mouse are frozen while this screen is up (could this be because they are both connected through the USB?), so I actually have to wait for the 30 second countdown to pass and the installer to go the next step by on its own. Anyways, once the 30 seconds are up I get the screen with the Ubuntu logo and the orange bar that bounces back and forth. Once that screen is gone, the install screen comes up but I can't see anything aside from vertical lines that are flashing in different colors. Then the monitor switches to analog mode and gives me an error (something along the lines of "ideal resolution is 1280 x 1024"). I try to change the resolution with ctrl - alt - <+> but its all the same.

I have no idea what to do. I would appreciate any help.

Just some notes that might help:

Processor: AMD Athlon 64 X2 6000+
Motherboard: Gigabyte S Series
Graphics Card: nVidia GEFORCE 6800 GS

I know my way around the hardware, but not so much the software. So I would need extra help (detailed instructions) if I have to edit some files.

Thanks in advance.


I had exactly that problem with the keyboard and mouse on usb. In my case, it was a matter of enabling the usb in the BIOS.

---

