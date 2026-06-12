---
title: "just installed mplayer and amsn, but don't see them on application"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by henry8596 on 2007-05-29
i have just installed mplayer and amsn
but i cannot find them under application
i have already restarted my computer and still don't find them
is there any way to check if i have installed?
or i need to do sth to make them appear under appllication?

---

### Post by seshomaru samma on 2007-05-29
open a terminal and run:
```
amsn
```
or```

mplayer
```
there is a way to add them to the gnome menu , but i forgot
it's an application called alacarte or something

---

### Post by Tux Aubrey on 2007-05-29
alacarte is now called "Main Menu"  ie.  System>Preferences>Main Menu

You can add them there (but its weird they didn't show up automagically)

---

### Post by henry8596 on 2007-05-29
thx for the reply

i run   mplayer in the terminal and it shows the detail of it
can i then assume it is installed already?
but i go to menu layout, and i still cannot find mplayer

---

### Post by zvacet on 2007-05-29
**system>preferences>main menu>sound&video>new item**

This will create laucher and put this in it

1.name = mplayer
2. command = /usr/bin/mplayer
3. icon = usr/share/pixmaps

---

