---
title: "Can't Access Internet With Wired Connection"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by RonnieV on 2007-08-01
I just installed 7.04 onto a relatively fast P3 with 256 MB of memory with no apparent problems. However, I can't access the internet.  While this PC will normally reside on a wired home network with 2-3 other Windows machines, in an effort to troubleshoot the problem, I connected it directly to my cable modem and still had no access.

Here's my Network Settings.  I have my Wired Connection set to automatic configuration (DHCP), with roaming mode disabled.  I enabled this connection by checking it on the Connections Tab.  The fields labeled IP address, Subnet Mask, and Gateway Address are not populated.

When I access Network Tools, I find the default Network Device is Loopback Interface.  Under IP Information, two protocols appear -  IPv4 and IPv6.  Changing the device to Ethernet interface (which I would have guessed to be correct for me) eliminates everything in the IP Information dialog box and the Interface Information dialog box.  I am unable to ping Yahoo using either.  

Ubuntu seems to see my ethernet card.  

Where do I go first (and second and third)?  TIA for your assistance.

---

### Post by Rocket2DMn on 2007-08-01
Try allowing roaming on the wired ethernet, that's what I had to do.
If that doesn't work, you may need to disable ipv6

---

### Post by RonnieV on 2007-08-02
My problem was Ubuntu's inability to work with my NIC card.  I replaced it with another one from an older PC and it worked fine.  

Reminds me of something doctor's sometimes say when diagnosing a patient - "When you hear hoof beats, think "horses" rather than "zebras."

---

