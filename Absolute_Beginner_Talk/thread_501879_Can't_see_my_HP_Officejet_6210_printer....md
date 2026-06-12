---
title: "Can't see my HP Officejet 6210 printer..."
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by mattinthematrix on 2007-07-15
Ubuntu's printer utility and HPLIP can't find any USB printers, although System>>Preferences>>Hardware Information has no trouble acknowledging that the 6210 is 
attached.

CUPS was also no help, although I'm not sure I'm using the correct UIP. I've tried socket://localhost and the same with :9100.

I'm on a powerpc based ubuntu 7.04.

Any ideas?

Thanks!

---

### Post by jerrynewt on 2007-07-15
Go to System>Administration>Printing. Click on the Global Settings tab and click on Detect LAN printers. I ma using Fiesty 7.04 and when I did this My HP C5140 Printer was automatically detected.

---

### Post by tgalati4 on 2007-07-15
What printers are shown in your browser:

localhost:631

---

### Post by mattinthematrix on 2007-07-15
localhost:631 only shows the printer I created, which does not work.

"Detect LAN Printers" has no result, but I wouldn't expect it to, since the printer is connected by USB... am I missing something here?

Also, I am on a PowerPC based Ubuntu 7.04. Editing the original post to add this info...

---

### Post by mattinthematrix on 2007-07-19
bump. 

Is there any more help to be had on this topic?

Thanks!

---

### Post by gatzby on 2007-10-19
I'm having the same issues.  Previously my printer had been working fine, then somewhere along the line (not sure what caused it...possibly my upgrade to gutsy beta but I'm not sure) it stopped printing.  After trying to add the printer again, it is no longer detected.  This also happens in my Fedora 7 desktop as well so I don't think it's Ubuntu specific.  I bought a new print cable and it's all connected properly.

---

