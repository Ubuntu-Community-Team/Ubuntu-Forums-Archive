---
title: "Sound sporatic- need to restart"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by saltsoda on 2008-03-09
hi, 
i'm brand new to ubuntu and linux in general. 
assume i know nothing. 

i have a problem when i start my computer sometimes i do not have sound. the sound will come back on again if i restart 1-3 times. this is a major problem! 

thanks in advance.

---

### Post by nowshining on 2008-03-09
What are u running?

Ubuntu - Gnome
Kubuntu - KDE, etc..

---

### Post by Dave Otter on 2008-03-09
What soundcard do you have?

---

### Post by drewcoon on 2008-03-09
Try opening a terminal and typing
```
killall esd
```
It's often a quick fix to sound problems (It restarts the sound server), although it likely won't solve whatever underlying problem is causing your sound to not work properly.

---

### Post by Dave Otter on 2008-03-09
Applications--Accessories-terminal

   type in asoundconf list

    post output

---

