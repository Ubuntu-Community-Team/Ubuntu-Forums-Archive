---
title: "changes in X don't affect anything..."
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-05-03
this is pretty weird...
I recently did a format to my computer(long story..), and I'm trying to get the hebrew working again...

So I went to the X file and replaced the keyboard entry to this lot:
> Section "InputDevice"
   Identifier  "Generic Keyboard"
   Driver      "keyboard"
   Option      "CoreKeyboard"
   Option      "XkbRules"      "xfree86"
   Option      "XkbModel"      "pc105"
   Option      "XkbLayout"     "gb,il"
   Option      "XkbCompat"     "group_led"
   Option      "XkbVariant"    "il"
   Option      "XkbOptions"    "grp:switch,grp:alt_shift_toggle,grp_led:scroll"
 EndSection

Trouble is, it didn't do anything, and yes, I did restart X...
I'm using fluxbox and KDE, in KDE I just enabled the layout via X, but I''m stuck in fluxbox...

what can I do?

thanks:D

---

### Post by Caligula on 2006-05-03
ah, it's alright...
happens to me too often, I ask a question here and until someone answers I've already solved the problem...

To the matter, i just got some words wrong...

---

