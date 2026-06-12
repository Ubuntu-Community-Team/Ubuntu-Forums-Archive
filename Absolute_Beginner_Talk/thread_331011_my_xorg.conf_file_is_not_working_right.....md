---
title: "my xorg.conf file is not working right...."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by chesman on 2007-01-04
Okay, i attempted to install compiz, and well when i restarted the wm it went all weird, so i had to hard restart...

Well, it would not boot then, So i logged into safe mode to the command line, and go to the directory, removed the bad xorg.conf file cause i couldnt figure out to edit it :(


Well i do have a n original there, but for some reason i cannot rename it :(
it currently stands with a name of xorg.conf~ 


Can someone help me figure this out? Or give me some instructions to the proper commands to rename that backup file. 


Thanks :)

---

### Post by taurus on 2007-01-04
```
cd /etc/X11
cp xorg.conf~ xorg.conf
startx
```

---

### Post by chesman on 2007-01-04
Thanks ill give that a try now :)

---

### Post by chesman on 2007-01-04
Back up and running! :)

Thanks a lot taurus :)

posting this from Ubuntu

Guess compiz / beryl is just not for me

---

### Post by taurus on 2007-01-04
> **chesman said:**
> Back up and running! :)

Thanks a lot taurus :)

posting this from Ubuntu

Guess compiz / beryl is just not for me

You're welcome.  That's why they call it a beta since it works great for some but not for a few others...

---

