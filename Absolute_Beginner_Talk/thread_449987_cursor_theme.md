---
title: "cursor theme"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-05-20
i know its a n00bish question, but how do i install cursor themes for my version?
is there a gui i can use or do i use a cmd line?
please help me

---

### Post by starcraft.man on 2007-05-20
Did a quick search of the forums, ya should remember to try before posting often its been solved before you :).

All you need is to install gcursor from the terminal.

```
sudo aptitude install gcursor
```

Then you open it (can also do that via terminal, just type in "gcursor") and you can import the theme from the archive I guess.

Have fun with themes :D.

---

### Post by pbw on 2007-05-20
There's a bunch in repos already, just apt-cache search cursor | less, and sudo apt-get install what you want. you can set the cursor theme from within gnome (which i assume you're running) under preferences, kde from within kcontrol and .Xdefaults/.Xresources from cli.

-- pbw

---

### Post by 99bluefoxx on 2007-05-20
allright
thanks for the help

---

