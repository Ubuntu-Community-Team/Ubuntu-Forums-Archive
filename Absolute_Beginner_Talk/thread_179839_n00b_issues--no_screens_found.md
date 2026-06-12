---
title: "n00b issues--no screens found"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by durableapostle on 2006-05-20
Help!!

In the process of trying to reconfigure the screen resolution (which I still have to do), I jacked someting up.  I'm now in a "DOS-like" screen that I cannot escape from.

Is there a command to restore to the previous settings--before I screwed it all up?

I'm going crazy here.  Any help is appreciated....

---

### Post by macdo on 2006-05-20
Try running ```
sudo dpkg-reconfigure xserver-xorg
```
Choose the vesa driver option, normally. You can choose your screen resolution with that too.

---

### Post by Sef on 2006-05-20
1) Did you back up your settings?

2) What did you do specifically?

---

### Post by kaamos on 2006-05-20
This should generate the default settings:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```
You can leave out "-phigh" to make changes to the settings.

Hope this helps!

---

### Post by durableapostle on 2006-05-20
yeah.  this worked--what a relief.

---

### Post by durableapostle on 2006-05-20
I ran an update, and it somehow changed settings somewhere---not sure

---

