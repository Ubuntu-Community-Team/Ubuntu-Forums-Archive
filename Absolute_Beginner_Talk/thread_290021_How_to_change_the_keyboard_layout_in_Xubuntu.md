---
title: "How to change the keyboard layout in Xubuntu"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by HenningS on 2006-10-31
So my mom used the computer and BAM the keyboard layout got switched to US. I want it to be the German layout, which is what I set up at install. How do I change this back?

---

### Post by Brutus2006 on 2006-10-31
I had the same probelmm but I wanted to have English.

put in is/usr/share/xmodmap to find your country code
then type in xmodmap/usr/share/xmodmap/xmodmap.xx  (xx is your country code)
Try that worked for me

---

### Post by pana on 2006-11-23
... Or you could simply edit the xorg.conf file :

sudo nano /etc/X11/xorg.conf

find the Section "InputDevice"
Somewhere beneath is a ligne   
OPTION  "XKbLayout" with a value.

Set that value according to your Keyboard Layout (e.g. "sf" for Swiss-French, "us" for US, "fr" for French Azerty etc...)
Save your changes, and restart the X server (CTRL-ALT-BACKSPACE) and voilà, you Keboard has changed.

---

### Post by MasterOfMuppets on 2007-02-12
I added "he" for Hebrew and that didn't quite help...
Any ideas?

---

