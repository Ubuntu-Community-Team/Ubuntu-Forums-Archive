---
title: "Video driver problems"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by vierdreieins on 2007-02-13
I know I must have screwed up my driver settings fixing my screen resolution. But from browsing the forums, I can't seem to find anything about Intel drivers, only Nvidia and ATI. It's set to vesa right now, but I might have accidentally knocked it out of place when it's not supposed to be set there. I need it fixed because scrolling is very jerky and makes me quite nauseous. I've tried using Google to figure out what driver to use (it was FINE until I fooled around with the settings, so I know there's a driver somewhere in the list that works with my computer). Any ideas?

---

### Post by taurus on 2007-02-13
Edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and replace the **vesa** with **i810**.  Reboot and see if it gets any better.

---

### Post by sardion on 2007-02-13
To be certain I will need to see the output of lspci (just type lspci in a terminal and post the output).  That said, for intel it is usually the i810 driver in xorg.conf.  So try that one, and if its not right, post lspci (or priv message me).

---

### Post by vierdreieins on 2007-02-13
I thought it might be the i810, but my chipset is 845gv and I never saw it on any of the lists for i810 when I searched for it. But it worked beautifully, so thank you guys very much. :) I have no idea how I changed i810 to vesa unless I held the arrow button down trying to get to the OK before I remembered the tab button. :p

---

### Post by ramjet_1953 on 2007-02-13
Download [COLOR="Blue"]915resolution[/COLOR] from the repositories, using the syanptic package manager.

In a console type in: [COLOR="Red"]sudo 915resolution -l[/COLOR]

It will then give you a list of available resolutions.

If the desired resolution is in the list, but is way down, for some reson it won't recognise it.
Pick a MODE that you will never use. (MODE 30 is usually ideal)

If you desire widescreen on a laptop for instance 1280 X 800 @ 24 bits/pixel type in:

[COLOR="Red"]sudo 915resolution 30 1280 800 24
[/COLOR]
This will patch 1280 X 800 @ 24 bits/pixel to MODE 30

In a console type in: [COLOR="Red"]sudo gedit /etc/default/915resolution[/COLOR]

Now edit this file to agree with the above. ie

[COLOR="Red"]MODE=30
XRESO=1280
YRESO=800
BIT=24[/COLOR]

Save this and then re-start X

You should now be operating in the new mode and it should also be available as an option in the System>Preferences>Screen Resolution menu.

Regards,
Roger :cool:

---

