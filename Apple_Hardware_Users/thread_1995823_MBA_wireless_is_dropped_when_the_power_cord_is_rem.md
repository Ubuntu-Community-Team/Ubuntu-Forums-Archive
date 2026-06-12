---
title: "MBA wireless is dropped when the power cord is removed"
date: 2012-06-03
forum: Apple Hardware Users
---

### Post by shinkansen on 2012-06-03
I have an odd but crippling problem with my MBA running kubuntu 12.04.  When the power cable is removed the wireless network is dropped and all connections are lost.  If I reconnect the power then the network fires up again (the  existing connections eventually resume but it is very slow).

I have no network prior to plugging in.  The machine is new and I haven't noticed this problem before but it is remotely possible that I never tried to use the network before without the power connected.

I found some posts relating to power management events in k10.10 and tried these fixes but they made no difference.  There is no information in syslog / dmesg that relates to this and I'm stumped.  

Anyone have any clues? I'm stumped. I have an MBP running K11.10 (previously 10.10) and this does not have this problem.

---

### Post by shinkansen on 2012-06-04
Ok - I've found the offending script and bodged it - fix posted here:

[http://ubuntuforums.org/showthread.php?t=1996291](http://ubuntuforums.org/showthread.php?t=1996291)

I do not know what the other consequences of this bodge are hopefully someone will help there...

---

