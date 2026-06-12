---
title: "Run evolution in background?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-11-22
Is there a way I can have evolution start at startup and alert me to new messages all day, while at the same time not being open in a menu. (Kind of like how Amarok can play after the window is closed)

---

### Post by rahimveron on 2007-11-22
Maybe the option "Close Window" under File Menu does the background checking of mails, though i am not sure.

---

### Post by el escocés on 2007-11-22
install alltray

```
sudo aptitude install alltray
```

then in terminal launch

```
alltray evolution &
disown
```

this will launch evolution but keep in minimized in the menu bar, click to hide/show just like amorak.

then if you like it you can either edit your evolution launcher in the menu (right-click menu -> edit menus -> right-click evolution -> properties) simply type alltray in front of the command, leaving a space between the two words and close it.

another way is to run evolution on startup, System -> Preferences -> Sessions, there you can add a launcher for evolution using alltray.

I also use alltray to clean up my menu bar, you can use it with firefox also.  very handy!

---

### Post by Romanus81 on 2007-11-22
Thank you so much, this is exactly what I needed!

---

### Post by Jumpmasterrt on 2007-11-23
Wow! That's awesome. I'm so going to do that when I get home.

---

### Post by Jumpmasterrt on 2007-11-23
Worked like a charm....

---

