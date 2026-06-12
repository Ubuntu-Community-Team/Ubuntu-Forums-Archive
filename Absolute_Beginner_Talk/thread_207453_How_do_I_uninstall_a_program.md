---
title: "How do I uninstall a program?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Dusk2k2 on 2006-07-01
I just installed Audacious from the package.  How do I go about uninstalling it now?

I also have Wolfenstein installed as well and would like to uninstall it.  Any help?

---

### Post by joshrobinson on 2006-07-01
[QUOTE=Dusk2k2]I just installed Audacious from the package.  How do I go about uninstalling it now?

I also have Wolfenstein installed as well and would like to uninstall it.  Any help?[/QUOTE]

if you installed it as a package you can open up synaptic and search for it, it should let you remove it from there

---

### Post by Dusk2k2 on 2006-07-01
I meant I installed it as a deb package.  It doesn't appear in synaptic.

---

### Post by Jessehk on 2006-07-01
```

sudo aptitude remove *package-name*

```

---

### Post by Dusk2k2 on 2006-07-01
Ah, thats it, Thanks a lot.

---

### Post by joshrobinson on 2006-07-01
maybe im losing my mind.. but i sware ive installed a package from a .deb file and have had it show up in synaptic.. yeah probibly losing my mind

---

### Post by user1397 on 2006-07-01
[quote=joshrobinson]maybe im losing my mind.. but i sware ive installed a package from a .deb file and have had it show up in synaptic.. yeah probibly losing my mind[/quote]nope, you haven't lost your mind, it has happened to me too. i, however, am already completely insane anyways!

---

### Post by joshrobinson on 2006-07-01
[QUOTE=erik1397]nope, you haven't lost your mind, it has happened to me too. i, however, am already completely insane anyways![/QUOTE]

we might both be insane.. at least im not alone

---

### Post by someusernoob on 2006-07-02
You probably installed Wolfenstein ET with a .run file? If yes, you have to manually remove it:

Check with nautilus if it is in here: /usr/local/games/enemy-territory

if so, type:
```

sudo rm -R /usr/local/games/enemy-territory

```

Otherwise change the dir name to the one you installed it in (this is the default dir).

Then remove your savegames and configuration:
```

rm -R .etwolf

```

And remove the menu shortcut with Applications > Acc. > Alacarte Menu Editor.

---

