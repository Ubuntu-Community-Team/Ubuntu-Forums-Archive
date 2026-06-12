---
title: "keyboard setup"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-02-18
Hi all! Since installing EDGY 6.1.0 I must have chosen US as keyboard layout. I need British (en).
I have tried to change layout options in Systems/preferences/Keyboard. I have selected my Keyboard and tried the UK layout but none are what I need. The character '@'used in email address is only achieved by using the 'shift+" key and if I hit the 'Shift+@ key' : get the " marks.
an anyone help please.
regards

---

### Post by terdon on 2007-02-18
Try doing the following:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo gedit /etc/X11/xorg.conf

Find the section that looks like this:
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "uk"
EndSection


abd change the 
 Option      "XkbLayout" "us"

to

 Option      "XkbLayout" "us"

---

### Post by Sbarton on 2007-02-18
Thanks for your quick reply. Looking at the reply I have assumed that the change should be from 'us' to 'uk'. I have done that but no change to keyboard unfortunately. Any other ideas?
regards

---

### Post by terdon on 2007-02-20
Could you post the relevant lines of your /etc/X11/xorg.conf file?

And, yes, of course the change was meant to be to "uk" :oops:

---

### Post by Sbarton on 2007-02-21
terdon, many thanks for looking back. In retrospect perhaps I should have posted that I have reinstalled 'Dapper'. Less buggy! I enjoyed the quicker bootup and shutdown of 'Edgy' but thats about it. Everything is fine now!
Once again thanks for your input.
regards

---

