---
title: "[SOLVED] Numbered keys on wired keyboard"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by mfox on 2008-11-08
I have an Apple wired keyboard that I use with my Intel iMac and I noticed the other day that I got no input from the numerical keypad keys on Ubuntu 8.10 running from VirtualBox.  I don't think this problem is specific to keyboard, Ubuntu version or virtual program because I get the same problem when using the numerical keypad from my Mattias keyboard running Ubuntu 8.04.1 on an Intel Mac mini on VMware Fusion.  Does anyone know of a way to activate these keys?

---

### Post by cyberdork33 on 2008-11-08
> **mfox said:**
> I have an Apple wired keyboard that I use with my Intel iMac and I noticed the other day that I got no input from the numerical keypad keys on Ubuntu 8.10 running from VirtualBox.  I don't think this problem is specific to keyboard, Ubuntu version or virtual program because I get the same problem when using the numerical keypad from my Mattias keyboard running Ubuntu 8.04.1 on an Intel Mac mini on VMware Fusion.  Does anyone know of a way to activate these keys?
the "clear" key is the numlock key. It should toggle between numbers and arrows for the number pad.

---

### Post by mfox on 2008-11-09
I'll have to check this clear key on my Apple keyboard, but meanwhile, I discovered how to enable the numeric keys on my Mattias keyboard.  In System Preferences->Preferences->Keyboard from the main menu, there is a layout options button.  One of the layout options under "Miscellaneous Compatibility Options" is "Numeric keyboard keys work as with Mac".  That did it.

I have several VMs installed on my Intel Macs and the only one that picked up the keyboard correctly out of the box with Mandriva 2009.  But enabling the keypad was no hassle in any of the others once I discovered the "magic menu". :)

---

