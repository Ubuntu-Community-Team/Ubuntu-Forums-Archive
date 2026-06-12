---
title: "azureus hangs"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by dwight on 2006-09-20
The situation is this. My ISP blocks most ports used by p2p programs. Up to now(in windows and different distros) I have been able to avoid NAT problems problems by running azureus on port 113 (which is one of the few ports not blocked). This, however, means that I need to run azureus as root (yes, I know not a very good idea as far as security is concerned). I can also do this in Ubuntu. For a few minutes everything is ok, download speeds are high and indicator icons are green. But after about five minutes everything grinds to a halt. No more traffic, neither up or down. Any suggestion on what could be the reason for this?

---

### Post by nickpaton on 2006-09-20
Have a look at this information from Shieldsup site on Port 113:

[http://www.grc.com/port_113.htm]("http://www.grc.com/port_113.htm")

It seems to indicate specific problems with that port.

Especially have a look down at the final para 'Stealthing port 113 on personal firewalls'

As a general rule, are you sure that your router firewall is fully configured to see that range of ports, and the pc IP address itself.  These sort of things can affect down or uploads.

---

### Post by dwight on 2006-09-20
Thanks for the link. Learned lots of new stuff there. But I doubt that my router settings are the issue here. Mainly because there are no problems like this with azureus on other distros (I've tried Arch and OpenSuse). I did a test with azureus on Arch and Ubuntu (triple booting the same machine with winxp). I downloaded the same torrent first in Arch and now in Ubuntu. In Arch download speed capped at about 250kB/s and stayed there until the torrent finished, also the upload speed was always near the maximum limit I had set. In Ubuntu it starts also with 250 but then, after a few minutes drops to 0. If I wait for a while downloading resumes and periodically oscillates between 0 and 10-15 kB/s. Upload speed never reaches maximum.

---

### Post by moore.bryan on 2006-09-20
*have you tried bittornado and setting a much higher series of ports?*

---

### Post by nickpaton on 2006-09-20
Have a look at the following post which has exactly the same problem, and appears to be due to not having Sun Java installed

[http://www.ubuntuforums.org/showthread.php?t=188149]("http://www.ubuntuforums.org/showthread.php?t=188149")

Later posts appear most useful.

Alternatively try using Bittornado which has always worked OK for me, and I believe is available via Synaptic.

---

### Post by dwight on 2006-09-22
> **nickpaton said:**
> Have a look at the following post which has exactly the same problem, and appears to be due to not having Sun Java installed

[http://www.ubuntuforums.org/showthread.php?t=188149]("http://www.ubuntuforums.org/showthread.php?t=188149")

Later posts appear most useful.

Alternatively try using Bittornado which has always worked OK for me, and I believe is available via Synaptic.

Exactly!! That was it. Installed SUN JRE and now everything works as it should. Thanks

---

### Post by nickpaton on 2006-09-22
Glad it's fixed and thanks for feeding back.

---

