---
title: "Considering making the jump"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-03-27
I have a 3.0ghz pc with 2 gigs of ram and 220gb combined HD space(2 drives) that I want to turn into both a workstation and small server to run some text-based games and maybe a site or two.

Which would fit my needs better? Ubuntu, Ubuntu server? Kubuntu?

Also, I've been looking at VMware and it looks very neat as I could put my server on a virtual machine and do full backups on a consistent basis. Is this smart?

Also, how well does Wine work? I want to use some basic programs like Google Sketchup, Photoshop and my mud client, pueblo, would it be a pain in the *** every time I wanted to use it or is it easy?

Also, I tried to run a kubuntu install cd and my Microsoft Comfort Wireless Keyboard and Mouse was not detected. I tried a normal keyboard/mouse. The mouse worked, the keyboard did not (both work on windows). Is there any reason this could be happening?

---

### Post by houstonbofh on 2007-03-27
Well, you left out the important specs, like what video card, sound, IDE, WiFi...  These are the things that can be problems with the wrong hardware.  As to version, you have the power, so go with Ubuntu.  It uses Gnome, and is the heaviest.  But, it has the most config tools...  The others are changed from stock for performance reasons. (Or they like KDE)

WINE sometimes works.  Check the AppDB at [www.winehq.org](www.winehq.org) for details.

As to the keyboard, if it works in the BIOS it will work in Linux.  If it doesn't, it may not.  Try the full ubuntu LiveCD, and also try the BIOS settings to emulate a ps2 keyboard.

---

### Post by tonyr1988 on 2007-03-27
Unfortunately, I can only answer a few:

-I *think* that Ubuntu server does not have a GUI installed by default - if you're running GUI apps, you'll probably want the Desktop CD. Using your computer as a server isn't hard on the Ubuntu Desktop version, either. Example, if you want Apache (and all dependencies), do this:

> sudo apt-get install apache

:) w00t

-Wine works **amazing** for some things, and **absolutely horrible** for others. If you plan on using Wine, bookmark this site:

[http://appdb.winehq.com](http://appdb.winehq.com)

It's user-contributed (like a wiki) and has many programs. Here are the pages for Sketchup and Photoshop:

[http://appdb.winehq.com/appview.php?iAppId=1815](http://appdb.winehq.com/appview.php?iAppId=1815)
[http://appdb.winehq.com/appview.php?iAppId=17](http://appdb.winehq.com/appview.php?iAppId=17)

Plus, the guys working on Wine keep making it better and better, so you may want to keep an eye on your WinApps that don't work yet to try again in the future.

-For your keyboard / mouse: I don't have those, but from other threads, you may want to try this (if you can find a working keyboard / mouse) from the Terminal (once you have Ubuntu installed):

>  sudo apt-get remove bluez-utils

Reboot and see if it works. If it doesn't, you can reverse that command with:

>  sudo apt-get install bluez-utils

---

### Post by sunexplodes on 2007-03-27
Ubuntu would probably work fairly well for your purposes, but you should tell us what graphics card you're using, and if you're using wifi, what wireless card you've got. those are the bigger issues most people have at first. 

in terms of the keyboard, you might have to change a setting in your bios to allow for usb keyboard use, there's such an option in my bios settings.

Wine works fairly well, but you should check out their website for compatibility concerns. Your mud client may work, but i'm sure linux has several alternatives. I've heard of photoshop running okay, but most of the stuff an average user would use it for is covered by The Gimp. I'm not sure about google sketchbook though.

---

### Post by Warpnow on 2007-03-28
My video card is a radeon 9200.

I won't be using wireless to connect my desktop.

---

### Post by sunexplodes on 2007-03-28
Yeah, should be fine. ATI is fairly well supported. Not as well as nVidia, but you should have no serious issues.

---

### Post by Warpnow on 2007-03-28
Toying with the Live CD, I still can't get it to recognize my keyboard (grrrr). It works in windows, the bios, ect, but when I am in linux the lights on the USB reciever stops coming on.

Weird part is that it works during the boot menu for ubuntu, but not once its loaded or during the install.

BTW, I've looked at VMware, wouldn't it work better than wine? I could just boot up windows itself when I wanted to use a windows application.

---

