---
title: "Keyboard Layout"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by xwhisper on 2007-09-21
When I switch the keyboard layout to Bulgarian Phonetic (using Alt+Shift) I cannot copy/paste anything. Is there a fix for this?
Here's part of my xorg.config:
Section "InputDevice"
       Identifier  "Keyboard0"
       Driver      "kbd"
       Option      "XkbModel" "pc105"
#      Option      "XkbLayout" "us"
       Option      "XkbLayout" "us,bg"
       Option      "XkbVariant" ",phonetic"
       Option      "XkbOptions" "grp:rwin_toggle,grp:lwin_switch,grp_led:scroll"
EndSection

---

### Post by Nikitas350 on 2007-09-22
see this thread [http://ubuntuforums.org/showthread.php?t=274250&highlight=bulgarian+phonetic](http://ubuntuforums.org/showthread.php?t=274250&highlight=bulgarian+phonetic) :) enjoyyyyyyyyyy

---

### Post by xwhisper on 2007-09-23
I don't have problems switching the layouts, but when I press Alt+Shift it activates ScrollLock indicator and then I can't use Ctr+C, Ctrl+V, Ctrl+X and etc. Is there any fix for this?

---

### Post by Nikitas350 on 2007-09-23
I don't that it can be fixed (i am not sure, i am a newbie). When i switch to Greek keyboard layout  i can't use the ctr-c to copy or ctr-v.... maybe somebody more expert is able to answer your question...

---

### Post by Acunga on 2008-03-12
Well is there a fix to this stupid bug?
Edit:I found that this bug is only for firefox in all other applications I tested shortcuts work:Skype, VLC, text editor

---

