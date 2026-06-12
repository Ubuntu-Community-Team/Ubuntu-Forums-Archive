---
title: "Ubunutu 10.10 on a Mac Mini 2010 (Model #A1347)"
date: 2010-11-04
forum: Apple Hardware Users
---

### Post by jason.fonseca@gmail.com on 2010-11-04
Hi,

I just bought a Mac Mini with the following specs:
2.4ghz Intel core 2 Duo
Nvidia Geforce 320M graphics
HDMI and Mini display port

I installed Refit and then created a bootable usb of Ubuntu amd64 iso (10.10) desktop edition. 

I booted into refit, selected linux icon (boot from pen drive, no issues there?) and it comes up with a screen that has a little pic of a keyboard = human in circle. Well anyway I leave it for about a minute and then I see all this text telling me that ubuntu is loading, and the files it is loading. it goes too fast to read but in any case after that the screen turns off and won't come back on again. The computer doesn't seem to have frozen, it just seems that the monitor won't come on.

When I press the power button once on the back of the mac the hard drive does some work and it shuts down, i can only imagine it is shutting down gracefully. 

I've tried using both the DVI and the VGA components of the monitor. Neither work, the screen always comes up blank.

I've also gone and burnt the iso to cd and tried to boot it but that doesn't work either.

I get the feeling that it's something to do with the display drivers, but since I can't even see the monitor how am I going to be able to get it to use different drivers?

Do I need to edit some start up scripts on the USB so that it uses a very basic legacy driver or is there some sort of switch like "nomodeset" i have to use? and if so, how would I do this without being able to ever see the screen after that initial screen with the keyboard = human in circle?

Could really use some help here, thanks!

---

### Post by matthew malkin on 2010-12-17
once the screen goes dark - if we assume that ubuntu has booted, but just doesn't ahve the right drivers or whatever for your screen you can get into the console by pressing ctrl+alt and F1.

You'll then need to find out what the default ubuntu user and passwords are to get in, and you can use command line to try and get a gui showing - to switch back to the gui mode you use ctrl+alt F7.

---

### Post by tuan kuranes on 2011-02-23
same here.

ctrl+alt and F1 doesn't work nor any other key combination (even atl+sysreq+B or any kernel hotkeys)

More like it just crashed (I got either black or entirely blue screen), by trying some wrong VESA calls.

Tried ubuntu 10.10 livecd and install mode. 

I guess I have to try some other distribution with an install CD that doesn't try anything graphics ?

isn't there a minimal ubuntu install CD does only command line, no clever graphic Vesa modes ?

Once there with a linux command line, we could try and report on serveral X driver and configuration.

---

### Post by matthew malkin on 2011-02-23
Ubuntu does provide a cd they call alternate, that allows for command line installation.

---

