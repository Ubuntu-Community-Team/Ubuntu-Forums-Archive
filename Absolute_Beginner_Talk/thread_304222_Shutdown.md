---
title: "Shutdown"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by captgadget on 2006-11-21
OK, I'm using a compaq Presario V4000 laptop with Ubuntu running on an external USB HD. Sometimes when I shut down and come back to restart it doesn't always start up properly. It gives me like a terminal screen and everything stops right there. Since I can't just turn the power off on the laptop I have to plug the power supply and then restart everything again. Then I have to restart in the recovery mode and the better choice for me there is the older of the two kernals. Of course the desktop is just flying by doing whatever it needs to do and until it gets to a point it makes repairs and then reboots. What am I doing wrong that this continues to go on?
 Sort of long but didn't know how else to tell my story.

Thanks

---

### Post by ajgreeny on 2006-11-21
If I understood your post properly, rather than just pull the plug, so to speak, when you get terminal mode sometimes, you should login as user with name and password as usual and then type "startx".  If that does nothing try "sudo shutdown -r now"

This will do a restart in the normal manner so hopefully it will then start with a GUI as you wanted in the first place.  If I didn't quite understand what you meant as your problem, apologies to you, but I assume that having to restart in recovery mode means that you just did a "power off" without shutting down as you should;  is that what you mean by "plug the power supply"?

---

### Post by captgadget on 2006-11-21
Thank you - I knew there had to be a better way - I just didn't know where to find it. I will sure try this the next time it happens.

---

### Post by yanqui on 2006-11-21
okay, so what do you do when the keyboard and mouse both freeze and nothing happens?  at that point, it's shut down by power button.

---

### Post by ajgreeny on 2006-11-21
I'm afraid so, yanqui.  If you can't get any input into your machine at all, then a power-off is all that's left to you.  Mind you, in linux that's not usually as bad as it is in windows.  Almost unknown to me in linux, however.

---

### Post by yanqui on 2006-11-21
It's happened to me several times today.

Ubuntu is going to have to get a lot btter than it is at this point if it wants ot live on my machine past february.

---

### Post by ajgreeny on 2006-11-22
What version of (K)ubuntu are you using?  Edgy is a bit more unstable than Dapper, which is what I use, and have not had any problems with lock-ups.  Perhaps it is simply a hardware incompatibility thing.

---

