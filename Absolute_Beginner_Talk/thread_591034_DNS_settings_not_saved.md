---
title: "DNS settings not saved"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-25
I need to set a specific DNS in order to surf in internet. Everything works ok, but then 10 minutes later, everything gets deleted and I have no DNS, so I Need to set up everything again every 10 minutes.. Why DNS aren't saved?

Any idea?

---

### Post by speed145a on 2007-10-25
I have had numerous problems with the DNS settings in Gutsy as well.

I found that if you make the settings as you need them to be then click on the "save current configuration as location" button (the one that looks like a floppy) in the network settings manager that should keep all your settings from changing

let me know if that works!

---

### Post by ghantoos on 2007-10-25
Try this:

```
 sudo vim /etc/dhcp3/dhclient.conf
```and add this:

```
 interface "eth0" {
        supersede domain-name-servers XX.XX.XX.XX;
}

```This should force your resolv.conf to the settings above.

Hope this helps,

cheers,

Ghantoos

---

### Post by Kosimo on 2007-10-25
Gonna try to do it now, thank for answers guys.

---

