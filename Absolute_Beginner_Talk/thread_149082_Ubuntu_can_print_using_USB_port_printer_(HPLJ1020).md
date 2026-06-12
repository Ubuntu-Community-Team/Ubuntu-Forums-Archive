---
title: "Ubuntu can print using USB port printer (HPLJ1020)"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by budialok on 2006-03-23
Dear all,

I am new to ubuntu and Linux, I have been trying to replace our windows client on my office to linux (ubuntu) but i got a problem with printing process. If we print using printer that use LPT port (such as HP LJ 1200), everything goes excellent, but when we do on my printer with USB port, the problem comes up... On screen, it notified that print jobs is completed, but on printer doesnot print anything. We are using ubuntu 5.0.

Any help and advice are more than welcome.

Terima kasih ( Thank you )

Budi Santoso

---

### Post by tuxinvader on 2006-03-23
The linux printing HP ppd files can be buggy sometimes. I've got an old 5Lsi here that only works with the HP supplied ppd. Try installing the HP drivers from the hp-ppd package in the universe repository and change the printer to use those instead.

---

### Post by nlow04 on 2007-02-02
I have the same problem.  I switched to Ubuntu 6.10.  I have a HP 3322 and this operating system detected it but when I try to print a test page, it can't print.

Can someone assist me?  

Thanks.:confused:

---

### Post by donnguna on 2007-10-18
my hp dj 1360 work with freespire and ubuntu,....

Just plug and search the driver in the net,...

---

### Post by Sef on 2007-10-18
Have you downloaded the [pnm2ppa drivers]("http://sourceforge.net/projects/pnm2ppa/")?   These are the drivers for [printer]("http://hplip.sourceforge.net/faqs.html"): 

> Question: Are drivers available for the Deskjet 710C, 712C, 720C, 722C, 820Cse, 820Cxi, 1000Cse, 1000Cxi; or LaserJet 1000, 1005, 1020, 3100; or Color LaserJet 1500, 2600 printers?

Answer: These are non-standard host based printers. Currently there are no plans to support these printers in HPLIP. Ghostscript print filters for the Deskjet products can be found at the pnm2ppa project.

---

### Post by Sef on 2007-10-18
> We are using ubuntu 5.0.

Please note there is no 5.0.   There would be 5.04 and 5.10.  Both of those are no longer maintained.  If you are using one of them, then I would tell you to upgrade to Hardy Heron, 8.04, when it comes out in 6 months.  It will be an LTS - Long Term Stable with updates for 3 years on the desktop and 5 years on the server.  Non-LTS's are updated for 18 months.  Ubuntu naming goes by year and month released.

---

