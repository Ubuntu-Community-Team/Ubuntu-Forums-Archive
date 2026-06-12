---
title: "crystal window manager"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-02-13
well i just installed the crystal window manager and really like it.  but i screwed up and put it on a clean mode...now i dont have any menus and i cant figure out how to get it back to the way it was originally.  any help is much appreciated.  thank you

---

### Post by sardion on 2007-02-13
I can't swear this will work but I would guess that the easiest thing to do is look for files/folders called .crystal in your home folder (or maybe in .fvwm) and remove them.  These are the config files for your setup so if you remove them it should default back.

---

### Post by dragnazz5.0 on 2007-02-13
i didnt mean to remove crystal.  i selected an option that takes all menus off the desktop...and i guess you have to run everything through terminal...but i dont know the commands.  sorry for the confusion

---

### Post by sardion on 2007-02-13
Not knowing how crystal works I can't tell you for sure, but if you open a terminal (or switch to consolve by typing ctrl-alt-F3) and do:

cd .fvwm
ls

you will see a list of all the config files for crystal.  at that point either edit them and try to fix it or just remove them all:

rm -fr ~/.fvwm

which will not remove crystal but will delete all of its settings.

---

### Post by dragnazz5.0 on 2007-02-14
does anyone have any idea on how to get back to the original setup from the clean mode?  ive searched but nothing is very helpful.

---

