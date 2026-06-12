---
title: "How do I add a printer when using a usb print server?"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Linuxnewbie2006 on 2006-05-01
I'm using a router with a print server included. I installed the print server on my XP computer using a utility cd included w/router. 
How can I intall the server on my ubuntu computer?
I appreciate your help.

---

### Post by Chuck_W on 2006-05-04
I think my setup is similar. The laser printer (Kyocera FS-1010) connects to my network with a Hawking Technologies ethernet to usb print server. The configuration of the print server was already done from a windows machine. In Ubuntu, I used Unix printing (LPD). The host is the IP address (192.168.123.xx) and the Queue is lp1. After making those entries you pick the correct driver and you should be good to go. One caution - if you do something wrong and need to change settings don't bother trying to revise the printer just created. It didn't work for me. The best thing was to delete the printer and start over with the add printer wizard. Hope this helps.

---

### Post by Linuxnewbie2006 on 2006-05-05
Thanks for the advise Chuck.

---

