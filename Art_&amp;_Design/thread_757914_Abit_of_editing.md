---
title: "Abit of editing"
date: 2008-04-17
forum: Art &amp; Design
---

### Post by Roque2 on 2008-04-17
Okay here is my small problem and someone might be able to help me . I have added a nice looking login screen to gutsy and its mainly white, now when I log in I get that moment of the ubuntu brown, then the white background I have added to my splash screen. That brown is killing me. I have looked in the gdm factory conf and not sure if thats where I need to remove the brown background. Plus when I do go and try to edit it its not allowing me to. If anyone has any ideas about this please help me out.

sudo gedit /etc/gdm/PreSession/Default
Then look for
Code:
# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#FFFFFF"

This is what I did to make my splash screen white.

---

### Post by smartboyathome on 2008-04-17
I can't remember where I saw it, but there is a tutorial here on the forums which tells you how to change that.

---

### Post by duckgoesoink on 2008-04-17
> **Roque2 said:**
> Okay here is my small problem and someone might be able to help me . I have added a nice looking login screen to gutsy and its mainly white, now when I log in I get that moment of the ubuntu brown, then the white background I have added to my splash screen. That brown is killing me...

Maybe a dumb question, but did you check your Login Window Preferences? In the Local tab there is an option to choose the background colour... (I changed my login screen to a grey one, and made the background colour a similar grey via this option.)

---

### Post by Roque2 on 2008-04-17
Lmfao how the heck I missed something that simple I have no clue. Thank you both for responding.:lolflag:

---

