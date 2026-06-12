---
title: "Fluxbox which file browser?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Scarath on 2007-10-28
Hi,
I have been using ubuntu with gnome for a while but wanted a more minimal desktop, so i got fluxbox and its great  apart from a things that i cannot find the answer for in any of the documentation.

i have read lots of docs and lots of posts of flux but i cant find these simple answers.

1. Does Fluxbox have a file browser (like nautilus or thunar) as standard?
2. If not if their one that will run in fluxbox.
3. I tried to make F12 my shortcut to the xterminal in fluxbox but it didnt work (i did it using the key file in the fluxbox folder), is there a preset shortcut to the terminal in flux? 

thanks

---

### Post by kerry_s on 2007-10-28
> **Scarath said:**
> Hi,
I have been using ubuntu with gnome for a while but wanted a more minimal desktop, so i got fluxbox and its great  apart from a things that i cannot find the answer for in any of the documentation.

i have read lots of docs and lots of posts of flux but i cant find these simple answers.

1. Does Fluxbox have a file browser (like nautilus or thunar) as standard?
2. If not if their one that will run in fluxbox.
3. I tried to make F12 my shortcut to the xterminal in fluxbox but it didnt work (i did it using the key file in the fluxbox folder), is there a preset shortcut to the terminal in flux? 

thanks

1. no, any file browser will work, you can use both nautilus or thunar, there are many to choose from, just use the 1 you like.
2. see 1
3. what did you put? (None F12 :Exec xterm)

---

### Post by raul_ on 2007-10-28
my vote goes to pcmanfm

keep in mind tht it doesn't have a trash folder and that if you accidentally press delete without selecting anything, the entire folder is deleted

---

### Post by Scarath on 2007-10-28
thanks for the help

When i tried nautilus my fluxbox when mad and turned into some sort of flux/gnome monster lol
I will try thunar and pcmanfm and see which works best. 

@kerry = i changed the text file in the fluxbox file but did it wrong >.< will re-try with what you wrote.

---

### Post by spupy on 2007-10-28
I personaly use Rox with fluxbox (i call it fluxrox :)); it's different from other file browsers, but have some rare and nice features. It can also give you a lightweigth desktop with icons, in which case it will be even faster.
When you open nautilus, it tries to display the gnome desktop. You need to invoke nautilus like that:
```
nautilus --no-desktop
```
PCmanfm was too bloatet for my minimal desktop, so i use ROX and sometimes thunar.

---

