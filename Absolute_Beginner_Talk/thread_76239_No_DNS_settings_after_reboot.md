---
title: "No DNS settings after reboot?"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by Feirax on 2005-10-14
Hi,

I'm having a problem where everytime I login to Breezy, my DNS settings from resolv.conf are gone.  I add them but everytime I restart they're gone again.

How can I go about figuring out what is overwriting them?  If it helps, I had tried to install vpnc/cisco vpn clients and ended up backing them out, and that's when the problem started.

Thanks in advance!

-F

---

### Post by adwait on 2005-10-14
Try installing resolvconf:
```
sudo apt-get install resolvconf 
```

Edit the file in /etc/resolvconf/resolv.conf.d/original and add the nameserver entries that you want in the resolv.conf.

---

### Post by Feirax on 2005-10-15
That did the trick! Thanks alot for the help!

---

