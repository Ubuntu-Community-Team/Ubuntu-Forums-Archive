---
title: "Wireless only works after reboot"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by colokevin on 2006-03-22
When I reboot my machine, ifdown eth0 (my ethernet card) and ifup wlan0 (my wireless card), wireless network connectivity works fine.  I get an ip from my router, WEP is on, name resolution and routing is all perfect.  If I ifdown wlan0 (say I want to go back to wired network), and then later try to ifup wlan0, dhcp can not get a lease from my router.  Dhclient wlan0 just sits there trying until it eventually times out.  The only way to Re-get a lease is to reboot, and start the process all over again. 

I've seen a couple of threads on the forums from people with a similar problem, but I haven't seen a resolution yet.  Can anyone help?  Thanks!

---

### Post by nanotube on 2006-03-22
dont know about your specific problem, but if you frequently change between wired and wireless, network-manager package will do it for you automatically, without you having to bring interfaces up and down manually.
check the link in my sig, and go to the "multiple wireless profiles" section. note: do not use the network-manager package from synaptic, because it has problems, use the one linked to on my site.

---

