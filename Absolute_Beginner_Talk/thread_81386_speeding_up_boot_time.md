---
title: "speeding up boot time"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by chrisblack on 2005-10-24
Is there a simple way of speeding up the boot time of Ubuntu.... I read somewhere about disabling the search for networks.... but can't remember where...

Chris

---

### Post by Kyral on 2005-10-24
You may want to check out BootUp Manager (Bum)

sudo apt-get install bum

Be careful though. Disable one at a time, and only if you know what you are doing

---

### Post by Juippisi on 2005-10-24
Maybe you should try this howto:
[http://www.ubuntuforums.org/showthread.php?t=80423](http://www.ubuntuforums.org/showthread.php?t=80423)
I haven't tried it, don't know if it works or not.

And install bum (apt-get install bum) and deactivate the useless services (for ex. if you don't have bluethoot or laptop, disable bluethoot and laptop services). If you use this, you better know what you're doing or else your system might not boot again. I'm not taking that responsibility of that ;-).

---

