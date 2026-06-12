---
title: "I think I just killed my gnome-terminal"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by shakajumbo on 2007-06-08
I was fiddling with the options, and I think I selected an option to close the window immediatly. Now whenever I open it, it closes down immediatly (guess that option works :D ). But now it dosent stay open long enough for me to right click it, get to properties, and change the setting. 

Any suggestions?

---

### Post by NeoLithium on 2007-06-08
Try alt+f2 and enter ```
gnome-terminal
```  Does it still close instantly?

---

### Post by diatribe on 2007-06-08
yea there is not an option to close it automatically when you open it ;p

---

### Post by shakajumbo on 2007-06-08
Sorry, this was my 1st post. Maybe I didn't word it clearly.  When you open gnome-terminal, right click on it, and goto properties. There is a tab entitled 'Title and Command'. At the bottom, there is an option to set: "When command exits" I selected 'exit terminal'.   

But thankfully I got the problem solved. What I did was, install another terminal.. tilda from the add remove list. Then ran "man gnome-terminal" and found a -x switch. This prompted the termianl to stay open waiting for me to enter a password. lol

I promptly undid the settings I made that screwed me.

w00t! 1st self created linux problem fixed :D


PS Thanks for the alt+F2 tip too!!

---

