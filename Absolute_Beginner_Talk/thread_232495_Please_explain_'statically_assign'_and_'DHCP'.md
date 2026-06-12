---
title: "Please explain 'statically assign' and 'DHCP'"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Stephen_A on 2006-08-08
Hi, 
Please excuse the ignorance. Someone just advised me to 'statically assign' the informaiton my ISP provided in 'System>Administration>Networking.' The problem is internect connection. On Network settings>Interface properties I entered my IP information, but if I change to DHCP the fields 'IP Address,' 'Subnet mask' and 'Gateway address' all become greyed out and inactive. 
  Could someone please explain what 'statically assign' means and what I'm doing wrong in setting up 'Network settings.' Thanks very much. 

Stephen.

---

### Post by bensexson on 2006-08-08
DHCP stands for Dynamic Host Control Protocol.  It needs a DHCP server to provide IP address information.  Static assigned means to assign the IP address manually and it does not change.  Hence static.

---

### Post by Stephen_A on 2006-08-08
Thanks for your quick and helpful reply. So how do I enter the IP information manually if the relevent fields are greyed out? Thanks.

---

### Post by dalonso on 2006-08-08
> **Stephen_A said:**
> Thanks for your quick and helpful reply. So how do I enter the IP information manually if the relevent fields are greyed out? Thanks.

Simply do not change the combo to DHCP, keep it in the statically assigned option, and the entry boxes will be active again.

---

### Post by Stephen_A on 2006-08-08
Thanks for that but I seem to be in a kind of vicious circle. Someone else advised me to change to DHCP in order for the connection to work.

---

### Post by IYY on 2006-08-08
It depends on your connection. Does your ISP/router give you assign you an IP address automatically (DHCP), or are you given an address you're supposed to type in? If it's the latter, you don't have DHCP and should not use it.

---

