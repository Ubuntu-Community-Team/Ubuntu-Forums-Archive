---
title: "BIOS upgrade under Linux?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Cartwheels4amile on 2006-08-11
Hey everyone,

I'm running Xubuntu 6.06.1 on a Toshiba Portege 7140ct. I recently got a new hard drive, but all I know about it is that the model number is MK4025GAS.

My system's BIOS doesn't recognize the drive](*,) , and I was wondering two things:

1. Will a BIOS upgrade allow my system to use the drive?
2. Can I upgrade the BIOS under Linux, since it's the only OS installed on the system?

Any help is MUCH appreciated. :grin:

---

### Post by wpshooter on 2006-08-11
Your best source for this information is on the Toshiba website.

Hopefully your BIOS can be updated using either a bootable floppy disk or a bootable CD-Rom which the Toshiba site should give you instructions on creating.

My **guess** is that you will not be able to strictly do a live BIOS update from within Ubuntu like you might from with in M/S windows.  

However having said that, I would never recommend updating the BIOS from a running O/S in any case.  Always update BIOS from diskette, IMO.

---

### Post by whein on 2006-08-11
Google is your friend.  :)
> The MK-4025GAS is a 2.5 inch embedded hard disk drive for advanced mobile computing and sophisticated multi-media applications. The drive features Toshiba's premier 40GB per platter technology (1 platter, 2 heads) making it one of the most advanced HDD available in this form factor.
[http://www.toshiba-europe.com/storage/pci.asp?page=PCI=ISH_PRS&stype=product&model=MK4025GAS]("http://www.toshiba-europe.com/storage/pci.asp?page=PCI=ISH_PRS&stype=product&model=MK4025GAS")
Looks like they have a technical specs page that lists cylinders and platters and heads, oh my!
-Will

---

### Post by wpshooter on 2006-08-11
I don't think the hard drive is a problem.

Seems to me that they problem need info on updating BIOS, so hard drive is recognized.  Just go to toshiba website and look for bios upgrades for your machine model.

---

### Post by Cartwheels4amile on 2006-08-11
Well, bad news guys. I updated the bios successfully (turns out the .exe file from toshiba just creates a floppy... so I used a windows pc to do that) but my HD is still not being recognized. It's not that big of a loss, seeing as I got it for free.

What's odd though, is it works fine in an older Toshiba Tecra 530cdt I have lying around. No idea what that's about, since that computer is so old it's barely usable. Thanks for the help, guys.

---

### Post by whein on 2006-08-14
Have you tried manually setting the HD parameters in the bios instead of using the autodetect?  Sometimes drives will work this way even if the autodetect can't recognize them or gets the info wrong.
-Will

---

