---
title: "cannot click"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by tomor on 2008-02-29
hi ,

sometimes my panel (containing the Kmenu icon, system menu, desktop access) freezes and i cannot click anything in that panel and also in desktop .. but desktop widgets still continue to work.. the only solution for this seems to be rebooting. 

Is there any better solution :(:(:(??

---

### Post by Hospadar on 2008-02-29
does it only freeze at specific times (when a certain application is open, etc) or does it just happen totally at random.

Has it always happened (since you installed the system?). If so it might be an issue with corrupt user config files.  you might try creating a new user and see if it crashes on that account as well.

Alternatively, I suspect a restart of your X server would clear up the problem faster than a reboot in the meantime.  Try Ctrl-Alt-Backspace or (on a command line, assuming you are using kde) ```
sudo /etc/init.d/kdm restart
```

---

