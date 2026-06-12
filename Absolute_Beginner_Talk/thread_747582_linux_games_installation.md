---
title: "linux games installation"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Ketson on 2008-04-06
I've been browsing through synaptic trying to install some of the games on there to see what they are like the majority seem to disappear after I have installed them with noting showing in either the add/remove programs or the games. Synaptic is only giving me the choice to reinstall or remove as if has all been processed correctly.

Anyone know as to what has happened or how to correct this?

---

### Post by scragar on 2008-04-06
what games did you install?

---

### Post by wolfen69 on 2008-04-06
right click the menus and edit. you should be able to add the games there. or right click taskbar > +add to panel > application launcher

---

### Post by JoshuaRL on 2008-04-06
> **Ketson said:**
> I've been browsing through synaptic trying to install some of the games on there to see what they are like the majority seem to disappear after I have installed them with noting showing in either the add/remove programs or the games. Synaptic is only giving me the choice to reinstall or remove as if has all been processed correctly.

Anyone know as to what has happened or how to correct this?

Could you give me a name or two of some games you installed?  I'll give you a command in the terminal that will search for those games and see if they're there.  That way we'll see if they are installed.

> **wolfen69 said:**
> right click the menus and edit. you should be able to add the games there. or right click taskbar > +add to panel > application launcher

Another option, admittedly more involved, is Alacarte.

In the terminal type:
```

alacarte

```
and you can edit the menus, including adding icons.

---

### Post by Ketson on 2008-04-06
successfully
alien arena, barrage and flight gear
unsuccessfully
empire, overkill, rott and rocksanddiamonds

tried the edit menu idea but they were not there to add i'm afraid

---

### Post by JoshuaRL on 2008-04-06
Yeah, editing the menu with Alacarte means you need to put in the command to run the application.

But first, try this:
```

apt-cache search barrage

```
in the Terminal and post the output here.

---

### Post by Ketson on 2008-04-06
barrage - Rather violent action game
libbulletml-dev - C++ library to handle BulletML easily - development files
libbulletml0d1 - C++ library to handle BulletML easily - runtime library
rrootage - arcade-style space shooting game
torus-trooper - speeding ship sailing through barrage
torus-trooper-data - speeding ship sailing through barrage - game data

---

### Post by JoshuaRL on 2008-04-06
Now try to launch it from the Terminal and see what happens:
```

barrage

```

---

