---
title: "Slightly rather urgent problem - graphics drivers"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2007-05-13
Okay so I tried to install the ATI drivers and erm.. it went tits up. I now have nothing except a dos like screen when I boot Ubuntu. How do I put the default drivers back? If possible I could do with an exact break down of the commands to use so I can just type them out and fix it from the terminal (I assume it's a terminal screen).

And well.. sooner the better :P

---

### Post by Hobo Joe on 2007-05-13
Go into recovery mode and type:
```

sudo dpkg-reconfigure xserver-xorg

```
On the one for video drivers, select vesa. Just leave all the other options as they are.

---

### Post by Happy_Man on 2007-05-13
it is a terminal screen. First off, login and then enter this:
```
sudo nano /etc/X11/xorg.conf
```

Scroll down, and when you get to the part that looks like this:
> Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 420]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
(the specifics will vary) change whatever you have in place of "nv" to "vesa" (with quotes). Then press ctrl-alt-backspace, cross your fingers, and hope it works.

---

### Post by codejunkie on 2007-05-13
> **DiJEH said:**
> Okay so I tried to install the ATI drivers and erm.. it went tits up. I now have nothing except a dos like screen when I boot Ubuntu. How do I put the default drivers back? If possible I could do with an exact break down of the commands to use so I can just type them out and fix it from the terminal (I assume it's a terminal screen).

And well.. sooner the better :P

login when you get to the terminal and enter 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
this will revert you back to the default driver settings for you card, now reboot the computer by pressing ```
ctrl+alt+delete
```
hope this helps..

---

### Post by Bakerconspiracy on 2007-05-13
I wouldn't try Happy Man's solution.....

---

### Post by Hobo Joe on 2007-05-13
> **Bakerconspiracy said:**
> I wouldn't try Happy Man's solution.....

Yeah, I second that. In general, if you don't know  a whole bunch about editing the xorg.conf, don't do it.

---

### Post by DiJEH on 2007-05-13
Okay I can now get back into my PC but the resolution options are all missing. I usually run at 1280x1024, but under preferences - screen resolution it only gives me the options of 3 up to 1024x768. Any ideas?

Thank you everyone BTW

---

### Post by Hobo Joe on 2007-05-13
I *think* you can manually add those into xorg.conf to make them available, but I'm not sure. I'd get an expert opinion before you tried it.

Out of curiousity,  what method did you end up using to get back in?

---

### Post by DiJEH on 2007-05-13
sudo dpkg-reconfigure -phigh xserver-xorg - worked. :)

The problem is I don't know how to config those things. could someone point me in the right direction? :)

---

### Post by Happy_Man on 2007-05-13
Sorry, but you'll have to run dpkg-reconfigure xserver-xorg again.
When you get to the screen that lists a load of resolutions, scroll down and highlight using the spacebar, the ones that your computer supports. Afterwards, reboot and see if it will let you change.

---

### Post by DiJEH on 2007-05-13
> **Happy_Man said:**
> Sorry, but you'll have to run dpkg-reconfigure xserver-xorg again.
When you get to the screen that lists a load of resolutions, scroll down and highlight using the spacebar, the ones that your computer supports. Afterwards, reboot and see if it will let you change.

Tried that, it went nuts.. AKA it all distorted and went to hell. I'm not in 800x600 now.. spiffy :/

Starting to think tomorrow I'll just burn a fiesty CD off, back up everything (woo 50 gigs of file transfering, how cool will that be!?) and restart :/

---

