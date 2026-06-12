---
title: "[SOLVED] Can't remove printer!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2007-07-07
OK,
So I finally got my Laserjet 1100 to print from my laptop over the network.  The problem is, while playing around with CUPS, etc., I managed to add a printer called "LaserJet", and send 2 print jobs to it.  It's now sitting uselessly in my task bar, "printing".  When I go to System-Administration-Printing, select the bad printer, and click "remove", the GOOD printer (laserjet-1100) disappears!  However, the "bad" printer (LaserJet) won't go away.  I've reinstalled the working printer 3 times now, while trying in vain to remove the non-working one.  There must be a .conf file or something somewhere that I can use to get rid of this non-working printer.  Oh, by the way, when I open the printer to view the 2 "jobs" there's nothing on the list, so I can't even delete them and get the icon off my desktop!
Thanks again for any help,

---

### Post by Speedoo on 2007-07-07
Aha!  I found it.  /etc/cups/printers.conf
I just edited the file to remove "LaserJet", restarted cups, and I'm good to go.  
Problem solved.

---

