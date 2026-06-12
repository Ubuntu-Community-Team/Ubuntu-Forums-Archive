---
title: "port 21"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-09-07
How do I disable port 21 so it is stealth?

---

### Post by justleen on 2007-09-07
uhm... can you eleborate?

what do you mean with "stealth" and "disable" in this case?

if you dont have an FTP server running, there shoulnt be anything listening on port 21

---

### Post by robert_pectol on 2007-09-07
justleen,
  'Stealth' is another name for a non-response to a SYN packet, or connection request.  Instead of a TCP reset (closed port) type response, there is no response whatsoever, hence 'stealth'.

pdlethbridge,
  Any of the firewall configurators for Linux will probably get you what you are looking for as far as, 'stealthed' ports.  Or, if you're willing to dig in a little, the iptables tool will allow you to configure a firewall which can accomplish it.

---

### Post by pdlethbridge on 2007-09-07
my bad, its port 22

---

### Post by BrendanM on 2007-09-07
I believe Firestarter is a program that will help configure your firewall. By default, Ubuntu doesn't have any open ports, so I wouldn't worry too much.

---

