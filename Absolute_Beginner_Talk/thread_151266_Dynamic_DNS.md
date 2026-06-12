---
title: "Dynamic DNS?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Charlatat on 2006-03-27
Any way to enable dynamic dns updates to a W2k3 DNS box??

---

### Post by dragonfyre13 on 2006-03-27
Yeah, go into the network settings, and set that to your DNS server.

---

### Post by dragonfyre13 on 2006-03-27
Also, edit smb.conf, and /etc/dhcp3/dhclient.conf to reflect your Hostname.

---

### Post by Charlatat on 2006-03-27
Hmm, alright.  I'll try looking at smb.conf and dhclient.conf for anything I missed. Otherwise, DNS should be already automatically configured via a DHCP server...

Thanks

---

### Post by dragonfyre13 on 2006-03-27
Sure. I thought it should, but I know someone who disallowed that, in leu of a dedicated DNS server, or so I thought. I may be totally off base though.

---

