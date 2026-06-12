---
title: "local printing w/ HP laserjet 1100"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by RH9R on 2007-04-15
After changing systems, I find the install did not detect & configure the local printer - it did on the last box. 
 
I went to the setup wizard, which prompts for a PPD file. It doesn't say what a PPD is, or give you a 'back' option for when you don't have or can't find one. I downloaded the HP laserjet PPD file to desktop and it says its successfully installed, but no joy when I try to print an Open Office doc. I went though the wizard again, pointing to the new PPD file, and the wizard completed, and looked successful - but no print. 
 
Any help troubleshooting would be appreciated. Many Thx, all.

---

### Post by tchoklat on 2007-04-15
do you need to intall the CUPS driver?

---

### Post by RH9R on 2007-04-16
Thank You for responding. I appreciate your help.
 
I didn't think to check for CUPS 'cause on my last box, it detected the printer, driver, etc. and worked fine from the start. 
 
I checked synaptic, and there were other cups packages not loaded. I selected all that seemed to fit, and restarted. I tried a test page that contained text and links. It printed about the first 12 lines and only 1/2 of a line and none of the rest of the page. Its bizarre. 
 
 If there's a troubleshooting routine, I'd like to go through it. 
 
Again, thank you for the help.

---

### Post by ramjet_1953 on 2007-04-17
If you follow this link, it should get you going:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1100](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1100)

Regards,
Roger :)

---

### Post by RH9R on 2007-04-23
I installed the driver, but no joy. 
 
I'm wondering if the install process was correct. If not, how to uninstall the ppd.
 
There seem to be alot of ppd files in usr/share/ppd - many of which seem not to apply - can they be deleted?
 
The notes in the ppd file itself reference the need for a backend filter script.
 
"The printer must be configured with the
*% "foomatic-rip" backend filter script of Foomatic 3.0.0 or newer."
 
I checked and installed foomatic, but there seems to be no foomatic package component called 'foomati-rip'. Cancel that - a search shows foomatic-rip in usr/bin.
 
Any ideas? 
 
Again, thank you for your help.

---

