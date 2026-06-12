---
title: "Sound issues"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-12
When I am using any of the desktop enviroments my sound works perfectly. When I play any type of game I get no sound what so ever it is driving me nuts...

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=CookieOrc]When I am using any of the desktop enviroments my sound works perfectly. When I play any type of game I get no sound what so ever it is driving me nuts...[/QUOTE]
If you use one sound system for the desktop, and another for the game, the desktop sound system could be hogging the sound device.

Many times, this means you use esd for the desktop and alsa for the game.
Try:
```

$ sudo killall esd

```
That will kill desktop sound and you can try the game.
If you need to restart it
```

$ esd&

```
Some game libraries can be made to use the same sound system as your desktop by creating config files in your home directory.

---

### Post by CookieOrc on 2006-02-13
When I do the sudo kill esd it says 
> esd: no process killed

This is what happens when i try to run
```
cookieorc@LinuxBox:/$ esd$
bash: esd$: command not found

```

---

