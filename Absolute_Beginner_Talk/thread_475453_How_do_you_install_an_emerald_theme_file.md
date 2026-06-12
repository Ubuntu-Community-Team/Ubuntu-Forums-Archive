---
title: "How do you install an emerald theme file?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-16
Hi,
sorry but I've been trying to install beryl themes with no luck.
Beryl is working fine. I just cannot install themes.
Don't know how to...

I downloaded a file them: SGlass.emerald but I cannot install it.
I open the Beryl Settings Manager. I click on Import, select the file from my Desktop and nothing happens.
Shouldn't my windows take up the new theme? the glass theme?

How do we do that?

---

### Post by ROUBOS on 2007-06-16
Sorry it looks like I did not have emerald themes installed.

So I now have the Emerald Theme Manager under System>Preferences

So how do I install the theme and activate it?

---

### Post by bigken on 2007-06-16
you open emerald and import the file then select it

---

### Post by ROUBOS on 2007-06-16
I open Emerald, and there are some Themes in there pre-installed. I select them, but nothing happens. The Ubuntu default human theme does not change :(

---

### Post by bigken on 2007-06-16
you need to running beryl for the emerald themes to work

---

### Post by ROUBOS on 2007-06-16
Beryl is running on startup. It's always on. Is there an option I have not selected somewhere?

---

### Post by ROUBOS on 2007-06-16
RESTART maybe?

---

### Post by bigken on 2007-06-16
click on the beryl icon go to select window manager then select beryl

---

### Post by ROUBOS on 2007-06-16
It is selected :(

---

### Post by bigken on 2007-06-16
are any of the beryl features working ie the cube ect

---

### Post by ROUBOS on 2007-06-16
yes. I spin around and even all the window effects fire etc work

---

### Post by bigken on 2007-06-16
very strange try reinstalling emerald using synaptic

---

### Post by ROUBOS on 2007-06-16
Does the Desktop Effects have anything to do with it? It's on. Does it need to be off maybe?
And My Restricted Drivers - ATI accelerated graphics driver is disabled.
Beryl works fine though

---

### Post by bigken on 2007-06-16
I also have an ati card which runs fine without the restricted drivers

both desktop effects and beryl run with no problems

---

### Post by ROUBOS on 2007-06-16
Yes my Beryl works fine. It spins around, go the fire effect when closing windows. Wiggles windows and all.
Just the themes :(

---

### Post by bigken on 2007-06-16
try removing the emerald package then reinstall it

---

### Post by ROUBOS on 2007-06-16
LOL
Sorry mate. I feel so stupid.
I had to select the window decorator. LOL

Sorry dude.

Thanks for your replies. It works now

---

### Post by bigken on 2007-06-16
[LEFT]We all learn by our mistakes LOL
[/LEFT]

---

### Post by dronepower on 2007-06-18
well i have the same problem.

somehow no theme at all is loaded i guess, cause no window bars ar ebeing shown. 
No option to resize windows at well.

I try to install a theme - also pre-installed - . but have no idea how to get them working. :(

---

### Post by cerebellum on 2007-06-22
i think the hidden window bars can be solved by enabling the desktop effects.
btw, where's the select window decorator part? care to explain? thnx.

---

### Post by dronepower on 2007-06-22
My problem was solved using follwing command in terminal:

sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by cerebellum on 2007-06-22
I'm using ATI.
Followed the instructions at [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html) but still can't get it work using the restricted driver of ATI.

Haven't got the time to explore for now, disabling the restricted driver for now. But it still works like a charm.

---

### Post by Herix on 2007-06-26
I had the same problem. all I did was right click on the beryl Icon on the toolbar on the top and Select Window decorator: Standard Beryl decorator(Emerald)

---

### Post by cerebellum on 2007-06-26
My problem was that beryl wasn't installed properly, and it crashed when I selected the beryl window decorator.

---

### Post by kinglet on 2008-02-17
> **ROUBOS said:**
> Hi,
sorry but I've been trying to install beryl themes with no luck.
Beryl is working fine. I just cannot install themes.
Don't know how to...

I downloaded a file them: SGlass.emerald but I cannot install it.
I open the Beryl Settings Manager. I click on Import, select the file from my Desktop and nothing happens.
Shouldn't my windows take up the new theme? the glass theme?

How do we do that?

Alt+F2 -> Run -> **Emberald --Replace** ;-) I hope ur problem will be solve.

---

### Post by sting547 on 2008-07-01
my emerald icon doesn't give me the option to activate windows decorator! can anybody help? plz respond! :(

---

