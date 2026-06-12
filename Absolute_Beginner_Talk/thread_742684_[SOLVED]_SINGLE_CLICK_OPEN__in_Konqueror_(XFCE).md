---
title: "[SOLVED] SINGLE CLICK OPEN  in Konqueror (XFCE)?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by viiv on 2008-04-01
Using XFCE & Gutsy, is there ANY way to turn off the Single-click open function in Konqueror?? I've searched and only found solutions for KDE... using the KDE control panel or something. Any XFCE users out there know of a solution?

---

### Post by kerry_s on 2008-04-01
huh? xfce4 uses thunar, not konqueror.

---

### Post by Whiffle on 2008-04-01
~/.kde/share/config/kdeglobals

Change
SingleClick=true

to 
SingleClick=false



(i think)

---

### Post by viiv on 2008-04-02
Hey Whiffle
Thanks! It worked.
Funny tho, there was no actual entry for  *SingleClick=true* in the config file
I'm not kidding. Strange.
Anyway, I just made a guess and added the line (with FALSE) and it worked.
I've included it below for anyone else who might need to know.

Thanks again!


```

[KDE]
ShowDeleteCommand=false
SingleClick=false
```

---

### Post by viiv on 2008-04-02
Kerry_S
You're right. I just prefer Konqueror. It does a lot that Thunar doesn't

---

