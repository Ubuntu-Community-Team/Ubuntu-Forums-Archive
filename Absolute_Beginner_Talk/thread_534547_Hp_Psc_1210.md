---
title: "Hp Psc 1210"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by dnance on 2007-08-25
Hi!

I have an HP psc 1210 (usb) installed on feisty fawn.  It has been printing fine for a few months

Today I tried to scan using XSane, and I was able to scan fine, (save to pdf, etc) when I went back to print, the job hangs in the queue. The printer status says "Printing: Printer not connected; will retry in 30 seconds..." If I restart my machine, it again prints fine until I scan again. 

I have tried restarting cupsys under /etc/init.d, which makes the printer show a status of ready, but it reverts to printer not connected again when I print.

I am using the psc1210 driver.

Any ideas?

---

### Post by str8line on 2007-09-02
Sounds like a possible CUPS issue.  Have you tried using the HPLIP drivers from Synaptec?  I have found with my HP 1510 that I get a few more options out of the 3 click installation than I do from the standard HP drives.

---

### Post by dnance on 2007-09-09
I'll try that 

thx

---

