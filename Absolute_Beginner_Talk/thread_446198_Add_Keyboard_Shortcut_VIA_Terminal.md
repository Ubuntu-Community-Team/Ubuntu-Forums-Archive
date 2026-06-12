---
title: "Add Keyboard Shortcut VIA Terminal"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by azarath metrion zinthos on 2007-05-16
[FONT="Trebuchet MS"]Hi everyone! Is it possible to add a keyboard shortcut via the terminal window instead of through the GUI? I guess this is also related to my second question: Where are the keyboard shortcuts (mappings) stored? I would appreciate any information. Thank you.[/FONT]

---

### Post by drs305 on 2007-05-16
I don't know about combinations, but individual keys can be remapped using xmodmap in terminal mode. The key codes for each key on your keyboard can be obtained by typing

```

xev

```

It places a small box on your screen and returns the codes for the keys you subsequently type. Learn more by typing 

```

man xmodmap
```

and 

```

man xev

```

As for where they are stored, I don't know the disk location but I have my single-key remaps appear in my System, Preferences, Sessions, Current Sessions after each boot of the computer.

---

### Post by azarath metrion zinthos on 2007-05-16
[FONT="Trebuchet MS"]Thanks for responding. Yeah, I know about individual key mappings. I mean keyboard events can be mapped to specific values, found in /include/linux/input.h. I was wondering if you could map certain events like "Open a Terminal" to a key combination as input.h did.[/FONT]

---

