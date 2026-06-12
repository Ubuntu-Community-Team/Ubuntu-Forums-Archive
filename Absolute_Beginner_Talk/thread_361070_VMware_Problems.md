---
title: "VMware Problems"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by c_forq on 2007-02-13
Every time I reboot I have to run /usr/bin/vmware-config.pl in order to get vmware to start, and I think this shouldn't be needed but don't know how to fix it.  Also half the time the VMware script is unable to stop the Virtual ethernet, forcing me to reboot again or even reinstall VMware server.  Anyone have any suggestions or solutions to these problems?  Thanks in advance!

---

### Post by c_forq on 2007-02-13
Okay, I fixed it myself.  For people encountering this problem in the future I had a file called vmwareplayer in /etc/init.d that I removed, and now all is well in my computerland :).  I knew VMware Player and Server didn't get along together, but apperantly the uninstall of VMware Player wasn't complete and they REALLY don't get along together :).

---

