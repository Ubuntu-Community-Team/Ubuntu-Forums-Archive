---
title: "[SOLVED] My Ubuntu pc just won't open anymore!"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Phil420 on 2008-01-03
okay so emm... i'm writing from a windows pc now... because after installing ATI drives on my ubuntu pc using Envy... well emm now that i start my pc.. after the ubuntu loading.. nothing happens. i tried more than once, and it just doesn't do anything! i checked on this link where it says to get nvidia drivers, but my graphic card is ATI... so I got ATI drivers... and then I just can't get ubuntu to open.. Please help i've spend so much time trying to understand this complicated language that is ubuntu!
Thanks!

---

### Post by Phil420 on 2008-01-03
oops haha i forgot to put the "link i used to do what i was going to do when it stopped working"
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by taurus on 2008-01-03
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Phil420 on 2008-01-03
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

okay thanks i'll try that... in a couple of days lol i'm not at home for a while :P

---

