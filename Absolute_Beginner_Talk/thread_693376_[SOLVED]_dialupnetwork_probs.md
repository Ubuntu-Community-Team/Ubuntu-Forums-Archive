---
title: "[SOLVED] dialup/network probs"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by japephillips on 2008-02-11
got a conexant softmodem working OK after a week ...
but something (updater?) dials in as booting
i can then browse (seems slowly compared to XP) and get mail or download
but after i disconnect i cannot connect later - nothing happens
also where do i find the updater off switch, lol!

edit; using 7.10

---

### Post by spiderbatdad on 2008-02-11
System>>Administration>>Update Manager

---

### Post by japephillips on 2008-02-11
that has no 'switch' that I can find to turn off updater, stop it from running as the machine boots
the problem of no more connections possible after closing first one is the worst

---

### Post by spiderbatdad on 2008-02-11
sorry System>>Administration>>Software Sources>>Updates

---

### Post by japephillips on 2008-02-11
> **spiderbatdad said:**
> sorry System>>Administration>>Software Sources>>Updates

that sorted that bit, hopefully it will fix the other if it was the updater not releasing
many thanks

---

### Post by japephillips on 2008-02-11
no, that didn't work, dialup during boot works automatically for some reason whether auto update is on or off. Then if disconnected (oolbar/network/dialup disconnect) it does nothing if 'connect' is selected for later dialup attempt.
This has happened since accepting and installing all the bloody 85 meg seven hour dialup download of security updates! i have also uninstalled Open Office, doubt if that has anything to do with it.
so it has to be a network setting but goodness knows what where and how to change it.
i have to shutdown and restart each time I want to connect!
any ideas how/where i can control this?

---

### Post by japephillips on 2008-02-11
well...updater didn't turn off under the sys/admin/softupdate menu but after another few hours i found out that it only turns off under sessions/startup. Is this a bug?

however, although i can now turn off/on the ppp connection for dialup at will under toolbar/network, something still dials and connects during boot and stays doing so (noisily despite modem sound turned off in network/modem config) until the boot is complete and I can turn off the ppp dialup I didn't request! Any ideas please?

---

### Post by japephillips on 2008-02-11
turning off "set modem as default connection" which I had found on another post as a possible solution didn't work either! I also tried pulling out the phone lead and it still dialed (noisily) but to no avail (leaving phone line 'brrrr' coming through speaker) and then as soon as i put the lead back it dialed on its own again - but wouldn't find anything through browser until I reset that default and restarted

I am going in circles and getting very cross! ANY IDEAS ANYONE? This has taken me a week of browsing and experimenting to get a dialup configured and although it works now i do NOT want anything dialling out withotu my control or at least knowledge of what it is. I HATE windows for many reasons but dammit, even a beginner like me can work this basic stuff out there!

---

### Post by spiderbatdad on 2008-02-11
you can do```
cat /etc/wvdial.conf
``` or you can navigate to it with Places>>Computer>>File System>>etc...then scroll to the bottom and click wvdial.conf

Also. are you using gnome-ppp? How do you launch the connection manually...in terminal?
What dstew said about System>>Administration>>Services may be the simple solution.

---

### Post by japephillips on 2008-02-11
i got confused, will stick to the later thread

[http://ubuntuforums.org/showthread.php?p=4311763#post4311763](http://ubuntuforums.org/showthread.php?p=4311763#post4311763)

---

