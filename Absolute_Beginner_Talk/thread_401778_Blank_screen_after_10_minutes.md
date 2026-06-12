---
title: "Blank screen after 10 minutes"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-04-05
Any idea why my screen blanks after 10 minutes of idleness even when my gconf and power management both say never? I can't get it to stop blanking. 

I should also add that my screensaver never gets a chance to come on.

---

### Post by mssever on 2007-04-05
Xorg is probably to blame. It keeps its screen blanking settings separately. A quick Google search revealed [this site]("http://www.shallowsky.com/linux/x-screen-blanking.html"). Hopefully it'll be helpful.

---

### Post by shanepardue on 2007-04-13
For some reason xset outputs "xset:  unable to open display" on my XGL machine. I was able to use 
it on a different computer that isn't running XGL. I'm assuming XGL throws this method off. 

I've also put the following into the xorg.conf and it gets rid of the blanking, but doesn't allow for the 
monitor to ever turn off and the screensaver always looks funky so I need a different method.

```
Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```

---

### Post by mssever on 2007-04-13
> **shanepardue said:**
> I've also put the following into the xorg.conf and it gets rid of the blanking, but doesn't allow for the 
monitor to ever turn off and the screensaver always looks funky so I need a different method.

```
Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```
How about adjusting those times to be what you want?

---

### Post by shanepardue on 2007-04-13
Yeah, I've done that..and none of them work when set for a specific time.

---

### Post by shanepardue on 2007-04-13
"xset s noblank" prevents blanking, but also prevents my monitor from powering off.

I'm finding that when i disable blanking, I am also disabling the monitor from powering off 
automatically. I'm looking for a way to have my monitor power off after about 30 minutes, but my 
screensaver to go til then.

---

### Post by Mana82 on 2007-04-14
hey i have the same problem and i think the info in this thread will help fix it, but what i want to know is that if i set it to say 30 minutes, will it still kick in if say i am watching a movie in vlc and if so, is there anyway to get around this?

---

### Post by forrestcupp on 2007-04-14
Here's a real silly question.  Are you sure your screensaver isn't set to just have a blank screen?  If it isn't set to something else, maybe it actually is your screensaver.  Blank screen is the default.  I know that's obvious, but sometimes people overlook the obvious.

---

### Post by mssever on 2007-04-15
> **Mana82 said:**
> hey i have the same problem and i think the info in this thread will help fix it, but what i want to know is that if i set it to say 30 minutes, will it still kick in if say i am watching a movie in vlc and if so, is there anyway to get around this?

The screensaver seems to come on even when I'm doing something like watching a movie. Apparently, it doesn't know to disable itself. However, if you install brightside (I think that it's in the universe repository), you can configure a screen corner that you can put your mouse in that will disable your screensaver while it's there.

---

### Post by shanepardue on 2007-04-22
I was unable to fix this situation while still using XGL and XGL is more important to me than having a working screensaver without blanking every 10 minutes. I guess I've prioritized.

---

