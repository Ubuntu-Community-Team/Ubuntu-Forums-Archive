---
title: "Dolphin question"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by whein on 2007-12-28
I recently upgraded my Kubuntu box to Gutsy and what do you know, Dolphin is now my default file manager.  But all the pull down menu boxes seem to freak out when the mouse passes over them.  They start blinking very rapidly and it seems like my system slows down, as if the CPU/RAM was suddenly under a heavy processing load.  Is this a Dolphin problem or a Compiz related thing?  I don't think I ever explicitly installed Compiz (not since Ubuntu Dapper, and I hastily removed it) but I want to say I read somewhere that Gutsy installs Compiz or some variant automatically.  Anyone know for sure yes or no?  is the pull down menu thing a known problem (with a known work around/fix)?  (How) Can I safely remove Compiz without breaking stuff?  Thanks for the help guys and gals!
-Will

---

### Post by p_quarles on 2007-12-28
No, Compiz does not come with Kubuntu 7.10, so that shouldn't be the problem. You can always find out whether or not it's installed, though, by running this:
```
dpkg --get-selections compiz
```
Anyway, what are you hoping to do? Would you prefer to fix Dolphin, or to change the default file manager to something else? I can try to help with the former, and can definitely help with the latter.

---

