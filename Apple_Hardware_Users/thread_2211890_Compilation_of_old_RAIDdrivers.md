---
title: "Compilation of old RAID*drivers ??"
date: 2014-03-18
forum: Apple Hardware Users
---

### Post by Vincen_PUJOL on 2014-03-18
Hi

I switched my MacPro early 2008 from OSX to Ubuntu with a lot of success. I have one issue with my Raid Card in the MacPro. It's a Caldigit one and manufacturer supplies source files to compile driver on Linux but they are pretty old and don't compile on current Linux versions :( Drivers are avalaible on this link: [http://www.caldigit.com/support/CalDigit2.0.2.zip](http://www.caldigit.com/support/CalDigit2.0.2.zip)
Any idaes what to change in the Makefile to succeed to compile it ? as I'm definitively not a programmer :(

Thanks

---

### Post by lukeiamyourfather on 2014-03-18
I would send a support request to the manufacturer asking for them to update the drivers. If they won't play ball you'd be better off buying a RAID controller from a different manufacturer and moving on. Alternatively you could use a distribution with a kernel that's supported by the drivers, looks like it was written for version 2.4 of the kernel which predates the existence of Ubuntu (all versions).

---

### Post by Vincen_PUJOL on 2014-03-19
> **lukeiamyourfather said:**
> I would send a support request to the manufacturer asking for them to update the drivers. If they won't play ball you'd be better off buying a RAID controller from a different manufacturer and moving on. Alternatively you could use a distribution with a kernel that's supported by the drivers, looks like it was written for version 2.4 of the kernel which predates the existence of Ubuntu (all versions).
For manufacturer product doesn't exist since nearly two years already :(
I won't change of Linux distribution for this card so I guess I should search for an other hardware solution :(

Thanks

---

