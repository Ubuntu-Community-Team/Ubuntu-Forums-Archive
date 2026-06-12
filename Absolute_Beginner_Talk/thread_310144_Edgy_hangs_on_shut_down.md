---
title: "Edgy hangs on shut down"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-11-30
Having made the move from XP to Ubuntu today, I installed Edgy in my works PC and it worked perfectly. But, when I turn of the computer the new Ubuntu logo ramains on screen and stays there and I have to switch off power to be able to shut down the PC.  When I restart, everything works normally and without problems until it comes to turning off the PC once again and the same thing happens.  Is this how Edgy is supposed to work, I can't imagine so?  Perhaps someone has a fix?

---

### Post by LLRNR on 2006-11-30
Try putting this in a terminal:
```
sudo shutdown -hv now
```

The **-v** switch is for verbose output, so it'll show you what happens at shutdown time.

LLRNR

---

### Post by a.v.l on 2006-12-01
> **LLRNR said:**
> Try putting this in a terminal:
```
sudo shutdown -hv now
```

The **-v** switch is for verbose output, so it'll show you what happens at shutdown time.

LLRNR

Thanks, when I enter the above in the terminal the computer shuts down immediately and I'm left with the new Ubuntu Edgy logo on screen as before. This remains on screen until I switch of power to the PC. 

There doesn't seem to be any problems with the normal operation of this PC other than it is not completely switching off by itself.

---

