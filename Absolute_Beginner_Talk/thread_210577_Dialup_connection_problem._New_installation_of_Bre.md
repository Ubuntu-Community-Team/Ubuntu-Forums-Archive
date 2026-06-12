---
title: "Dialup connection problem. New installation of Breezy"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by brn on 2006-07-07
I just installed Breezy on a newly aquired second-hand laptop.  All went well except that I cannot maintain connection through my external 56 Kb modem.  

This 'new'laptop came with Windows XP which I am using now. It works with the modem just fine.  Previously I had Breezy installed on an older machine with the same external modem and the same phone line.  It worked just fine.  My problem is that after repeated efforts, I cannot make the modem connection work with this new one.  The modem connects, negotiates, appears to  be normal, but soon disconnects. This same installation disk worked fine on the older machine and (as seen here) the hardware works with Win-XP.  I am baffled.  Thanks for any help.

---

### Post by editrix on 2006-07-07
Check your /etc/ppp/options file. There's a section about the remote host having to authenticate itself. If it ends with "auth" just comment out that line--that is, put a # at the beginning of the line.

---

