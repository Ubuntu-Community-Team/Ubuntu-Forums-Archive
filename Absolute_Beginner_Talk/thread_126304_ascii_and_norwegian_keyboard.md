---
title: "ascii and norwegian keyboard"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by JKJK on 2006-02-06
Hi! I'm a new user to ubuntu (have used slackware a bit before) and I wonder how to get ascii letters (example: alt+666) on norwegian keyboard setup. 

Can somebody give me a hint?

-J-

---

### Post by d4rk on 2006-02-06
I can\t get NOR letter eighter :(                  Sry for not havin a answer..   
Just trying make this questinon ending up in the light:) 

I dont even know how to play off mp3s in Linux. 
Let\s hope for an answer soon...

---

### Post by JKJK on 2006-02-06
I can get norwegian keyboard layout, but not with ascii......

---

### Post by d4rk on 2006-02-06
[QUOTE=JKJK]I can get norwegian keyboard layout, but not with ascii......[/QUOTE]

OK, do u get AA and lettters like that.. ??    U know what AA stands for, right ?

---

### Post by JKJK on 2006-02-06
like æøå?

yes ...

---

### Post by d4rk on 2006-02-06
[QUOTE=JKJK]like æøå?

yes ...[/QUOTE]


OK, i dont even get those... Ive tried almost everything..

EDIT: Ive found the solution for my problem, in my own post :D  It's highlighted for the time, but for aftertime:

LINK          [http://www.ubuntuforums.org/showthread.php?t=126369](http://www.ubuntuforums.org/showthread.php?t=126369)

---

### Post by JKJK on 2006-02-07
This is my config in xorg.conf

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "no"


.... but i still want my ascii-letters :cry:

---

### Post by JKJK on 2006-02-07
isnt' there anyone with some expericene to help here? (sorry for bumping).

---

