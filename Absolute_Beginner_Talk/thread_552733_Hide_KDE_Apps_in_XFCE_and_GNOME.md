---
title: "Hide KDE Apps in XFCE and GNOME?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by eduardounder on 2007-09-16
Somone now how can I hide then in XFCE/GNOME at same time?

The KDE Apps are already using 'ShowOnlyIn=KDE' and Gnome isnt showing but XFCE is appears to be ignoring it..

I am using 3 DE because..
Gnome - default.. 
XFCE - works most time faster than gnome and still looks good.
KDE - has better apps but looks awful.. (I couldnt install a style and a window deco. If someone can help me with that too..)

Thanks in advance,

---

### Post by capink on 2007-09-20
I think you have it wrong in your *.desktop files. It should look as follows:

```
OnlyShowIn=KDE;
```

Notice the semicolon at the end. Try Replacing the old ShowOnlyIn=KDE with suggested string and it should work in xfce.

---

### Post by Jaymac on 2007-09-24
Don't think you need the semicolon, at least, I don't use it and it works fine for me, but the line I use (in common with previous poster) is:

```
OnlyShowIn=KDE
```

as opposed to ShowOnlyIn...

---

