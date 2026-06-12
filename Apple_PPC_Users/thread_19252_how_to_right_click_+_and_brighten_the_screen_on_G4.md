---
title: "how to right click + and brighten the screen on G4 powerbook"
date: 2005-03-11
forum: Apple PPC Users
---

### Post by luna6 on 2005-03-11
I installed ubuntu hoary....on the powerbook G4...but for the life of me cannot figure out how to right click like in windows/linux on x86 without the second mouse button. Can someone explain what keys to hit for the option? 

also the brightness keys on F1 and F2 does not seem to be working, how would I be able to brighten the screen it is pretty dim....

 thanks

---

### Post by callipeo on 2005-03-11
> **luna6]I installed ubuntu hoary....on the powerbook G4...but for the life of me cannot figure out how to right click like in windows/linux on x86 without the second mouse button. Can someone explain what keys to hit for the option? 
[/QUOTE]

(I have an iBook G4, but it should be the same)
Right click and middle click are emulated with F12 and F11 said:**
> also the brightness keys on F1 and F2 does not seem to be working, how would I be able to brighten the screen it is pretty dim....


Is pbbuttonsd installed?

---

### Post by ssam on 2005-03-11
You might need to hold the fn key down to get brightness and volume keys working.

you may also want to install powerprefs, a gui configuration tool for pbbuttons

---

### Post by luna6 on 2005-03-11
thanks for the tips but I do have pbbuttonsd installed........and the lcd brighten (F1, F2) buttons dont work, nor the volume buttons (F3,F4,F5)....and i tried holding the FN keys...as well....even if the buttons dont work is there a config file i can change to keep the screen as bright as posible? Right now it is real dim and looks fugly..thanks

---

### Post by callipeo on 2005-03-11
You can change the default brightness level editing the "LCD_Brightness " value in /etc/pbbuttonsd.conf; you can also adjust it on the fly with the command

pbbcmd config TAG_LCDBRIGHTNESS <brightness_level>

If that works, at least you know the problem is keyboard-related.

---

