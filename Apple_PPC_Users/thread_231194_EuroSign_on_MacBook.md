---
title: "EuroSign on MacBook?"
date: 2006-08-07
forum: Apple PPC Users
---

### Post by hajk on 2006-08-07
I run Dapper on a MacBook with US-keyboard, and have mapped the third-level chooser to the left Apple key with:

xmodmap -e "keycode 115 = ISO_Level3_Shift"

and the EuroSign to the E key with:

xmodmap -e "keycode 26 = e E EuroSign"

So, holding the left-Apple key while pressing E should give me the EuroSign, right? Well it doesn't work. Checking the key event in xev shows (in order)

KeyPress event for keycode 115 = ISO_Level3_Shift
KeyPress event for keycode 26 = NoSymbol
KeyRelease event for keycode 26 = NoSymbol
KeyRelease event for keycode 115 = ISO_Level3_Shift

There is no symbol for the EuroSign... I'm stumped.

---

### Post by hajk on 2006-08-08
The trick is to select adding the EuroSign to the E-key (or to the 5- or 2-key) in System -> Preferences -> Keyboard, Layout Options tab. My choice of third-level chooser (the left Apple key) is not available there, but this can be set in a terminal with the command

sudo xmodmap -e "keycode 115 = ISO_Level3_Shift"

Putting this in an executable script to be loaded at boot time completes this.

---

