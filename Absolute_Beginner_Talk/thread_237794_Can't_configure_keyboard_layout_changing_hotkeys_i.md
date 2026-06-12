---
title: "Can't configure keyboard layout changing hotkeys in Kubuntu"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by VictorGavrish on 2006-08-16
I installed Kubuntu on top of Ubuntu. I added the icon to switch layouts to tray and it works fine when you click it, but I want to configure a keyboard shortcut. When I right-click the icon and select configure > xkb options > enable > group shift/lock behaviour and select a shortcut, nothing happens. Am I doing something wrong?

---

### Post by LadyDoor on 2006-08-18
Here's a cross-platform way to do it!

First, install xbindkeys and xkbutils.

```
sudo aptitude install xbindkeys xkbutils
```

Then, add the following lines to a file called **~/.xbindkeysrc** using your favorite text editor (replacing the keyboard shortcuts with the ones you want and the languages with the ones you want--for more information on the languages you can choose from, type **man setxkbmap**.

```

"setxkbmap es"
  control + Mod4 + e
"setxkbmap us"
  control + Mod4 + u

```

If you've modified any keys with xmodmap and want to keep them that way, enter these lines *instead* (assuming your .Xmodmap file is ~/.Xmodmap

```

"setxkbmap es && xmodmap ~/.Xmodmap"
  control + Mod4 + e
"setxkbmap us && xmodmap ~/.Xmodmap"
  control + Mod4 + u

```

Then, in a terminal, enter the following line:

```
$ xbindkeys
```

I'm not familiar with KDE, so I don't know how to automatically load programs on startup, but I'm sure you can find a way! Let me know if this works!

--Door

---

