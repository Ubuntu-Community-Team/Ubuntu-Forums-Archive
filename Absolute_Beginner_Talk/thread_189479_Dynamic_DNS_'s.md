---
title: "Dynamic DNS ?'s"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Charlatat on 2006-06-05
hostname is UbuntuPC.  I'm using these entries in dhclient.conf to automatically update DNS:

send fqdn.fqdn "UbuntuPC.HomeDomain.local.";
send fqdn.encoded on;
send fqdn.server-update off;

It seems to work fine, but have a couple questions:

1. As well as the A host entry, it creates a "TXT" entry.  Wondering what it is, if its necessary, and if not, how to disable its creation.

2. In both DHCP and the reverse lookup zone, the entry is kinda garbled.  Its like this:    (line break)UbuntuPC(line break)HomeDomain(line break)local(line break)HomeDomain.local.   Any way to fix this?

Thanks

---

### Post by Charlatat on 2006-06-05
anyone?

---

### Post by Vati-Khan on 2006-06-05
uncomment

[FONT="Courier New"]
send host-name "myhostname"; [/FONT]

in dhclient.conf

don't use the fqdn - usually not necessary


hope this helps

---

