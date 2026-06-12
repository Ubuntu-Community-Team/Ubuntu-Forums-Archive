---
title: "USB Mouse MiniMac Problem"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by bucko on 2006-07-24
Hi I have a PPC MiniMac with Dapper Ubuntu all up to date, it's a great OS btw been using it as my Mac only OS good few weeks now. 

Theres just two annoying things atm, after running  

sudo dpkg-reconfigure xserver-xorg

All was fine but my mouse (a Logitec Cordless Desktop Optical, very old mouse now but still works fine) goes funny on bootup. Sometimes it works, sometimes it doesn't. I have to keep unplugging it, trying it in different USB ports etc for it to eventually work. This is getting annoying now and I tried to find a fix but I couldn't.

It's set to Explorer/PS2 in Xorg, before it wouldn't even work on IM/PS2 or whatever it was. 

Here is the mouse section,

> 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"


Is there some sort of USB option I should use, btw if I use my Mum's USB mouse it works fine every bootup, I think my mouse just needs tweaking some how, btw works fine on my PC.

Also how do I change my USB keyboard to GB layout, I put it in GB-UK in config option but it don't seem to work, 

> 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbVariant"    "uk"
        Option          "XkbOptions"    "lv3:lwin_switch"


Am I choosing the wrong option here?

I can't even use the pound sign which is buging me. 

Apart from that all is good, cheers.

---

### Post by richbarna on 2006-07-24
Silly answer first, have you checked the batteries in the cordless optical mouse?, mine run down quite quickly.

Second, to change the keyboard language setting, you open the terminal and type :-
> xmodmap /usr/share/xmodmap/xmodmap."[COLOR=Red]keyboard code[/COLOR]"

For example, my Spanish keyboard code is :-
> xmodmap /usr/share/xmodmap/xmodmap.[COLOR=Red]es[/COLOR]

Hope that helps :)

---

### Post by bucko on 2006-07-24
Hi the xmodmap seems to work :D, hope it's permanent after reboot.

The batteries last a long while in my mouse which is what I like about it.

---

### Post by bucko on 2006-07-25
Nope that is not permanent on the keyboard :(. Anyone know about my mouse?

---

### Post by bucko on 2006-07-27
Bump

---

### Post by bucko on 2006-07-28
bump

---

### Post by bucko on 2006-07-31
Bump, problems still persist, USA keyboard and Mouse problems. Is anyone alive in this forum?

---

### Post by bucko on 2006-07-31
Seems I fixed the keyboard :D, £££ see :D. Now just mouse problems left.

---

