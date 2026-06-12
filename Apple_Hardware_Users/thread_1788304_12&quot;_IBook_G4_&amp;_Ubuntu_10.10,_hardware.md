---
title: "12&quot; IBook G4 &amp; Ubuntu 10.10, hardware?"
date: 2011-06-22
forum: Apple Hardware Users
---

### Post by Ottis on 2011-06-22
Someone gave me an 12" iBook G4 that wouldn't boot, no OS disks but otherwise ok.

This is my first Apple/ Mac product so I'm kind of learning as I go, I'm a casual Ubuntu user, so I'm still learning on that front also.

So, I wasn't able to fix the boot problem on the Mac OS so i downloaded Ubuntu 10.10 for PPC, installed it, messed up something, reinstalled it and it's now working, although with a few well known bugs. (no flash support, battery monitor (?) or sleep mode) 

My 1st question is; how can I find out just what hardware my G4 has? There's no model number on the case that I can find. Is there a utility or app I can run to see what hardware it's equipped with, ie processor speed, cd/dvd burner, RAM etc. 

Q #2; assuming it has a cd burner, can U 10.10 burn CDs bootable on a iBook from a .dmg file? I would like to be able to dual boot Ubuntu and the original Mac OS if possible. 
I am still running Ubuntu 8.04/ Win XP on my desktop, it does have a CD/DVD burner, but would the different hardware keep it from burning a Mac bootable disk?

Thanks in advance for any help and tips!:)

---

### Post by holastickboy on 2011-06-23
The page that I am about to link to does not 100% relate to PowerPC stuff, but should give you some idea if you try the terminal commands.  Basically it breaks up each component with a terminal command.  Give it a try and see how you go!

[http://cviorel.easyblog.ro/2008/02/19/get-system-information-using-the-terminal/](http://cviorel.easyblog.ro/2008/02/19/get-system-information-using-the-terminal/)

---

### Post by linuxopjemac on 2011-06-23
Ad 1: It should have a Model Number somewhere on the bottom of the iBook, google it in combination with everymac.com. You'll end up with your machine.

Ad 2: Consider [http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/) dmg2img may convert a .dmg file (which is a proprietary Apple format) into an .img file which can be burned from within Linux.
Documentation for Ubuntu: [https://help.ubuntu.com/community/DMG2IMG](https://help.ubuntu.com/community/DMG2IMG)

---

