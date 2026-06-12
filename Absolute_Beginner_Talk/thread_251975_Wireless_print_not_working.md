---
title: "Wireless print not working"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Wumpus20 on 2006-09-06
I'm trying to print on my Brother HL-1440 using a Trendnet TEW-P1UG wireless print server.

The print server works: I can print a test page through its web interface.
But I can't print from any Ubuntu application.

As "printer type" I've chosen CUPS-printer (IPP).
But I'm not entirely sure what to use as "Address". Right now I have ipp://PS-8B65F5/PS-8B65F5-U1 (the server name/the printer name). But I get the message "Unable to lookup host 'PS-8B65F5' - Unknown host".

I could be making some simple mistake...
Any help is appreciated.

Thanks.

---

### Post by Apple 101 on 2006-09-06
You could try using the "Network Printer" search function, or use the actual IP of the print server instead.

---

### Post by Wumpus20 on 2006-09-06
Thanks. But I'm not sure where to find the search function - there doesn't seem to be one in the "add printer" wizard. Using the IP (as in ipp://192.168.1.34) doesn't seem to work either.

---

### Post by Apple 101 on 2006-09-07
> **Wumpus20 said:**
> Thanks. But I'm not sure where to find the search function - there doesn't seem to be one in the "add printer" wizard. Using the IP (as in ipp://192.168.1.34) doesn't seem to work either.

Are the Linux drivers correct for your printer?

---

