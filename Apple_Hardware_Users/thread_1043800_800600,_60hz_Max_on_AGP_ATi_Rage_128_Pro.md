---
title: "800*600, 60hz Max on AGP ATi Rage 128 Pro"
date: 2009-01-18
forum: Apple Hardware Users
---

### Post by MechWarrior001 on 2009-01-18
I'm using a Samsung Syncmaster 932b w/ VGA input (need a ADC to DVI for digital) and for some reason, Ubuntu 8.04 is saying the only resolutions available are 800*600 at 56 & 60 HZ. Can anyone help me?

---

### Post by beekr on 2009-02-25
Here is what I had to do to fix 800x600 only with an ATI Rage 128 pro card. You don't have to do the following, but maybe just cat out the file and see if you already have these settings

When I ran
```

gksudo displayconfig-gtk

```

I would get an error at the bottom saying "Index error: List index out of range", so then I opened a terminal and took a look at my xorg.conf file. 

First I backed it up with:
```

cp /etc/X11/xorg.conf /etc/X11/xorg.bak

```

Then I edited the file with:
```

sudo vi edit /etc/X11/xorg.conf

```

Once that was opened, I stepped down till I found the line that said " Configured Video Device". This is what I found:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Then I edited the file by pressing i and right under "Identifier" I added a line that said Driver  "ati"  So when I was done it looked like this:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
EndSection

To save the file and exit vi, press <esc> : wq

Then exit the terminal and reboot system. When it came back up, I clicked on Applications >> other >> screens and graphics. From there I was able to select a monitor type. It asked me to log out and back in. Then, I was able to go to System >> Preferences >> Screen Resolution and select 1024x768 and higher. I do hope this helps. Have a good one.

Beekr

---

