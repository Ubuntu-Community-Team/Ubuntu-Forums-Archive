---
title: "Please Review My GUFW Configuration For Errors"
date: 2013-06-03
forum: Any Other OS
---

### Post by guimaster on 2013-06-03
Greetings,

I've configured GUFW as follows. I'm wondering if  someone can review it to see if it's going to work well and if there is  anything missing or unnecessary:

```

**First, I allowed all of these outgoing ports as such:**

Example = To: 21 /tcp   Action: Allow Out   From: Computer's IP Address
Example = To: 137 /both   Action: Allow Out   From: Computer's IP Address

21 / tcp (ftp)   From: Computer IP
53 / both (dns)   From: Computer IP
67 / udp (dhcp)   Etc..
80 / tcp (http)
123 / udp (ntp)
137 / both (samba)
138 / both (samba)
139 / both (samba)
161 / udp (snmp for printer i think)
443 / tcp (https)
445 / tcp (windows shares)
465 / tcp (secure smtp)
587 / tcp (starttls)
631 / both (cups)
995 / tcp (secure pop)
1863 / tcp (msn)
5353 / udp (i can't remember why i need this)
11371 / both? (openpgp)
51413 / both? (transmission)
54925 / udp (brother scanner)

**Secondly I added all of these incoming ports:**

68 / udp   From: Router IP
123 / udp   From: ntp.ubuntu.com (91.189.94.4)
137 / both   From: Router IP & Networked Computers IPs & Printer IP
138 / both   From: Router IP & Networked Computers IPs & Printer IP
139 / both   From: Router IP & Networked Computers IPs & Printer IP
161 / udp   From: Router IP & Printer IP
445 / tcp   From: Router IP & Networked Computers IPs & Printer IP
631 / both   From: Router IP & Printer IP
5353 / udp   From: Router IP & Printer IP
54925 / udp   From: Router IP & Printer IP

**Then I added these rules to ensure nothing else can get through either way:**
**I blocked the following from any Outbound IP:**

1:65535 / tcp
1:65535 / udp

**And I blocked the following from any Inbound IP:**

1:65535 / tcp
1:65535 / udp


```

 I see that Ping isn't working, so I'll have to sort that. Traceroute too probably. But otherwise, does this sound like a good configuration? I'm concerned a bit about the time server. Will my time get updated? I'm running Linux Mint 15. Will people be able to see me on MSN and Skype?

 Thanks!

Edit: I was able to test NTP successfully by running the following command: sudo ntpdate ntp.ubuntu.com
Edit: I can't print. Damn...

---

### Post by Perfect Storm on 2013-06-03
**Moved to Other OS/Distro Support.**

---

