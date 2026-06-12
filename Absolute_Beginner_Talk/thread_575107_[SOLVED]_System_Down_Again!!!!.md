---
title: "[SOLVED] System Down Again!!!!"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by michiel.patrick on 2007-10-13
As bad as i want to say Linux is unstable ... I know this is my fault for trying to customize everything and now i think i have finally done it. The last things i did to the system was to place a terminal onto the desktop background. I also changed the login and splash screen. After this, when i rebooted it had a long error message saying something along the lines of: your session lasted less than 10 seconds. I am given an ok button and when i press it the system goes back to the login screen. Any ideas? I tried to copy the whole error code but it wouldn't let me.

---

### Post by oilchangeguy on 2007-10-13
sounds like it's time to do a re-install.

---

### Post by kellemes on 2007-10-13
You get this message everytime starting the system?

---

### Post by michiel.patrick on 2007-10-13
ya after messing with a few things today

---

### Post by michiel.patrick on 2007-10-14
does anyone have any ideas? I am in XP right now and it has been pure torture. I would much rather use linux! If only i had a good answer for Visual Studio then I would need windows no more!

---

### Post by kellemes on 2007-10-14
Assuming you're on Gnome.. You could try deleting your Gnome sessionfile, maybe there is crap in there? It should be at ~/.gnome2/gnome-session

Edit: If this doesn't work..It could also be video-related, you changed something with your videodriver or something?

---

### Post by philinux on 2007-10-14
+1 the above poster. The error message will tell you which files are causing the problem. There's no need to reinstall

---

### Post by sailor2001 on 2007-10-14
gnome2 is a hidden file...in your home folder: ctrl/h

---

### Post by cowkiller on 2007-10-14
> **michiel.patrick said:**
> does anyone have any ideas? I am in XP right now and it has been pure torture. I would much rather use linux! If only i had a good answer for Visual Studio then I would need windows no more!

I'll cross fingers for that answer for Visual Studio. I hope that the Mono project can do something about it.

---

### Post by Capricori on 2007-10-14
I got this error a few times... 
As far as I could tell, because I'd filled up the root partition, or messed with permissions and locked myself out of my home directory.... don't ask me how :)
Could either of these be the cause?
Also, I'm using Mono for C# programming with no problems :) Hopefully it can do the same for you.

---

### Post by michiel.patrick on 2007-10-14
i will see what i can do... thanks guys

---

