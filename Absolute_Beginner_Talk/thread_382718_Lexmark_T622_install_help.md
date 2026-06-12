---
title: "Lexmark T622 install help"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by colby.westerfield on 2007-03-12
I just installed Ubuntu on my work machine and I need to get my network printers installed. We have a t622 that I need to be able to print to and I can't figure it out. I have downloaded the .deb file from lexmark that is supposed to have the driver in it but I don't know where to go from here.

Thanks

---

### Post by John.Michael.Kane on 2007-03-12
This should help.
[NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

---

### Post by colby.westerfield on 2007-03-12
I looked through all the instructions and that seems to be to make one machine share the printer. This printer has it's own server. I just want to connect through ipp but the driver doesn't show up for this model. The download is 

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:86:0:0&emeaframe=&fileID=6083&searchLang=en&searchLang=en&os_group=Debian%20GNU](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:86:0:0&emeaframe=&fileID=6083&searchLang=en&searchLang=en&os_group=Debian%20GNU)

I have d/led and installed this package but the 622 still doesn't show up in the driver list.

---

### Post by John.Michael.Kane on 2007-03-12
You can try clicking on system-administration-printing from there you should see box open.

click new printer go through the steps. this should allow you to pick your printer ,and install it with the driver you downloaded as well show it a shared printer ect.

This may be needed if the printer is installed but not set to be shared:
Click global settings share printers.

---

### Post by colby.westerfield on 2007-03-12
where would the driver be if I let the installer do it's thing?

---

### Post by colby.westerfield on 2007-03-13
Plissken so far has helped he greatly, now I just need to know the process of pulling the driver from the deb file and installing the printer. Any help will be greatly appreciated.

---

### Post by haelters on 2007-03-13
If I'm not mistaking, the only thing you need is a pdd file. It can be found here:
[http://lprng.sourceforge.net/DISTRIB/RESOURCES/PPD/LEXMARK/LEXT622.PPD](http://lprng.sourceforge.net/DISTRIB/RESOURCES/PPD/LEXMARK/LEXT622.PPD)

when you then go to the printer management, System->administration->printing, add a new printer,  select ipp printer with ip address, and on the next screen select the install driver button. Go and look for the ppd file you have downloaded and it should continue just fine. 

Let me know if you did not succeed.

---

### Post by colby.westerfield on 2007-03-13
Unfortunately this still isn't working. I did a port scan on the printer and both 515 and 613 are open and the driver seemed to work, for some reason when I try and print a test page it says job-hold-until-specified. Anything else I might need to do?

---

### Post by haelters on 2007-03-13
Did you restart the cups daemon ? I also had this problem and after a reboot I saw that suddenly it was working. Normally a restart of the cups daemon should have done the job.

---

