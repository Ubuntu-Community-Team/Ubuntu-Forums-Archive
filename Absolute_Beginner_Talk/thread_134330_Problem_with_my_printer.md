---
title: "Problem with my printer"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by markkun on 2006-02-21
I have a problem with my Canon PIXMA iP1500 printer. I have recently changed from Mandriva to Kubuntu and I have problems getting the printer working. In Mandriva printer worked with the drivers that I got from Canon's driver page. I've found and installed drivers that I found for Ubuntu, but the problem seems to be that I can't access the printer. When I go to 127.0.0.1:631 and select printers, it says the following:

> Description: CANON PIXMA iP1500
Location:
Printer State: stopped, accepting jobs.
"Unable to open USB port device file: Permission denied"
Device URI: canon_usb:/dev/usb/lp0

I tried to add permission to read-write for /dev/usb/lp0 (sudo chmod a+rw /dev/usb/lp0) and still nothing. Advice is needed :-k

---

### Post by markkun on 2006-02-22
Hmm... I did all kinds of things that I found from these forums and finally I set the CUPS password and in the webpanel (localhost:631) I started the printer and it seemed to help... :-k

---

