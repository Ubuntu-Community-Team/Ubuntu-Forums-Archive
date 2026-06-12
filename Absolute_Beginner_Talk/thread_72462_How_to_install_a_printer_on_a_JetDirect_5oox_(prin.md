---
title: "How to install a printer on a JetDirect 5oox (printserver)"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Immortalis on 2005-10-06
I've had a lot of trouble getting my printers working in ubuntu, but recently I found out how I worked for me.

1) System->Administration->Printng.
2) Double click on "New printer".
3) Select "Network printer" -> HP JetDirect.
4) Host = the ip-adress of the print server xxx.xxx.xxx.xxx e.g. for my printserver 192.168.1.50.
Port = the port in the printserver your printer is connected to. 9100 = port 1, 9101 = port 2, 9102 = port 3 etc. In my case 9101 because my printer is connected to port 2 on the printserver.

To sum up, in my case the data looked like the following,
Host: 192.168.1.50
Port: 9101

5) Press "forward".
6) Find your printer and select accept.

---

