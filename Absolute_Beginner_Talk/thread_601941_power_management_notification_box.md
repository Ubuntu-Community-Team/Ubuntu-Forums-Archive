---
title: "power management notification box"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by onlyraider on 2007-11-03
hey
i just installed ubuntu, and im loving it.
one small accident though... i was plugging my laptop in, when i saw the notification on the top panel...
the one thats like a little window on the top saying :"you are now connected to the AC suppy" and then goes away after a while... on that window though, is a little opption to not show it again... 
i accidentally pressed that! 
how can i re-enable that window? 
thanks for all the help.

---

### Post by bluepowder7 on 2007-11-03
just a guess:

system - preferences - power management - general tab.

---

### Post by Dr Small on 2007-11-03
You could check under System > Preferences > Power Management, but I just looked in there and didn't see anything relevant to your situation. I could be wrong though.

Dr Small

---

### Post by onlyraider on 2007-11-03
i already tried that, nothing related... only option for turning sound notificaiton on/off.
i thought maybe that it was the notification panel, but thas not it. 
any other suggestions?

---

### Post by twisted_steel on 2007-11-03
Try running gconf-editor from the terminal.  Navigate to apps/gnome-power-manager.  There is a folder in there called notify.  Is there anything checked/unchecked that should not be?

I know on my laptop I have a horrible battery and I supressed the bad battery warning.  I have the "low_capacity" option unchecked in the notify folder.

---

### Post by onlyraider on 2007-11-03
it worked!!! Thank you soo much!

---

