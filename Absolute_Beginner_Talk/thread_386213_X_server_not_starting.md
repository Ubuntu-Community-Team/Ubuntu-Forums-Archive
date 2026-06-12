---
title: "X server not starting"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by android mouse on 2007-03-16
I installed Ubuntu on my Hp Pavilion dv5000 laptop from the 5.10 CD. After finishing the install, X server immediatly crashes. Since I was unable to interpret what was going wrong by reading the logs I ran apt-get update; apt-get dist-upgrade to see if that would fix the problem.

Upgrading did not solve the problem and X still crashes. I have made no other changes besides upgrading to 6.10

My graphics card is ATI RADEAON XPRESS 200M

/var/log/Xorg.0.log: [http://paste.ubuntu-nl.org/10684/](http://paste.ubuntu-nl.org/10684/)

thanks

---

### Post by annda on 2007-03-16
from your post i gather it was a fresh install of breezy (not working)  > no changes > update to edgy (not working).

can you do a new edgy install from cd (no upgrade)?

also, your xserver complains about DRI (direct rendering). have you changed anything there or was it a default option? please post you xorg.conf

---

### Post by android mouse on 2007-03-16
> from your post i gather it was a fresh install of breezy (not working) > no changes > update to edgy (not working).
Correct. After I posted this I tried [http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766) which also lead to no success.

> also, your xserver complains about DRI (direct rendering). have you changed anything there or was it a default option? please post you xorg.conf
Nope.

xorg.conf: [http://paste.ubuntu-nl.org/10698/](http://paste.ubuntu-nl.org/10698/)

this part:

```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

was added after I posted this topic (it was part of the howto I posted above)

> can you do a new edgy install from cd (no upgrade)?
I don't understand. Do you mean create an edgy cd and do a fresh install of that? If so, then yes should I do that?

---

