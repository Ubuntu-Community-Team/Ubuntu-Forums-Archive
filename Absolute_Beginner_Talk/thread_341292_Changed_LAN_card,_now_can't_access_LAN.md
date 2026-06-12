---
title: "Changed LAN card, now can't access LAN"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by jomob on 2007-01-18
I had to change the (wired) LAN card to a different brand and now I can't access the LAN.  It works fine when I boot from the LIVE CD but not when I boot from the hard drive (that my brother-in-law installed for me).  Do I have to reinstall ubuntu to get the new LAN card to work?

---

### Post by makan on 2007-01-18
what is your current LAN card type/version?
it seems the kernel module for your LAN card is not loaded.

---

### Post by davebgimp on 2007-01-18
Check here to see if this new card is supported or has workable issues:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by jomob on 2007-01-18
The new card is a D-Link DFE-530-TX Plus.  The ubuntu install was done when a NDC 10/100 F/E card was in the PC.  Per the website, the D-Link card is supported and there are no issues.  It works fine when I boot from the ubuntu "live CD" (5.1) that my brother-in-law left me.  I'm now running 6.06 installed on the HD.

The reason I need to switch cards is that I'm trying to get an old Pentium 166 machine up with linux and the only extra LAN card I have around is the D-Link (which requires an 300MHz processor).  The NDC card works fine in the 166.  Now I want to get the D-Link card working in the P866 ubuntu machine.

---

### Post by jomob on 2007-01-18
Oops.  On my previous reply I said I was running ubuntu 6.1 which is wrong.  I'm running 6.06.  Still having the problem.

---

### Post by jomob on 2007-01-19
OK, you folks must have put me in the penalty box for saying that I was running 6.10.  It was a mistake;  I was running 6.06 and I eventually corrected the post. I understand that 6.10 is NOT for newbies.

Anyway, I was able to fix the problem by reinstalling 6.06.  I'd still like to know if there is a way to reconfigure the NIC card (in case this one fails and I need to replace it with another model).

Thanks,
jomob

---

