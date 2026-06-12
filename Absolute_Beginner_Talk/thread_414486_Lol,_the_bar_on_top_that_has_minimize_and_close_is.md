---
title: "Lol, the bar on top that has minimize and close is gone."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by JohnnyQuickCash on 2007-04-19
It seems to only do this when beryl is running. Anyway to get it back?

---

### Post by dugas on 2007-04-19
open beryl-manager (right click on diamone), and Select Window Manager (Choose Beryl). If Beryl wm is already picked, pick another one, and then pick beryl wm again.

---

### Post by igknighted on 2007-04-19
sounds like you didn't enable argbglx visuals if you are using nvidia.  Add this line to the "Screen" section of your xorg.conf file:

Option "AddARGBGLXVisuals" "true"

---

### Post by JohnnyQuickCash on 2007-04-19
It works for a sec but goes back to nothing thier. It really anoying cause I cant move any windows.

---

### Post by JohnnyQuickCash on 2007-04-19
> **igknighted said:**
> sounds like you didn't enable argbglx visuals if you are using nvidia.  Add this line to the "Screen" section of your xorg.conf file:

Option "AddARGBGLXVisuals" "true"

A little help on how to do this? I used envy to install my driver

---

### Post by igknighted on 2007-04-19
> **JohnnyQuickCash said:**
> It works for a sec but goes back to nothing thier. It really anoying cause I cant move any windows.

alt+click anywhere on window lets you drag it

---

### Post by igknighted on 2007-04-19
> **JohnnyQuickCash said:**
> A little help on how to do this? I used envy to install my driver

there is a file called xorg.conf, it is in the folder /etc/X11.  You need to open it in a text editor to add that line.  Use this command to open it:
```
gksudo gedit /etc/X11/xorg.conf
```
then find a section called Section "Screen" and add the line I mentioned above to it right before the end section line.

---

### Post by JohnnyQuickCash on 2007-04-19
So it would look like this
  "AddARGBGLXVisuals" "true" EndSection"

or
   "AddARGBGLXVisuals" "true" 
    EndSection

Sorry for being such a nub lol

---

### Post by igknighted on 2007-04-19
> **JohnnyQuickCash said:**
> So it would look like this
  "AddARGBGLXVisuals" "true" EndSection"

or
   "AddARGBGLXVisuals" "true" 
    EndSection

Sorry for being such a nub lol

The second one.

---

### Post by jiminycricket on 2007-04-19
Can you get it to start by typing 'beryl' in a terminal?  I had this weird problem on one of my ATI cards where opening beryl from beryl-manager didn't work, but that did.

Also you can get metacity (if using Gnome) back by doing ALT + F2 and typing metacity.

---

