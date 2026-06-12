---
title: "X lock up dapper 6.06?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by n0dl on 2006-11-19
Lately ive been having this strange problem in X where everything seems to lock up. I do not have any keyboard control but i can still move my mouse around and conky (my system monitor) is still actively running. This happens whenever I run firefox or a terminal as soon as i boot (or even a few seconds later). I tried looking through my logs but they dont tell me anything. Anyone know what might be going on? Im on Dapper 6.06 and my videocard is a 950 graphics media accelerator (intel). I use openbox 3.31 (compiled from source)

---

### Post by .t. on 2006-11-19
Does anything happen when you run firefox in a terminal? Or anything in ~/.xsession-errors?

---

### Post by n0dl on 2006-11-19
Well since my keyboard seemed to lock up there was no way to terminate X therefore no .xsession-error file was created. The problem only seems to occur when i start up firefox using a keybind i set in openbox as soon as i start X. This problem also occured when i used fluxbox as well

---

