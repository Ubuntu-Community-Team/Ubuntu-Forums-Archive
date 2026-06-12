---
title: "Desktop Icons"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Pioneer5000 on 2007-07-24
Hey i was wondering is there a way to disable desktop icons? so your desktop is completly empty except background. I know there is and its probally really easy to do but i just cant see it at the moment -.- " sorry is this is an extremely stupid question. And thanks in advance for the help :)

---

### Post by view_say on 2007-07-24
Hi ,good luck!!
That is a panel on the top of the desktop,you just right click on the panel ,and select "delete the panel", the rest is your desktop .

---

### Post by zanglang on 2007-07-24
Hit Alt-F2 and enter 'gconf-editor'. Browse to apps > nautilus > preferences, and untick 'show_desktop'. Or if you prefer commandline-fu:
> gconftool --set /apps/nautilus/preferences/show_desktop --type=bool false

---

### Post by ramjet_1953 on 2007-07-24
No problem!

In a terminal type this : [COLOR="Red"]gconf-editor[/COLOR]

When the window opens, use the nested menu in the left pane to navigate to [COLOR="Blue"]Apps>Nautilis>Desktop[/COLOR]

You will now notice in the right hand panel ticks in front of various desktop items.

Just un-tick the ones that you no longer want on the desktop.

Regards,
Roger :cool:

---

### Post by por100pre1 on 2007-07-24
You can also install gTweakUI:

```
sudo aptitude install gtweakui
```

and then look for "gTweakUI - Nautilus" under System > Preferences.

---

### Post by Crafty Kisses on 2007-07-24
> **ramjet_1953 said:**
> No problem!

In a terminal type this : [COLOR="Red"]gconf-editor[/COLOR]

When the window opens, use the nested menu in the left pane to navigate to [COLOR="Blue"]Apps>Nautilis>Desktop[/COLOR]

You will now notice in the right hand panel ticks in front of various desktop items.

Just un-tick the ones that you no longer want on the desktop.

Regards,
Roger :cool:

Thanks for that. :)

---

### Post by Pioneer5000 on 2007-07-24
Awsome that was easy and fast, but i prob wouldn't have figured out on my own so thanks so much for the help.

---

