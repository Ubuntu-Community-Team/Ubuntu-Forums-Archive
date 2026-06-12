---
title: "What is the name of the app that kills..."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-15
What is the name of the app that kills frozen programs? I've looked through Synaptic, possibly overlooking it, and I can't remember its name. Appreciate any help here.
kh

---

### Post by taurus on 2007-03-15
You mean you want to kill a dead app.  Open a terminal and see what is the PID (first column) is. 

```
ps -A
```
Then, kill it with, asusming it PID is 1234

```
sudo kill -9 1234
```

---

### Post by Aliarse on 2007-03-15
Hmm, are you talking about force quit?

Right click on your gnome panel > add to panel > Force quit, thats all i've ever used, and works fine for me.

---

### Post by kittyhawk63 on 2007-03-15
No, there is a small app that you can place its icon on the taskbar and click on it and then on the frozen program. It will immediately close the frozen program. Thanks for the suggestion, however.
kh

---

### Post by kittyhawk63 on 2007-03-15
[Aliarse]("http://ubuntuforums.org/member.php?u=197062")
That's it. Thanks.

---

### Post by SendDerek on 2007-03-15
There's always this method too:

Alt+F2 and then type "xkill" then you may click on the window that you want to kill...

---

