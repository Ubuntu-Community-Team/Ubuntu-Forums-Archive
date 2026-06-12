---
title: "[SOLVED] Shortcuts for running programs?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by hait2 on 2007-11-25
I'm looking for a way to simplify the running of programs with alt+f2
for instance, to run calculator, i'd have to go alt+f2 and type in gcalctool, then hit enter

in windows this could be made easier by putting a shortcut in the windows folder and naming it whatever you want. so i could run firefox by win+r, ff (ff = name of firefox shortcut in windows folder), enter.

is there a way to customize the names of the programs in ubuntu in a similar manner (e.g. instead of gcalctool, a different string)?
thanks a lot~

---

### Post by annda on 2007-11-25
sure, for example you can create a symbolic link to gcalctool called calc in the directory where most binaries (or links to them) are stored:

```
sudo ln -s gcalctool /usr/bin/calc
```

---

### Post by philinux on 2007-11-25
Like in windows create a desktop shortcut.

right click anywhere and select create launcher, in command put your program name.

---

### Post by hait2 on 2007-11-25
thanks a lot ^_^!

---

