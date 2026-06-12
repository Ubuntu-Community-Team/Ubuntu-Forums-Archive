---
title: "Edgy Won't Shutdown"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2006-12-18
I'm running "Edgy"

Problem: Shutdown buttons will not bring up GUI menu _Also_ Terminal will not open so I cannot shutdown through command line.

My Question: Will a hard powerdown mess up my Ubuntu installation?

Previous to this problem I had been attempting to use GAIM and eventually deleted my user account (for GAIM)

Also I had been trying to network my printer from this Ubuntu box with my WIN2K machine with no success.  Don't know if any of this had any bearing.

Suggestions?
](*,)

---

### Post by taurus on 2006-12-18
So Applications -> Accessories -> Terminal won't bring up a gnome-terminal for you?  What happens if you press <Ctrl><Alt>F2 and log in with your username and password.  Then run

```
sudo shutdown -h now  <-- to shutdown
sudo shutdown -r now <-- to reboot
```

---

### Post by xyz on 2006-12-18
You may want to try this if everything else has failed:
[HOW-TO reboot only if all else fails]("http://www.ubuntuforums.org/showthread.php?t=315404")

---

### Post by chaplanger on 2006-12-18
Thanks for the hints  <CTRL> <ALT> F2 got me to a terminal window -- unfortunately when I read this in the post I immediately tried it (thinking it would bring up a terminal window -- which of course it didn't as the system went into terminal mode)

After experimenting with various commands (exit) I finally hit upon "CTRL - ALT - DEL and the system came back with the message: "shutting down NOW!" system rebooted and all appears well again.  Thanks for the assist -- now if I only remember to print the advice before following bits and pieces I'll be much better off. . .(LOL)

----Situation Resolved---

---

### Post by taurus on 2006-12-18
<Alt>F7 will bring you back to X!

---

