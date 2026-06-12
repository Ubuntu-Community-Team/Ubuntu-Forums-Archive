---
title: "HVR-1300 help"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by ImolaOrange on 2007-02-08
Just installed Ubunto 6.10 and am trying to get my HVR-1300 card working.

I followed the steps here...
[http://www.ubuntuforums.org/showthread.php?t=337960&highlight=hvr1300](http://www.ubuntuforums.org/showthread.php?t=337960&highlight=hvr1300)

... and I managed to get the card working.

However if I reboot I need to re-run this command... "sudo modprobe cx88-dvb"

Can I had this to some config file so its run when I reboot the machine?

Thanks
Alan

---

### Post by pancyber on 2008-04-15
You can add cx88-dvb module in /etc/modules file so it loads automaticaly at boot time

---

