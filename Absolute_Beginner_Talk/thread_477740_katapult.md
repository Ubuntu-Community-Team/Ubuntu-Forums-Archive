---
title: "katapult?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-06-18
What does katapult do? Does anyone know? Its conflicting with my Beagle shortcut key, can I remove it?

---

### Post by Gavin77 on 2007-06-18
From man page:
> DESCRIPTION
       Katapult is a KDE laucher.

       It  uses text-based queries to launch a program, a bookmark or a direc&#8208;
       tory.


---

### Post by Jucato on 2007-06-18
Katapult is a launcher, ala Quicksilver on OS X. Basically you press Alt+Space and type in a few letter of a Program, a document, a playlist item (Amarok), a bookmark, etc. to launch it. you can even type in numbers for calculations (recognizes parentheses and ^ for exponents).

The shortcut key for Katapult can be changed, but since it already conflicts with Beagle (who also uses Alt+Space), you have to use this command to show Katapult. Press Alt+F2 and type

```
dcop katapult Katapult showLauncher
```

then once the Katapult launcher shows up, press Ctrl+C to popup the configuration menu and select Configure Global Shortcuts.

---

### Post by Butthead on 2007-06-18
Wow, that's pretty cool!  I brought it up accidentally a few times, but didn't know what it did.  Thanks for the useage explanation! :KS

---

