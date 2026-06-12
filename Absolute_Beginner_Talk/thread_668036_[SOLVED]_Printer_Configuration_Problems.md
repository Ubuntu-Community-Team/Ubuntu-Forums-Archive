---
title: "[SOLVED] Printer Configuration Problems"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by cement406 on 2008-01-15
List,

Today I downloaded and installed the lpr and cups from Brother for my HL-5150D laser printer, from the command line.  I am using Ubuntu Gutsy.  I was able to tweak the printer settings through System-Administration-Printers in the desktop menu.

Everything worked fine until I rebooted my system.  Now all printers disappeared.  When I go to System-Administration-Printers everything is greyed out.  In addition, at the bottom of the dialog box there is the message "Not Connected."  If I then click the "Goto Server" button in that same dialog box and try to connect, I get a "CUPS server error" box.

Any idea how I can get things back?

---

### Post by cement406 on 2008-01-17
I solved my own problem.  I realized that at sometime I had accidentally deleted the cupsys script in /etc/init.d .  I removed then re-installed cupsys and now the server is back up and running.

---

