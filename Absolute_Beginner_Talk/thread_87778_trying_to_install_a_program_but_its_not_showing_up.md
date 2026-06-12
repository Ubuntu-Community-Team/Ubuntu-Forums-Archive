---
title: "trying to install a program but its not showing up"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2005-11-08
I am trying to install a pong like game. I used synaptic and searched pong. I found a couple and installed them but they are not showing up under my games. :confused:

---

### Post by uby on 2005-11-08
Can you launch it from the terminal?

---

### Post by Samuel on 2005-11-08
did you try restarting the gnome panel?```
killall gnome-panel
``` if they still dont show up you can use the menu editor (applications>system>applications menu editor) to add a launcher to the menu, if your not sure where the game went use ```
locate <application name>
``` to find where its installed.

i had to do the same with zsnes yesterday, the app was in /usr/bin and the icon was in /usr/share/pixmaps/

hope this helps

hope that helps, i had to do the same for zsnes yesterday,

---

### Post by briguy on 2005-11-08
look under /usr/games

---

