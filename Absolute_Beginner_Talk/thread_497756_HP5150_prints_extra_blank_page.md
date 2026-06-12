---
title: "HP5150 prints extra blank page"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Astrikor on 2007-07-10
Hi

I am new to ubuntu, having moved over from xp, but my 5150 installed beautifully - except that it prints out a blank page following any printing job - from openoffice or from gedit.
I installed from "add printer" 
Should I have used the 5150 cd ?

Any ideas?
Thanks
Astrikor

---

### Post by wpshooter on 2007-07-10
No I doubt you can use the CD.

Have you looked at the paper type, i.e. letter, legal, etc. etc. and have you look at the page length setting in the printer property settings.

Good luck.

---

### Post by doncristobal on 2007-07-12
I have the same problem with a hp laserjet 1200 connected by usb to a siemens gigaset sx541 router. 

paper size is correct (a4). what else could it be?

---

### Post by Astrikor on 2007-07-16
> **wpshooter said:**
> No I doubt you can use the CD.

Have you looked at the paper type, i.e. letter, legal, etc. etc. and have you look at the page length setting in the printer property settings.

Good luck.


Have checked all these - seem ok

Printing a test page via System/Admin/Printing/...etc prints ok, just the test page.

Printing anything from openoffice or gedit follows the documents with a spare blank sheet.  How do I stop it?

Any more ideas??

Thanks
Astrikor

---

### Post by Astrikor on 2007-07-16
Finally I have found the answer:

Select System/Administration/Symoptic Package Manager and nstall python-qt3

Then select System/Preferences/HPLIP Toolbox (On my system this found the HP5150 printer which I had previously installed using System/Administration/Printing/Printer/Add Printer)
Select the printer required and contiunue to complete the installation.

This automatically printed out a test page satisfactorily.

Note that the System/Preferences/HPLIP Toolbox also gives access to printer setup and utilities.

Also,  gedit and openoffice no longer print a spare blank page.

Sorted!

Maybe this will help others.

Astrikor

---

