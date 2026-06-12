---
title: "Programs Running in Terminal"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by zombie_killer on 2006-12-23
I have certain programs (such as nm-applet) that I execute from the command line.  How can I make it so that when I close the terminal, the application stays running?

Also, how do I make shortcuts in the menu for these programs so I don't need to start them from the terminal?

Thanks ahead of time.

---

### Post by kidders on 2006-12-23
Hi there,

You could try detaching the process from the terminal (add an ampersand at the end).

How you add things to menus depends on which graphical environment you're using. In any case, you should have a menu editor hiding someplace.

---

### Post by 3rdalbum on 2006-12-23
You can try:

```
nm-applet &
```

Sometimes, even programs that are started with an ampersand will still quit when the terminal is closed. For these programs, you should press Alt-F2 and type nm-applet, and hit Enter.

If you go to the menu, then System Tools, and "Applications Menu Editor", you will be able to add these commands to menu items. Alternatively, you can have them start up when Gnome does by going System > Preferences > Sessions and clicking the "Startup Programs" tab.

---

### Post by zombie_killer on 2006-12-23
Thanks a bunch, guys.  Exactly what I was looking for.  :)

---

