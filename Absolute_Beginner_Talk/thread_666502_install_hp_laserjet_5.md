---
title: "install hp laserjet 5"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by stevek28 on 2008-01-13
I am running Ubuntu 6.06.  I can't seem to install drivers for my hp laserjet 5.  Would someone please help me!!

thanks in advance

---

### Post by edm1 on 2008-01-13
The printer works perfectly with the HPLIP driver. It is installed by default in Ubuntu 7.10 but i dont know about 6.06. Open Synaptic (System>Admin>Synaptic) and search for 'hplip'. If the driver is installed it should just be a matter of plugging your printer in and configuring it in System>Admin>Printing.

---

### Post by ajgreeny on 2008-01-13
You may need to try downloading the newest version of hplip from the sourceforge site.  There's a link to it on the HP hplip page but be warned, it doesn;t always play fair with older packages.  I tried it for a HP Deskjet F2180, and though the hplip package installed OK it wouldn't run that printer on my wife's laptop with 7.04.  Unfortunately the hplip in that version of ubuntu is the one just before the printer was supported.

I ended up upgrading her system to 7.10, and now everything works beautifully.  2 hours from start to finish, including doing a full backup of /home to an external usb drive, resizing the windows partition now it is not needed so much, installing system including updating everything and then reinstalling all the packages needed using aptoncd from my own fully updated system.

Try doing that in windows!  you'd be lucky to get it running in twice that, I reckon.

EDIT.
I've just had a quick look and I think the version of hplip in 6.06 should be OK for that printer.

---

### Post by stevek28 on 2008-01-13
> **ajgreeny said:**
> You may need to try downloading the newest version of hplip from the sourceforge site.  There's a link to it on the HP hplip page but be warned, it doesn;t always play fair with older packages.  I tried it for a HP Deskjet F2180, and though the hplip package installed OK it wouldn't run that printer on my wife's laptop with 7.04.  Unfortunately the hplip in that version of ubuntu is the one just before the printer was supported.

I ended up upgrading her system to 7.10, and now everything works beautifully.  2 hours from start to finish, including doing a full backup of /home to an external usb drive, resizing the windows partition now it is not needed so much, installing system including updating everything and then reinstalling all the packages needed using aptoncd from my own fully updated system.

Try doing that in windows!  you'd be lucky to get it running in twice that, I reckon.

EDIT.
I've just had a quick look and I think the version of hplip in 6.06 should be OK for that printer.

I ran the installer package (hplip) and it installed the drivers.  I chose the hp and the default printer.  However, when I try to print an office document or a test page, the printer goes in to pause mode and nothing happens.  Even if I choose to resume the job, in 5 seconds the printer returns to pause mode

---

