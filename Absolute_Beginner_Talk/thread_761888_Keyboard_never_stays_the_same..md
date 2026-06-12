---
title: "Keyboard never stays the same."
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-04-21
Hi

I configured my keyboard for the UK. With a Dell standard keyboard and it worked fine. the @ was in the right place and all the other symbols.

However when i restart the settings appear the same, UK layout, Dell keyboard but the whole layout is different, like a US layout, but the Keyboard prefs say UK.

Anyone had this before?

Its might annoying in the terminal as i dont know where the wiggly line is >_<

---

### Post by wesleybailey on 2008-04-22
Might be a X11 and Gnome conflict?

What is in your /etc/X11/xorg.conf? 

Here is mine.
> 
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection


I'm guessing, but I think that is where your problem, might be coming from.

---

