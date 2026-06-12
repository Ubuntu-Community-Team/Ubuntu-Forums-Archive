---
title: "[SOLVED] Turning off Desktop Effects."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-04-22
I turned on the visual effects in Feisty.  My system would crash after a few minutes.  After rebooting I unchecked them from the options for the wobble and cube.  Now it seems some of the effects are still working and they crash my system.  Where can I go to turn off the rest?  There are no other options under system> preferences> desktop effects.

BTW, where can I get the crash data on my system to submit for a bug report?

Thanks

---

### Post by jordanmthomas on 2007-04-22
Did you uncheck the 'enable desktop effects' button or just the cube and wobbly windows?  You need to disable them altogether by unchecking the very first checkbox.

As for the crash data, you'd probably just need to run compiz from the terminal.  How to get it to replace metacity (and by extension, to run), I'm not sure of any more because over time there have been about 20 different ways to start compiz and I switched to beryl (well, compiz-quinn at the time) a long time ago so I'm not sure exactly where compiz stands now.

---

### Post by wormser on 2007-04-22
Yes, I unchecked both.  Those 2 effects do not show up any more.  When I minimize and open a window back up it has the effect.

---

### Post by chakkaradeep on 2007-04-22
Install gnome-compiz-manager by typing the command in the terminal,

**sudo apt-get install gnome-compiz-manager**

And go to **System->Preferences->GL Desktop** and play with the options, this should help you have a safe compiz environment

---

### Post by wormser on 2007-04-22
> **chakkaradeep said:**
> Install gnome-compiz-manager by typing the command in the terminal,

**sudo apt-get install gnome-compiz-manager**

And go to **System->Preferences->GL Desktop** and play with the options, this should help you have a safe compiz environment

I just unchecked Enable GL Desktop.  That seemed to fix it.  

Thanks

---

### Post by jordanmthomas on 2007-04-22
[img]http://www.free-bees.co.uk/images/articles/fedoracore6/desktopeffects.png[/img]
Oops, thought there was another checkbox.  Basically, you just have to click the big **button** that says Enable Desktop Effects.  If they are activated it will say Disable instead.

Glad to see you got it working though.

---

### Post by wormser on 2007-04-22
> **jordanmthomas said:**
> [img]http://www.free-bees.co.uk/images/articles/fedoracore6/desktopeffects.png[/img]
Oops, thought there was another checkbox.  Basically, you just have to click the big **button** that says Enable Desktop Effects.  If they are activated it will say Disable instead.

Glad to see you got it working though.

It did not say disable.  It must be a bug.  The wobble and the cube did get disabled when I unchecked them.  The other effects were still working and would cause it to crash.  Installing the compwiz manager then unchecking GL Desktop solved it.

---

### Post by old_geekster on 2007-04-22
Whenever I enable/disable any effects or plugins, I always reboot my rig (Ctrl + Alt + Backspace).  This is to assure that all of the components are eliminated from the system.

---

