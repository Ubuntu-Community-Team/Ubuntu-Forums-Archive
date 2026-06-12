---
title: "Multicard reader?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-09-21
I have a multicard reader in my hp laptop, any idea on how to get it mounted? I dont know the name of it or such, but it comes with the hp laptop and its a 7 (or 6) in one kind of thing.

---

### Post by davmac on 2006-09-22
Hi,

It depends what sort of card reader it is. I was trying to do this with my Asus S6F laptop yesterday, but found that my card reader is not supported by Linux at all. I was lucky that I'd got an external card reader collecting dust at the back of a drawer.

The way to track down more information about it is to open up a terminal window and to type "lspci". You should see details of your card reader here.

Mine is a Ricoh based one and I was able to google for more information about it. You may be lucky and find that yours can be set up to work.

You could also post back the output of lspci here, and somebody may be able to help.

Regards,

Dave Mac

---

### Post by maestrobwh1 on 2007-11-10
similar issue

I used 
pccardctl insert
then
pccardctl status 
and got
Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "pata_pcmcia"

so it is there 

It has an xD card in it, but from here, I am not sure how to proceed to "mount" it?

I tried looking in disks in systemsettings: nothing new there.

---

