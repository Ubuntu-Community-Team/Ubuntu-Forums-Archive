---
title: "Swap Command/Control on 15.04?"
date: 2015-07-13
forum: Apple Hardware Users
---

### Post by mcoyle on 2015-07-13
Ok, this is sorta silly because in the past it was an easy preference setting, but in Ubuntu 15.04 I cannot find a way to swap the Command and Control keys!

Previously, I had a 15.04 install that was upgraded going all the way back to 12.04, so whichever control panel let me swap the keys just got carried along.

That hard drive crashed and I started over with a fresh install of 15.04 and I can no longer swap those keys.

Any help would be appreciated.


Michael

---

### Post by pindar on 2015-07-21
Yes, this has been made more difficult in recent versions of Gnome and Unity - supposedly, they want users to concentrate on their real task (admire the sleek graphics) and not fiddle with their keyboard settings... Anyway: you can make the change from the command line. The command would be
```
setxkbmap -option 'altwin:swap_alt_win'
```
If you don't want to type (and have to remember) this whole thing, save the command to a file, call it something like "myawesomekeyboard.sh" and call it from a terminal with 
```
sh myawesomekeyboard.sh
```

---

### Post by mcoyle on 2015-08-19
Thanks Pindar. Luckily, I found a GUI solution. After installing Gnome Tweak Tool, I found a setting under "Typing" to map the Alt/Win keys to Control.

---

