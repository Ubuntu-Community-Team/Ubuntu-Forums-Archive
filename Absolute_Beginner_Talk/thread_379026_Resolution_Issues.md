---
title: "Resolution Issues"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by bullsandbears on 2007-03-08
hello all.  i feel bad making my first post a "please help me" one, but alas i am in need of help.  i installed Ubuntu without a hitch on my laptop and everything was peachy.  unfortunately, i got ambitious and decided to put Beryl on as well.  the installation went well but i got the infamous "can't load your graphics display / XServer" problem.  i overcame that obstacle, but now when i'm in Ubuntu, i can not load a resolution higher than 1024x768.  if i switch to 1400x1050 (which is what i was running prior to the Beryl install), my screen glitches up, as seen in the attachment.  so, my question is - how can i fix this?  i assume that in the process of installing Beryl that i got my ATi driver overwritten by the script that i used.  any help would be greatly appreciated.

**EDIT**

i solved my own problem.  i simply had to reconfigure my Xserver settings again (i looked at the conf file and realized that my max resolution was set at 1024). :p

---

### Post by Scunizi on 2007-03-12
I'm no expert on Beryl (or anything for that matter).  Your solution might just be as simple as this:
from the command line try > sudo dpkg-reconfigure -phigh xserver-xorg and follow the prompts.  If that doesn't work you could always > gksudo gedit /etc/X11/xorg.conf  look for the lines that detail the resolutions.  If you don't see the resolution that you need/want just add it following the guidelines you see in the file.  When you're done, save then CTRL/ALT/Backspace to restart X, log back in and see if it worked!

---

