---
title: "No networking in new Dapper install!"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by sebald on 2006-08-12
On one machine I've had mysterious loss of networking on first boot from hard disk. Everything is fine with the live boot, so my hardware must be fine, but after the hard disk install, no network access at all. Strangely, it seemed to be able to access the network during install. But once installed, I can only ping 127.0.0.1, can't ping any IP addresses on the local net or the internet, can't run any network stuff. Have verified the install disks, used the same disks on another computer and everything's fine, have tried both the standard and alternate CD installs. Have tried deactivating/reactivating networking in the administration network panel. HELP!

---

### Post by drtvasudevan on 2006-08-12
how do you connect to internet?
what modem?
wired or wireless? cable or adsl?

also try this but if you cant ping it most likely will not work.
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox.

---

### Post by sebald on 2006-08-12
This is basic wired ethernet connection. Once again, no ping at all (except localhost/127.0.0.1) even though all worked fine when booting live CD. Yeah, I read about the Firefox issue but there's no connectivity at all, IP addresses, hostnames, nada.
> **drtvasudevan said:**
> how do you connect to internet?
what modem?
wired or wireless? cable or adsl?

also try this but if you cant ping it most likely will not work.
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox.

---

### Post by drtvasudevan on 2006-08-13
see this thread may be it helps.
[http://www.ubuntuforums.org/showthread.php?t=228606](http://www.ubuntuforums.org/showthread.php?t=228606)

---

### Post by sebald on 2006-08-13
> **drtvasudevan said:**
> see this thread may be it helps.
[http://www.ubuntuforums.org/showthread.php?t=228606](http://www.ubuntuforums.org/showthread.php?t=228606)

Thanks. Glad somebody else had the same problem, but it's odd it would be a problem on this machine and not another! 

But my workaround was to download Xubuntu and try that, and it works fine (I'm posting to you now on a fresh Xubuntu install!). Now I can add Gnome, KDE, etc. on top!

---

### Post by azmrb on 2006-08-13
What motherboard and ethernet?

---

