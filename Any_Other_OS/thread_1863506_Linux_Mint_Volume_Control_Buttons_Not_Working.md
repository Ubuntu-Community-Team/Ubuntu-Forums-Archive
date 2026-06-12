---
title: "Linux Mint: Volume Control Buttons Not Working"
date: 2011-10-17
forum: Any Other OS
---

### Post by meatytaco on 2011-10-17
Hi, I have a Sony Vaio Laptop, Model VGN-FE880E. After installing Linux Mint 11 (Katya), the volume control buttons above my keyboard are useless. I believe it should be noted that, while the mute button also does nothing, it toggles the mute light that's built in to the button on and off. Also, the volume and mute buttons did work in Natty. So my question is, does anyone know what controls this or how it's controlled? Not a big problem, but one worth looking at and learning from :D.
               Thanks,
                    Taco

---

### Post by meatytaco on 2011-10-17
Okay, this is weird. Was messing around with my theme, and went to explain what I originally posted for, and my volume buttons now work. O.o Only problem is, now I have no actual sound coming out of the speakers. :/ Its one or the other apparently.

---

### Post by meatytaco on 2011-10-17
And another update: Rebooting the system put me back to no buttons with sound... Better than the other way, but still not ideal.

---

### Post by garvinrick4 on 2011-10-17
Go to change the shortcuts in keyboard and make say volume up F12 and volume down F9 for some
reason I do that with all my installs, I cannot remember why those two but must be they are not used
by anything else I would imagine. Works any which way.

---

### Post by meatytaco on 2011-10-18
What command would you use for volume up and down? I don't get a drop down menu with function choices, just an empty command box :\.  Alternately, I can turn the volume up and down from the terminal with ```
amixer -c 0 set PCM 2dB+
amixer -c 0 set PCM 2dB-
```

But pasting that in the command box for the keyboard shortcut does nothing... I'm sure there's something i need before that in the command box, but I'm not sure what it is. Any ideas?

---

### Post by garvinrick4 on 2011-10-18
Systems/Preferences/Keyboard Shortcuts and make them what you want. I use F9 for down and F12 for up. Just went over to Mint to make sure.

---

### Post by meatytaco on 2011-10-18
This is what I'm looking at, I'm running XFCE if that makes a difference. My problem is it's wanting a command, and "volume up" and "volume down" aren't commands O.o ..  I posted earlier commands that work to set my volume up and down, but only in the terminal. Is there something special that I have to do to get them to work in that window?

---

### Post by meatytaco on 2011-10-18
As a side note, I can actually map them to the volume up and down buttons that are above my keyboard. Just can't get the commands to work.

---

### Post by garvinrick4 on 2011-10-18
Sorry running Gnome with the Mint 11 I have hanging around on one partition.

---

### Post by meatytaco on 2011-10-18
O.o

---

### Post by Perfect Storm on 2011-10-18
Moved to Other OS/Distro Talk.

---

### Post by meatytaco on 2011-10-18
Just checking in to say that the Keyboard Shortcuts work in Gnome Desktop Environment. Just not XFCE O.o

---

