---
title: "Recognizing a 'new' PC Card modem"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by brn on 2006-08-18
I have a 2nd-hand Dell laptop with Windows XP and Dapper.  Confined to 56 Kb I aquired a PC Card modem (3Com) which works with XP but I cannot get Dapper to recognize. When I installed Linux I did not have the PC Card in place and answered "no" to the question about "network".  Should I re-install to make it work?  Is there a "new hardware" search that I don't know about?

I am thinking about re-installing Breezy.  Frantic things have been done (like installing KDE) because of a bizzare incompatibility with this (Dell) computer.  I found the solution on this forum and Oh Boy am I ever grateful!  Also, the disk partitions I had made for Breezy have been ignored by Dapper.  This is a separate issue but I appreciate any comment on either subject.

Thanks!

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
Saying that it is a Dell unfortunately doesn't help much, because they make lots of computers. At this moment, I'm writing on a Dell Inspiron 6400, which came with an internal modem that shows up as a working device in the network configuration. I have never used it, though.

All drivers are, as far as I know, part of the Linux kernel, so it should work once you've plugged it in, if the device is supported. There could be written some code to get it running which is not yet included in the official kernel distribution, which you could find by searching for your modem's chipset, but then you'd have to compile the kernel yourself afterwards to add support for it.

I remember being told to recompile my kernel when attempting to get wifi working under GNU/Linux about three or four years ago, and that really put me off back then.

Anyway, if you figure out the modem's chipset, it would be easier to research wether it is possible to use in Ubuntu or not! I know 3com often switch chipsets, so you should start with the model number.

---

### Post by brn on 2006-08-18
> Saying that it is a Dell unfortunately doesn't help much 
I guess you're right.  This is a *Latitude CpX-650* manufactured I think around 2003.  At least that's what the copyright date on the BIOS shows.  At one time I thought I had the PC Card modem working (it does now with Win-XT) but I had the wrong cable (they sold me one intended for Ethernet! ...Grrrr...). That was before I took off trying to resolve the Dell-related problem mentioned before which has messed-up many things.  This is why I think re-installing Breezy might get me back to somewhere somehow familiar.  I guess I can either do this now and lose what I have accumulated or do it later and lose more. 
Not a happy choice.

---

### Post by &#12465;&#12452;&#12488; on 2006-08-18
You can configure the partitions which should be (and where they should be) mounted using the Discs Manager, found in System &#8594; Administration &#8594; Discs.

As for the KDE thing... I'm not sure. What happened?

---

