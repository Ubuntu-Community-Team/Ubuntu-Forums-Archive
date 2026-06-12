---
title: "Can't print with Canon IR 2020"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by twofished on 2007-05-05
Hey all,

I'm trying to print through a windows network to a Canon IR 2020. When I go through the printer setup in Ubuntu 7.04 I can find the printer on the network but then there is no sign of it on Ubuntu's printer list. What can I do?

Thank you!

---

### Post by mikeyphi on 2007-05-05
You probably need to install the driver etc....look here for instructions: [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-iR2020i](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-iR2020i)

---

### Post by Julian Lewis on 2007-05-05
I found the best way to install a network printer as LPD was to launch firefox, then goto
[http://localhost:631/](http://localhost:631/)
This talks to CUPS on your local host and you can add the printer from there

---

