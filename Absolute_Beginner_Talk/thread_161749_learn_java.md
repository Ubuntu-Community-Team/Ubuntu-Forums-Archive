---
title: "learn java"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by m3t3ors on 2006-04-17
hiya, although ive tried other linux distros ive never really taken to it as ive found it rather hard to get to grips with!
now im trying to learn java or visual basic and although i have a windows machine i thought id give linux another go. ive just installed ubuntu (for the 1st time) and want to know if i can get java or visual basic for ubuntu and where from](*,)

---

### Post by unbuntu on 2006-04-17
Visual Basic is MS's, which can't be run natively on Linux.  Although there's something similar called "Gambas".  You can try it.  (Menu->Add Applications->Programming->More...->Gambas)

As for java, download the latest J2SDK1.5 from java.sun.com, install it and there you go.  If you want an IDE, Eclipse is always a favourite.  For learning purposes, you may want to try DrJava.  (drjava.sourceforge.net)

---

### Post by m3t3ors on 2006-04-17
thanx for the reply, ive just installed gambas and rebooted my pc but cant see how to open it up.? theres no mention of it in my application menus

---

### Post by unbuntu on 2006-04-17
[QUOTE=m3t3ors]thanx for the reply, ive just installed gambas and rebooted my pc but cant see how to open it up.? theres no mention of it in my application menus[/QUOTE]

I don't think you need to reboot...well...I've never tried Gambas, but I guess as all the programming tools are installed under Application->Programming, so should Gambas. (by the way, if you installed it correctly, normally Add Application will tell you where it puts the shortcut in the menu)

---

### Post by m3t3ors on 2006-04-17
yeh i thought it would have, but i havent got a programming  in my applications menu?
although its visable in applications>system tools>application menu editor
i still cant seem to do anything with it

---

### Post by unbuntu on 2006-04-17
[QUOTE=m3t3ors]yeh i thought it would have, but i havent got a programming  in my applications menu?[/QUOTE]

Then maybe you didn't have it installed correctly.  As I said, if you had installed it correctly through "Add Application", it will inform you where it puts Gambas in the menu once it's done.  Go to terminal, type
```

which gambas

```
see if any path comes up.  (note:  I guess the executable for Gambas is 'gambas' but not sure.  Checking back with "Add Application" may be your best bet)

---

