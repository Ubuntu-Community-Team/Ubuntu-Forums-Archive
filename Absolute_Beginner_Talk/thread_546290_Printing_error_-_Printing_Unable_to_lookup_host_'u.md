---
title: "Printing error - Printing: Unable to lookup host 'usb' - Unknown host"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-09-08
After four months using TurboPrint driver on Ubuntu 7.04, Canon IP3000, I'm suddenly getting this error message:
Printing: Unable to lookup host 'usb' - Unknown host

My error log has only this:
E [07/Sep/2007:13:56:46 +0100] Creating missing directory "/var/run/cups/certs"
E [07/Sep/2007:13:58:59 +0100] Creating missing directory "/var/run/cups/certs"
E [08/Sep/2007:08:47:42 +0100] Creating missing directory "/var/run/cups/certs"

I can print a test page from System > printers with no problems, but not from TurboPrint configure. My printer is connected directly to my PC with USB - I have no network.

I've had these two updates:

Commit Log for Sat Sep  8 17:16:06 2007
Upgraded the following packages:
libkrb53 (1.4.4-5ubuntu3.2) to 1.4.4-5ubuntu3.3

Commit Log for Wed Sep  5 08:24:39 2007
Upgraded the following packages:
libkrb53 (1.4.4-5ubuntu3.1) to 1.4.4-5ubuntu3.2

Don't know if they can have caused this. I've seen this error msg for other printers while searching online, but can't find a solution. I can't help thinking that the updates must have done something as I've had no previous problems, and that's the only change.

TIA for advice.

---

