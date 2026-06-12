---
title: "Keyboard works fine... until KDE loads up my admin user account."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Rellin on 2007-10-27
I just had my first problem with gutsy.  I was playing around with Compiz-KDE and trying to set it up.  All of a sudden, my keyboard just stopped working.  I managed to copy/paste in my admin password character-by-character to create a new account.  I log onto that and the keyboard works fine!

I've looked around but havn't found any solutions.  Any suggestions would be greatly appreciated.

---

### Post by Rellin on 2007-10-28
(bump)

---

### Post by haldean on 2007-10-28
hiya! what were you doing? have you tried modifying the keyboard settings in your root account?

---

### Post by Rellin on 2007-10-28
Yeah, I tried uninstalling all of the compiz-kde packages and changing up or reapplying my keyboard settings.  

It must have something to do with a setting on my admin account because on the new user account I created, it works fine.

---

### Post by Rellin on 2007-10-28
(bump again)

---

### Post by Rellin on 2007-10-28
(triple bump)

---

### Post by Rellin on 2007-10-28
(m m m m monster bump bump bump)

---

### Post by Rellin on 2007-10-28
(ultra bump)

---

### Post by haldean on 2007-10-28
the bumping isn't necessary ;) not fun to sit down at your computer to have 5 emails telling you to check this thread :S

did you try changing around your keyboard settings while you were logged in as root? 

also: try typing this into a terminal and see if it gives any output:
```
ls -la ~root | grep -i xmodmap
```

---

### Post by Rellin on 2007-10-28
found the solution.  sorry for the spam.  its a KDE "feature" called Slow Keys that I had to turn off in the Accessibility settings.

---

