---
title: "wine issues"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-28
I got this message when I ran winecfg
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

when I tried to "add" one and hit apply it still is not there,I even went to the synaptics and uninstalled, completely removed,and reinstalled wine....still the same message! What should I do?

---

### Post by trent dillman on 2006-03-28
If you are just starting to use wine, delete your ~/.wine folder. If not, move it and see if that helps.

---

### Post by wolfee on 2006-03-28
[QUOTE=trent dillman]If you are just starting to use wine, delete your ~/.wine folder. If not, move it and see if that helps.[/QUOTE]
how do I delet it?
Also when I click on drives I get a warning saying "you don't have a drive c this is not so great remember to click add to the drivers menue to creat one" when I do this it still does not work

---

### Post by trent dillman on 2006-03-28
Open a terminal, then

```
rm -r ~/.wine
```

But if you already have programs installed in wine, they will be gone forever.

---

### Post by wolfee on 2006-03-28
[QUOTE=trent dillman]Open a terminal, then

```
rm -r ~/.wine
```

But if you already have programs installed in wine, they will be gone forever.[/QUOTE]
 Beautiful!!!! It worked!!!! Plus when I typed winecfg it must have reinstalled it!!!
Thanx Trent you ROCK!!!!

---

### Post by trent dillman on 2006-03-28
No problem. Welcome to Ubuntu!

---

