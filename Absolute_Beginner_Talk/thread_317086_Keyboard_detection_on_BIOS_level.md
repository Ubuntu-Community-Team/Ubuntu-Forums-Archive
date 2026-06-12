---
title: "Keyboard detection on BIOS level"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-11
I brought a friend's computer over to install ubuntu over his windows and used my peripherials (keyboard, mouse, screen) to do the install. I had forgotten this person had had a problem with his pins in the screen (monitor) connection in that they were all crooked ...tried to install ubuntu and kept on getting stuck because gdm couldn't load. In trying to get answers here(forum), I disconnected everything from this old computer and tried plugging things back to my own, which had resulted in a crooked pin on my monitor connection (which I had to set straight with a pen to connect to my own computer) and also all the mouse and keyboard PS2 connectors were either crooked or broken. I didn't worry about this as I ad a PS2 extension on top of a USB keyboard/mouse and directly plugged the USB connections to my computer without the PS2 connectors and restarted. Here's where I am having a problem...
While booting, the BIOS complains about a missing keyboard and beeps numerous times until GRUB takes over and loads the default OS, at this stage, my keyboard is inactive and I can not choose what OS I want to boot in. Shouldn't a USB keyboard be read at the BOIS level?
also How can I install ubuntu on my friends computer without getting a successful gnome session?
Will elaborate if my questions are not clear enough,....

---

### Post by chalex on 2006-12-11
Do you have "USB keyboard support" or "USB legacy support" or something like that turned on in your BIOS?  Try changing that setting and see what happens.

If you have a USB keyboard, it should be properly detected no matter when you plug it in.  If you have a PS/2 kbd, it needs to be connected when you turn the computer on.  (Both of the above are not always the case, depending on the age of your computer.)

---

### Post by habtish on 2006-12-12
> **chalex said:**
> Do you have "USB keyboard support" or "USB legacy support" or something like that turned on in your BIOS?  Try changing that setting and see what happens.
.
Well, to check that out I would have to hit some key to get me into the BIOS setup screen, since My keyboard is inactive at this stage, all I can do is watch it go by and select ubuntu and boot into it... I can not use arrow keys or any other key

---

