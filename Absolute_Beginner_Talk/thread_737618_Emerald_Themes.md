---
title: "Emerald Themes"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by m60dude5 on 2008-03-27
Hi. I recently installed Emerald Theme Manager. In order for the theme to load, I have to open a terminal and type emerald --replace. This works, except when I exit the terminal, the borders around my windows vanish. They;re gone until I reopen the terminal and type emerald --replace again. Then the theme comes back. In other words, how do I get the theme to stay applied, even after I exit the terminal. Thanks

---

### Post by i-am-me on 2008-03-27
When you type it in, does it look anything like this:
```
$emerald --replace

```
without ending again and starting a new line for a command? If that's what it is, its that the terminal process is running it in that command and exiting the terminal is the equivalent of hitting Ctrl-C aqnd killing emerald. I'm not really sure if that's a great explanation, but all you have to do is hit Alt-F2 to open the run dialog and type it in there. That should do it.

---

### Post by m60dude5 on 2008-03-27
That worked well. i just opened Alt F2 and typed it in there, and woohla. Thanks

---

### Post by iSplicer on 2008-03-27
Some more info:

What was happening when you ran that from the terminal, was that emerald was running IN the terminal, and was dependant on that process. If the terminal process in question was killed, so would all the dependant processes.

By running in alt+f2, you ran it normally, so there goes your problem!

---

### Post by m60dude5 on 2008-03-28
Thanks for the explanation. I was wondering why that happened. Thanks again.

---

### Post by sayakb on 2008-03-28
Goto System -> Preferences -> Sessions
Click on add. Type in the name as Emerald and the command as emerald --replace. This would start emerald each time automatically.

---

### Post by mrsudo on 2008-03-28
i was haveing the same problem for the longest time
:) all solved .... thanks LinuxIsInnovation

---

