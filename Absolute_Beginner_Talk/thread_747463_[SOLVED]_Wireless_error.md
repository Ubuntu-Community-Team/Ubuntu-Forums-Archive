---
title: "[SOLVED] Wireless error"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Orcaporka on 2008-04-06
I had a few issues with my wireless however I managed ot get it working by connecting via wired internet then enabling "Firmware for Broadcom 43xx chipset family" and downloading what was required.

It worked fine for an hour or so but then UI began to install and update which had an error and ever since then I have been unable to connect to my wireless. The network manager doesnt even provide it as an option just "wired" and "modem."

---

### Post by ugm6hr on 2008-04-06
If you are starting a new thread, I would suggest you tell the full story...
[http://ubuntuforums.org/showthread.php?t=746589&page=3](http://ubuntuforums.org/showthread.php?t=746589&page=3)
[http://ubuntuforums.org/showthread.php?t=747386](http://ubuntuforums.org/showthread.php?t=747386)

The problem is probably that you blacklisted bcm43xx when trying ndiswrapper, so when you rebooted, the driver wouldn't load.:

> 
For that - you need to unblacklist bcx43xx (edit /etc/modprobe.d/blacklist and remove the entry for bcm43xx)

To do that:

Backup blacklist first:
```
sudo cp  /etc/modprobe.d/blacklist  /etc/modprobe.d/blacklist.bkp
```

Then remove the bcm43xx line and resave:
```
gksudo gedit  /etc/modprobe.d/blacklist
```

Then reboot.

---

### Post by Orcaporka on 2008-04-06
Thanks it was indeed on the blacklist, however I still do not have the choice to pick my wireless connection. The ligjht is now one but there is connection.

---

### Post by Orcaporka on 2008-04-06
It is working once again, howver Im worried that if I reboot, ill have to go through the whole procedure again. I have a popup saying that a restart is required to put changes into effect...will that just reset it?

---

### Post by jpeddicord on 2008-04-06
> **Orcaporka said:**
> It is working once again, howver Im worried that if I reboot, ill have to go through the whole procedure again. I have a popup saying that a restart is required to put changes into effect...will that just reset it?

It shouldn't reset itself as long as you just removed the blacklist entry. That file is saved.

---

