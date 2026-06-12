---
title: "samba print share inaccessible"
date: 2013-03-21
forum: Any Other OS
---

### Post by hurtstotalktoyou on 2013-03-21
I'm trying to set up a network printer share through samba.  I enabled "guest ok" in the smb.conf file for the printers:

```
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
```

and so now I can actually see the printer on my samba network.  But when I set the authentication details and click "verify" I get a **print share inaccessible** error.

Searching the net for solutions, I discovered that one bug is the printer name can't contain spaces.  So I changed the printer name so that it has the following samba address:

```
smb://WORKGROUP/PRIVATE-TVROOM/BrotherHL2140series
```

Of course I restarted samba and tried again to verify authentication, but it failed again with the same **print share inaccessible** error.

Any help would be much appreciated.  Thanks!

P.S. I'm running Linux Mint 13 64-bit MATE on both host and client.

---

### Post by Perfect Storm on 2013-03-21
Moved to Other OS/Distro Talk.

---

### Post by gordintoronto on 2013-03-21
This writeup is excellent:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by hurtstotalktoyou on 2013-04-03
gordintoronto,

Good idea to check that article, but unfortunately it did not fix the problem.  I followed its instructions, but still I cannot access the printer through SAMBA.

Any other ideas are welcome.  Thanks!

---

### Post by gordintoronto on 2013-04-03
Your previous efforts might be interfering. In my experience, you install Samba, but you only think about "printers."

---

