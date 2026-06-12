---
title: "No internet in 6.10 on B&amp;W PowerMac"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by Killa Frog on 2008-05-12
Hi all! I recently installed 6.06 Dapper on my B&W PowerMac g3 (remarkably, ubuntu was the only distro that could and boot up later with video <not even straight Debian!>) and everything was working perfectly until I did a network upgrade to 6.10. Now it's entirely unwilling to connect to the inernet! This wouldn't be a problem, except the only reason I upgraded in the first place was so I could replace GNOME with E17. I already disabled ipv6 in /etc/modprobe.d/aliases and tried to filter it out in Firefox to see if I could at least get that running, but the entire system refuses to connect to the internet, even though the network connection is shown as a working one in the manager. I'm completely at a loss, any suggestions?

---

### Post by stream303 on 2008-05-12
I'd run ifconfig to help see if the ethernet interface is coming up, and go from there.  We'd also need a bit more info, such as are you running dhcp, static addresses, behind a router, etc?  This is probably more of a generic networking issue than anything PPC-specific.

Later on, you may want to upgrade to a newer version:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by Killa Frog on 2008-05-12
Actually, though I probably should have removed this thread after doing so, I went ahead and installed the Debian base on it and am just going to build everything myself from there. That sounds easier to me than trying to make do with other people's work (never had much luck with Ubuntu anyway, and I've tried it on at least 6 different computers). Thank you very much for responding though, the Ubuntu user community is always very helpful! (Just too slow for my ADD!)

---

### Post by stream303 on 2008-05-12
No problem - Debian is a fine distro, and netinst works well.  I'm watching lenny testing too...

---

