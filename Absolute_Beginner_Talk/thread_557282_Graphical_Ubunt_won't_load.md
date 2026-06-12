---
title: "Graphical Ubunt won't load"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Major Crash on 2007-09-22
I'm currently working from the Ubuntu Live disc.  Ubuntu has already been installed.  when I try to start up my computer, the graphical load screen appears, but the graphical desktop doesn't.  Instead, I get this.

Loading, please wait ...
kinit: name_to_dev_t(/dev/disk/by-uuid/123d465a-5678-46de-8969-38f9ac3aa4af) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/123d465a-5678-46de8969-38f9ac3aa4af
kinit: No resume image, doing normal boot...

Ubuntu 7.04 mike-laptop ttyl

mike-laptop login:



How do I fix this?

---

### Post by Jeroen Vernooij on 2007-09-22
1 )  type your username 
2 )  press enter
3 )  type your password  
4 )  type startx

tell us what happens.

---

### Post by Major Crash on 2007-09-22
Awesome, it worked.  Thank you.

Will I have to do that everytime from now on?

---

### Post by Jeroen Vernooij on 2007-09-22
Cool, no problem

To explain:
the command startx starts the Display server (X.org) which is required for the desktop.


> Will I have to do that everytime from now on?

-   Ehm, I don't know for sure because I don't know the cause why it didn't start in the first place. Just try and reboot. If it remains, maybe you should reconfigure X.org:
```
sudo dpkg-reconfigure xserver-xorg
``` 
This is a wizard which asks many questions, if you don't know answers for sure, safest is to just press enter each time.

---

