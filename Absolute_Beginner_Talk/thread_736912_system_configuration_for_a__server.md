---
title: "system configuration for a  server"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2008-03-27
Hello. I have a desktop with the following configuration. 


Pentium 4 3ghz 

1Gb DDR1 400Mhz

80 Gb sata HDD

Intel 865 desktop motherboard 

Can This desktop  run a dhcp server which wiil have 500 clients and simultaneously have a samba running on it. Note all clients will be accessing the samba share to save files etc. 

thank you

---

### Post by intel on 2008-03-27
dhcp is not a problem,

using it as a file server is also not a problem,
you need to configure it properly,
(so that 1 user's excessive usage does not hamper other users access)

I would also suggest RAID 1 i.e mirroring,

(based on assumption users usually download files more often that uploading it,
this holds true for file servers)

this will also protect you from 1 DISK failure
(you will still need to take weekly backups to another disk over the weekend)

---

