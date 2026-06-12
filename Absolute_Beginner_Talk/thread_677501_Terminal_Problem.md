---
title: "Terminal Problem"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by motion parallax on 2008-01-24
Two Questions:
After using certain commands in the terminal, like gedit, the cursor will move to a blank line and no longer process commands.  I can type, but when I press enter the cursor just moves to the next blank line.  Nothing happens.  

Couldn't get any info on forum search or google, but I may be using the wrong terminology.  

Also, when you Ctl-Alt-F1's, how do you get back to the GUI desktop?

---

### Post by Dylock on 2008-01-24
the termial is holding for that program you are running, if you want to open it without it tying up the termial throw in a & at the end of the command

ie: gedit &

give that a try.

---

### Post by FuturePilot on 2008-01-24
The reason why you can't enter anything else into the terminal when running something like Gedit is because the process is still running. If you would like to free the terminal to be able to enter more commands, run the command like this
```
gedit &
```
The & will free the terminal so you can enter more commands.
To get back to a GUI from a tty press Ctrl+Alt+F7.

---

### Post by motion parallax on 2008-01-24
Awesome.  Thank you.  Both commands worked.

---

### Post by mr_ed on 2008-01-24
Simply Alt+F7 will get you back to the GUI, too.  ;)

---

### Post by motion parallax on 2008-01-24
Even better.  Thanks!

---

