---
title: "Screen res ?"
date: 2006-06-22
forum: Bug Reports / Support
---

### Post by SteffJay on 2006-06-22
:confused:  I have set the screen resolution to **1024 - 768** @ **60 Hz**. When i restart the system with the monitor off, it defaults to **640 - 480**. I need this to be the first setting as when it is 640-480 the screen is to small to work with. I connect remotely to the pc to make any adjustments that are necessary and need to have a good size screen of 1024-768. Is this a bug or is there a work around ?

---

### Post by enyaw on 2006-06-22
[QUOTE=SteffJay]:confused:  I have set the screen resolution to **1024 - 768** @ **60 Hz**. When i restart the system with the monitor off, it defaults to **640 - 480**. I need this to be the first setting as i connect remotely to the pc to make any adjustments that are necessary. Is this a bug or is there a work around ?[/QUOTE]

Sorry I don't have a solution, but >= I do have the same problem. :( 

-enyaw

p.s.  This occurs on my machine even with the  monitor on!

---

### Post by SteffJay on 2006-06-23
It seems to me that it detects the monitor (when the monitor is switched on) you are using and loads the driver for it then it applys the setting that you set when you first installed Ubuntu. If on bootup it detects no monitor, it automatically defaults to 640-480 because it thinks that there is no monitor there !!  Looking at the screen-res app, you can set the screen by default but it says that this default setting is for **servers** only ??? (just a guess).

---

### Post by enyaw on 2006-06-24
[QUOTE=SteffJay]It seems to me that it detects the monitor (when the monitor is switched on) you are using and loads the driver for it then it applys the setting that you set when you first installed Ubuntu. If on bootup it detects no monitor, it automatically defaults to 640-480 because it thinks that there is no monitor there !!  Looking at the screen-res app, you can set the screen by default but it says that this default setting is for **servers** only ??? (just a guess).[/QUOTE]

I was incorrect...It doe not occur when the screen is turned on.  I wanted to inform you and others of this so that my earlier input would not cloud your thinking.  I stiil have no solution.  :(

---

### Post by digidruid on 2006-06-24
XServer tries to deterimine the best resolution and refresh rate at startup.
It does this firstly by polling the screen to figure out what the highest supported refresh rates is.
If your screen is switched off the lowest refresh rate and thus the lowest resolution is assumed.

For all the juicy bits on how to configure your xserver to use the same settings at startup (regardless of whether the screen is switched on or not) follow this link
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

Hope it helps
Worked for me

---

### Post by enyaw on 2006-06-26
[QUOTE=digidruid]XServer tries to deterimine the best resolution and refresh rate at startup.
It does this firstly by polling the screen to figure out what the highest supported refresh rates is.
If your screen is switched off the lowest refresh rate and thus the lowest resolution is assumed.

For all the juicy bits on how to configure your xserver to use the same settings at startup (regardless of whether the screen is switched on or not) follow this link
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

Hope it helps
Worked for me[/QUOTE]

Great direction here...thanks :)

---

### Post by enyaw on 2006-06-26
[QUOTE=SteffJay]It seems to me that it detects the monitor (when the monitor is switched on) you are using and loads the driver for it then it applys the setting that you set when you first installed Ubuntu. If on bootup it detects no monitor, it automatically defaults to 640-480 because it thinks that there is no monitor there !!  Looking at the screen-res app, you can set the screen by default but it says that this default setting is for **servers** only ??? (just a guess).[/QUOTE]

I'm curious....did the suggestion from digidruid "South Africa" help.:-k 

Thx...enyaw

---

