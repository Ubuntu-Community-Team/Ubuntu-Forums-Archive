---
title: "Stuck without mouse and keyboard"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by Paul_Janus_Finnegan on 2006-02-11
Please help me,
I´m stuck at the desktop without mouse and the keyboard allows me only to change between (empty) screens or going back to the login screen.
Where can I find the keyboard shortcuts to open a menue or start a program or reconfigure my serial mouse so I can use it. Nothing works, the whole two hour automatic installation was useless until someone can help me find a way to configure my mouse. Please help me.

Greetings
Paul

---

### Post by christhemonkey on 2006-02-11
Can you go to a terminal for us please?
(Ctrl+Alt+F1)
Then type
```
sudo dpkg-reconfigure xserver-xorg
```
then later on when its asking questions about mice, on the input port,
select ttyS0
Try to get the rest of the settings right! 
And then select save later on.

---

### Post by Paul_Janus_Finnegan on 2006-02-11
Woah! That helped. Thank you for this line worth to remember. But still: Are the keyboard shortcuts to navigate on the desktop, just in case my mouse fails in an unrecoverable way?
Thanks again for this very fast reply.

Greetings,
Paul

---

### Post by christhemonkey on 2006-02-11
Yeah, these would be good for me too actually, like in windoze when you press alt to get onto menus and stuff.
Ctrl+ALt+Del restarts, but that can get annoying!

---

### Post by christhemonkey on 2006-02-12
But it is possible to change the action of Ctrl+Alt+Del, but thats off the point.

---

