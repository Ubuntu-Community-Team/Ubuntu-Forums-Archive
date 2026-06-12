---
title: "Networking issue"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by mikec73 on 2007-12-11
dual boot system.  After installing ubuntu, cannot get ip on the ethernet port in windows or linux.  For windows found that if I turn off computer and wait 30 secs vs restart then network works.  assuming the same may work for ubuntu. this says there is some initialization problem that is retained with warm reboot to change OS.  any ideas to get rid of this problem?  Ubuntu did work at one point.

---

### Post by schmildo on 2007-12-12
Are you using DHCP? Perhaps your DHCP server is getting cranky about having to dish out new IP addresses to the same MAC address in a short period of time?

---

### Post by firestorm_v1 on 2007-12-12
are you directly connected to a cablemodem by chance?

---

### Post by mikec73 on 2007-12-12
connected to wireless router, then VOIP adapter, then DSL modem.  I had already tried bypassing the routers to no avail.
 (no cablemodem here, cannot tolerate that horrible service.):)

---

### Post by firestorm_v1 on 2008-01-11
Hmm, well that's a good one..
just out of estreme curiosity, what happens if you manually assign an IP to your interface?

(as root or sudo) ifconfig eth0 192.168.0.2 netmask 255.255.255.0
(as root or sudo) route add default gateway 192.168.0.1

and see if you can ping an IP address?  You'll have to use whatever network settings you're using, those IPs above are just an example.  Make the gateway IP the IP of your wireless router and the ifconfig IP to something you're not using on another machine.

DNS won't work because like I said, this is quick-n-dirty, but 4.2.2.1 answers pings typically, if you can't think of a server that does.

See what develops! - Kodak

---

