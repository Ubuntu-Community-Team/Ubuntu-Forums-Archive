---
title: "completely distroyed nautislaus and stuff with synaptic please help me"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by absol_of_doom on 2007-03-09
the worst thing i can imagine short of complete failure of my computer just happened. somehow, synaptic destroyed: terminal, synaptic itself, nautilus and files. how did this happen and can i fix it. i may sound like an idiot, but im in distress and im not thinking clearly...

---

### Post by Bachstelze on 2007-03-09
What did you do in Synaptic to break things that badly ?

---

### Post by absol_of_doom on 2007-03-09
i have no clue. i was just reinstalling gcc compiler with it and it removed almost everything but gnome and firefox.

---

### Post by Bachstelze on 2007-03-09
Move to a terminal with Ctrl+Alt+F2 and do

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by absol_of_doom on 2007-03-09
i tried but it said "cant find package ubuntu"





by the way: thanks for helping me, otherwise id be screwed

---

### Post by Bachstelze on 2007-03-09
It's *ubuntu-desktop*, not *ubuntu desktop* nor anything else ;)

---

### Post by absol_of_doom on 2007-03-09
yup. i screwed up and put ubuntu desktop...how'd you know?  its installing it. hope it works...

---

### Post by Bachstelze on 2007-03-09
Because apt-returned "package ubuntu does not exist", which means tht you typed *apt-get install ubuntu* or *apt-get install ubuntu somethingelse* so it was easy to guess that you just forgot the dash ;) Once the install is done, do

```
sudo /etc/init.d/gdm restart
```

to restart your GUI.

---

### Post by absol_of_doom on 2007-03-09
okay, it reinstalled, but my home folder has mysteriously disappeared

---

### Post by Bachstelze on 2007-03-09
Could you elaborate tht, please. What do you mean "it disappeared" ?

---

### Post by absol_of_doom on 2007-03-09
nevermind, it reappeared. THANK YOU SO MUCH FOR YOUR HELP :) :) :) :) 
i wont forget it.

---

