---
title: "[SOLVED] &amp;quot;Save Screenshot&amp;quot; window no longer appears when I press PrintScree"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-07-04
Hello,
It used to be that when I pressed the PrintScreen button on my keyboard, the [Save Screenshot] window would pop up. However, this is no longer the case. When I press the PirntScreen button now, nothing happens. I am able to go to Accessories/Take Screenshot. That works fine. 

I am sure that there is NO problem with my keyboard/hardware. I checked this out by running [xev] in terminal/CLI. 

So I think we can conclude that the problem is with software/Ubuntu. 

How can we fix this problem?


Thanks.

---

### Post by johnc4510 on 2007-07-04
Try reinstalling gnome-utils

sudo apt-get install gnome-utils

---

### Post by hanzj on 2007-07-04
$ sudo apt-get install gnome-utils
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by johnc4510 on 2007-07-04
Look in System>Preferences>Keyboard Shortcuts and make sure that screenshot is set to the print key and alt+print to the window screenshot

---

### Post by hanzj on 2007-07-04
John,
Thanks for teaching me about Window Screenshot. I used to have to open up gimp to crop the fullscreen screenshot.

That was interesting. [Screenshot] _did_ have [print] as the accelerator key. But when.
I re-edited it and pressed the 'new acceletor key", it had 0x6f for my Print Screen button. It now works. But I wonder why it changed from "Print" to "0x6f". I think it's because I had to fix up my xorg.conf file. It was asking me about my keyboard layout and how many keys were on my keyboard etc. Hmmmm. I wonder whether I have configured xorg.conf with weird keyboard configurations.

---

### Post by johnc4510 on 2007-07-04
hanzj, no problem, glad to help.  I've had the same thing happen with naming of those keys, I don't understand it either. Anyway, glad it worked.  :)

---

