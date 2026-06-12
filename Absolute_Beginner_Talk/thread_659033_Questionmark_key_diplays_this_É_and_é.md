---
title: "Questionmark key diplays this É and é"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by fattysfinest on 2008-01-05
Is there a way to re-assign this key back to normal É
This is the only key that seems to do this
Thank you for any help
Brian

---

### Post by ant1060 on 2008-01-05
Hi,
What are your keyboard layout and language options?
You may need to check in System --> Keyboard to make sure you have the correct choice enabled.  Also check your xorg.conf.
:)

---

### Post by ~LoKe on 2008-01-05
Sounds like you've got the French layout enabled.

---

### Post by fattysfinest on 2008-01-05
Hi Thanks for the replies,
I checked my keyboard layout, I have the generic intel keyboard selected by default.
It doesn't matter if I use the laptop keyboard or a plug in one its still the same.
I don know how to check my xorg.config, Just type it in the terminal É (question mark)
I don think its in French mode as thats the only key that seems messed up but I could be wrong.

---

### Post by ~LoKe on 2008-01-05
> **fattysfinest said:**
> Hi Thanks for the replies,
I checked my keyboard layout, I have the generic intel keyboard selected by default.
It doesn't matter if I use the laptop keyboard or a plug in one its still the same.
I don know how to check my xorg.config, Just type it in the terminal É (question mark)
I don think its in French mode as thats the only key that seems messed up but I could be wrong.

Pressing shift+4 should give you a question mark, or maybe it's shift+6, I can't remember.

But if either of those do it, you've got the French layout on.

---

### Post by ant1060 on 2008-01-05
You still need to check what your xorg.conf says.  The easiest way is to run the following command in a terminal : cat /etc/X11/xorg.conf

Look for the part that resembles this :

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

In this example the generic keyboard is set up with the 105 variant using the United States (us) layout.

Post what yours says, and then we may find the solution!

---

### Post by fattysfinest on 2008-01-05
Loke, Yes shift+6 gives me the ??? (yay) so I guess its in french, Thats a start thank you.
Ant1060 here is what you requested. (I hope)
Thanks for your help.
brian

---

### Post by fattysfinest on 2008-01-05
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ca"
EndSection
guess you might want this

---

### Post by ~LoKe on 2008-01-05
Open up gnome-control-center (system -> preferences -> **Gnome Control Center** -- if memory serves).  Click the "Hardware" filter on the left, then choose "Keyboard on the right.  It should open a preference window.  Click the "layouts" tab and choose "U.S. English".

---

### Post by fattysfinest on 2008-01-05
////////???Thank you!, Once I deleted the Canada one from there and added the US one it works. I guess were supposed to speak french here in Canada.
Thanks again to both of you. It's amazing the help everyone gives.

---

### Post by ant1060 on 2008-01-06
You're welcome!

Now, if all is OK, on redoing cat /etc/X11/xorg.conf you should discover that in place of your "ca" you should have "us".  If you don't have, don't be afraid to correct it yourself to "us" (and save the file before quitting) so that the problem never returns!

Good luck!

---

