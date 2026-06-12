---
title: "HP OfficeJet 5610 Issues"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by FiremothPilot on 2007-09-05
Recently bought a HP OfficeJet 5610. I'm running both WinXP and Ubuntu 7.04; installed all drivers, etc. in Windows for the printer. Also found all packages needed to run HP printers.

Cannot print from OpenOffice or from an image viewing window. When I pull up the printing menu through 'System>Administration' on the panel, the printer reads as 'Ready'. However, when I look at its properties, status reads as follows:
'Ready: open device failed; will retry in 30 seconds...'

While I can't seen to print anything, scanning is a breeze. All I do is open XSANE and press 'Scan' and get almost immediate results.

Anyone know what is going on?

---

### Post by dwhitney67 on 2007-09-06
Seems like you did a fine job installing the printer (and related drivers) under WinXP.  What about for Ubuntu??  Your post does not mention anything concerning this.  Did you go to **System -> Administration -> Printing** and create a printer handler?

Plus you might want to mention how you have the printer connected to your system.  Is it connected via USB?  The network?

If you have a dual-boot system, only one OS is active at a time.  Thus it is irrelevant what you have set up in WinXP.

---

### Post by Malta paul on 2007-09-06
Hi, Your printer type should run fine with Ubuntu.
Check out this link which will give you printer details and correct driver required:
 [http://www.openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_5610](http://www.openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_5610)
Good luck:)

---

### Post by FiremothPilot on 2007-09-06
> **dwhitney67 said:**
> Seems like you did a fine job installing the printer (and related drivers) under WinXP.  What about for Ubuntu??  Your post does not mention anything concerning this.  Did you go to **System -> Administration -> Printing** and create a printer handler?

Plus you might want to mention how you have the printer connected to your system.  Is it connected via USB?  The network?

If you have a dual-boot system, only one OS is active at a time.  Thus it is irrelevant what you have set up in WinXP.

If you mean 'Add Printer...', etc., then yes, I have completed that step.

As I say, I am able to scan without error. Linux sees the printer in all applicable programs, but will not carry out the job.

The all-in-one is connected via USB.

---

### Post by str8line on 2007-09-06
Had similar problems with an old school Cannon printer before we upgraded to an HP.  You may want to install using the HPLIP version of the drivers during the add printer wizard.  I have found that the drivers are a bit more responsive using that option.

---

### Post by FiremothPilot on 2007-09-06
> **str8line said:**
> Had similar problems with an old school Cannon printer before we upgraded to an HP.  You may want to install using the HPLIP version of the drivers during the add printer wizard.  I have found that the drivers are a bit more responsive using that option.

I'm pretty sure I installed all of the HP*** drivers through Synaptic PM.

Are there further steps to installing these drivers?

---

### Post by str8line on 2007-09-07
When you Add the Printer choose the HP*** file option...this should help.  As another option going to [linuxprinting.org]("http://www.linuxprinting.org") will allow you to download the specific driver and then direct the add printer to that file during the Add Printer Wizard.

---

