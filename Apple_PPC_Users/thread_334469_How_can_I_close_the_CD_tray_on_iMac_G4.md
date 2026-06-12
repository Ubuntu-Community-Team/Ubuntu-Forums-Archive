---
title: "How can I close the CD tray on iMac G4?"
date: 2007-01-08
forum: Apple PPC Users
---

### Post by ufugu on 2007-01-08
Does anybody know a command to close the CD tray on an iMac G4?

I can eject it in several different audio apps and also by a shortcut assigned in System/Preferences/Keyboard Shortcuts, but can't close it unless I manually push in the tray.  I don't like doing that, I worry about pushing it too hard and breaking it.

Thanks for any suggestions!

---

### Post by bionnaki on 2007-01-08
depends on the location of your drive

this works for me

to open:

> 
eject /dev/hdc


to close
> 
eject -t /dev/hdc


you could just try eject and eject -t if you only have one drive (I have two).

---

### Post by ufugu on 2007-01-09
That works, thank you very much.

I will use this for sure, but I also wonder if there is any way to map the eject -t command to the keyboard or make an Applet or something? It's several steps to do it with the command vs. the way Apple spoiled me with: using a key on the keyboard.

---

### Post by bionnaki on 2007-01-12
I dont know about a keyboard button but I know you can add those commands to the menu or create shortcuts for them for desktop or panel.

---

