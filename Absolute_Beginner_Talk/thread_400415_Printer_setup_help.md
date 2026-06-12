---
title: "Printer setup help"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Otto-C on 2007-04-03
Printer does not print. Appears hung in job que.
Current setup.
Using reccomended driver.
Network Printer address 192.168.1.3
Properties General show:

Name: Laserjet-4250
Description: HP4250Laserjet
Location: 9100

Resolution: 600 DPI

Status: Paused /usr/lib/cups/backend/ipp failed

Need some help on this one.
tia
Otto

---

### Post by 11hjpphty76lkjj on 2007-04-03
Uninstall  the printer and run

```
sudo hp-setup
```

to configure the printer?

A

---

### Post by Otto-C on 2007-04-04
Thanks for the response.
Could not delete from printer gui.
Not very good at command line.
Could use some help.
tia
Otto

---

### Post by 11hjpphty76lkjj on 2007-04-04
To delete the printer go to:

[http://localhost:631](http://localhost:631)

click printers, then delete next to the printer. :)

---

### Post by Otto-C on 2007-04-05
Thanks so much for your help.
Task completed.
Otto

---

