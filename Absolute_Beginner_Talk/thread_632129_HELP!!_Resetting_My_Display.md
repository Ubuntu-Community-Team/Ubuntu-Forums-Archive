---
title: "HELP!! Resetting My Display"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Patriot1776 on 2007-12-05
*sighs* While running with previous kernel (2.6.20-16-generic) to find what soundconfig I had that previously worked (troubleshooting sound problem), I made a new problem.  Previous kernel would only load up in basic display mode and I accidentally set the basic display mode as the permanent display mode.

Restarted to try and reset my soundconfig with current kernel (2.6.22-14-generic) and KDE started up in basic display mode, 640x480, and I don't know how to change it back.

Video card is an nVidia G70.  PLEASE SOMEBODY GIVE ME SOME HELP!!  I'M LOST and I've had to switch back to WinXP for the time being!

---

### Post by PmDematagoda on 2007-12-05
Try this:-
First kill the GUI using:-

```
sudo /etc/init.d/kdm stop
```

Then reconfigure the X-server.
```

sudo dpkg-reconfigure xserver-xorg
```

Select the driver as Nvidia and any other choices you may want and then do:-
```

sudo startx
```

---

### Post by Patriot1776 on 2007-12-05
Thank you very, VERY much!!  I shall try it now.

---

### Post by Patriot1776 on 2007-12-05
YES!!! It worked!  Thanks very much!!  Now back to tackling my ALSA problem.

---

### Post by PmDematagoda on 2007-12-05
Glad to hear your problem was solved:).

---

### Post by Patriot1776 on 2007-12-05
Yeah.  I'm back to using Kubuntu again normally (sans sound still).  The display HAS to fully work for another user to check their email on this machine.

---

