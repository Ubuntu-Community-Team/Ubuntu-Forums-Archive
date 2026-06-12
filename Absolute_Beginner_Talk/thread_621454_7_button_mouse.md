---
title: "7 button mouse?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-11-23
I have a logitech mouse (v200 I think) that has a middle mouse wheel that scrolls, but it also can rock left and right, adding 2 more buttons in the mix.

How can I enable those mouse buttons for use with my compiz keybindings, firefox, and other general use? How do I manipulate the Xorg configuration to get those working?

---

### Post by jingo811 on 2007-11-23
checking...
For Feisty I use this wiki couldn't find any helpful info in the Gutsy guide though.  But might give you some clues on your search for the real answer.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox)

---

### Post by Onay on 2007-11-23
Yeah, all of that is for side buttons, but mine is a side *rocker* on the scroll wheel, its a bit different.

---

### Post by jingo811 on 2007-11-23
Sorry wrong number :)

---

### Post by smithman89 on 2007-11-23
You should first run
```
xev
```
This is a program that tests various X events.  Hover over the outlined box and press the rocker buttons to see what their keymapping is.  Once you have done that, use that keymap for the compiz settings.  Though i cannot help you on using them in firefox, i could never get my regular extra buttons to work for that.

---

