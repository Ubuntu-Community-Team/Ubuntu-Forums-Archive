---
title: "key sequence control-a s locks terminal (using screen)"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2006-09-20
I keep locking my terminal becuase I am using screen. I have to press control -a then either p or n (for previous screen and next screen respectively) but sometimes I accidentally press s. The s key is right next to a, so this happens often, where I press the key sequence I have explained, and the terminal locks up. 
I do not know how to unlock it once it is locked.

Any help, incite, advice is appreciated!

---

### Post by deadgobby on 2006-09-20
Do you mean when the terminal is lock, that is stuck and you cannot close it?
You can use ctrl + C and see that will kick back unstuck. Or my fav
cntrl = f2 
it opens up a window and you type in xkill. Your mouse courser turns into a xbones and you click on the window. Pooof it is all gone.

---

### Post by mdecler2 on 2006-09-20
No. I just want to unlock it. I can bone the terminal easily. I just want to recover my screen session.

I tried openning a new terminal and doing a ```
screen -dr <screen#>
```
but that just hangs for a whil and does nothing.

The screen session still exists, and says it is attached, but for some reason I cannot remote detach it when it is  "locked" by the key sequence.

---

### Post by mdecler2 on 2006-09-20
It is not even technically a screen "lock" either, control-a control-x really does lock the screen and ask you for a password. What I mean is the screen just "hangs," and what I mean by that is it displays exactly what it was displaying at the time of the key sequence in question, but is completely unresponsive.

---

