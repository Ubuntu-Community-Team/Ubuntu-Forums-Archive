---
title: "Help!!!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by mmikelst on 2007-04-21
I've somehow managed to get rid of the taskbars...I just recently (10 minutes ago) installed Beryl and now my taskbars have gone AWOL. Does anyone know what I've done/how to fix it???

---

### Post by Campingman on 2007-04-21
You should be able to add new panels, right click menu includes add new panel and then if you right click on the new panel you can add items to it.  If they have just been deleted this should get you back to where you started.

---

### Post by mmikelst on 2007-04-21
When I right click on my desktop it just gives me the "create folder, create launcher, create document" etc. options...No place for new panels:(:(

---

### Post by bobplano on 2007-04-21
> **Campingman said:**
> You should be able to add new panels, right click menu includes add new panel and then if you right click on the new panel you can add items to it.
they don't have the bars to click on. i don't have beryl but this seems to be a fairly common problem. i think it had to do with editing some file that controls beryl. forum search should be helpful

---

### Post by Campingman on 2007-04-21
Sorry you are right yes, you have to click on a panel to get the option to add a new panel.  If you enter gconf-editor in the terminal and then go to apps/panel/toplevels are the panels showed there? if they are there may be something listed that will give you a clue as to where they have gone

---

### Post by bobplano on 2007-04-21
well there was another post about missing taskbars (it was about xubuntu so i don't know the exact command). press ctrl+alt+f2 to get to a terminal and type in something like 
```
gnome-panel
or
kde-panel
```

wel the basic format was *desktop enviroment*-panel and then press ctrl+alt+f7 to get back to your desktop

---

### Post by mmikelst on 2007-04-21
Yeah, I switched to gnome managing the panels, shut down, restarted and everything was dandy. Guess restarting does fix everything:) Thanks for the help!

---

