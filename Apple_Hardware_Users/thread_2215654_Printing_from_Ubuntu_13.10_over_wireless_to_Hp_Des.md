---
title: "Printing from Ubuntu 13.10 over wireless to Hp DeskJet F2480 on Mac"
date: 2014-04-07
forum: Apple Hardware Users
---

### Post by Michael_OSullivan on 2014-04-07
Hi, hope this is the correct forum for this.

I'm having difficulty using a printer that's attached to a Mac by USB.

The Printer is a HP DeskJet F2480 and is attached to an iMac running OS X 10.9.2 (Mavericks). I have set up printer sharing on the Mac.

I'm running Ubuntu 13.10 on a Lenovo E530 laptop. I can use the System Settings wizard to identify the IP address of the printer and it will print a simple text-only test page (which appears to be generated from a PDF). However, when I use the wizard's database of drivers to identify it as a HP Deskjet F2480, the test page gets stuck and an error message indicates that something (the Mac? Ububtu?) can't open a file in /private/var/spool/cups/temp/. I have also tried to configure the printer on Ubuntu using CUPS and the HP utility, with the same result.

Has anyone dealt with (and hopefully solved!) anything like this?

---

### Post by bapoumba on 2014-04-07
This file is from the Mac side of things. How did you share your printer ? [http://support.apple.com/kb/PH13940?viewlocale=en_US](http://support.apple.com/kb/PH13940?viewlocale=en_US)

---

### Post by Michael_OSullivan on 2014-04-08
Hi Bapoumba, thanks for your reply.

I shared the printer on the Mac by selecting the 'Share with Everyone' option outlined in Steps 1 & 2 on the page you linked to.

J'aime aussi les fraises!

---

### Post by bapoumba on 2014-04-08
Which printing protocol are you using on the Mac ? I think I had to use IPP (you can choose it when installing the printer).

Moving to Apple Users.

---

### Post by Michael_OSullivan on 2014-04-08
I've tried https, ipp and ipps using the format:

[protocol] ://192.168.10:631/printers/HP_Deskjet_F2400_series

The IP address is that of the Mac. The ":631" was prompted by using CUPS to identify the printer. 

It may be significant that it prints a simple text-only test page ("default-testpage.pdf") if I don't choose a driver from the Ubuntu database. Could it be something to do with the PPD?

I should add that I also tried changing Sharing on the Mac to allow Remote Management (specifically, Change Settings), but that didn't make any difference.

---

### Post by bapoumba on 2014-04-08
Unfortunately, I wont get close to my Mac station at work until tomorrow, I'll have a look at the settings I used (provided I have not done anything past the moment when I had to use my personal laptop at work, and provided it was for a different printer. Anyway, I ended up using the OpenPrinting Linux driver on the Mac, as the default Mac one did not handle some features as staples and such).

If the Mac prints fine, I'd say it has to do with either the driver used on Ubuntu or the sharing on the Mac, but it seems you did it ok.

[https://www.openprinting.org/](https://www.openprinting.org/) recommends hplip driver for models close to yours, is this the driver you are using on Ubuntu ?

---

### Post by Michael_OSullivan on 2014-04-08
Thanks, I appreciate the help.

Because the error message said that [something] couldn't open a file in /private/var/spool/cups/temp/, I did a bit of digging to try to see what might turn up.

Both the Mac and Ubuntu laptop are running CUPS 1.7.1. However, the only reference in the CUPS documentation site that discussed that temp directory was in the discussion of the cupsd.conf file for CUPS version 1.5: see [here]("http://www.cups.org/documentation.php/doc-1.5/ref-cupsd-conf.html#TempDir").

That directory exists on the Mac and (contrary to what the 1.5 documentation suggests) was not "world-writable", so I tried the chmod command they suggest at that link. That went through without difficulty, but didn't solve the problem - I still got the error message on the laptop when I reinstalled the printer, selected the driver and tried to print a test page.

So is the problem a lack of access or permissions to that temp directory on the ubuntu machine? There's no sign of a /private/ directory, even when I tell Nautilus to show hidden files etc. So I tried creating /private/var/spool/cups/temp/ and setting permissions to so that anyone could write, but that didn't fix it.


Perplexed....

PS: I should add that the cupsd.conf file on the Ubuntu machine has no entry for TempDir. I tried adding one, but the same error ("Can't open /private/var etc etc") recurred.

---

### Post by Michael_OSullivan on 2014-04-08
Concerning HPLIP, I've tried using it but it can't discover the printer. I've tried setting it up manuall by giving it the IP address but it doesn't accept it. I can't find any HP documentation that discusses that problem!

---

### Post by bapoumba on 2014-04-09
Would your firewall on the Mac be blocking the incoming traffic or not allowing access to the required files ?
Sorry, but the settings I had used are unfortunately gone (as I suspected). 

Please have a look at Console > cups (may be start with access_log) on the Mac and see if the errors you get are documented there. With a precise error, maybe it will be easier to pinpoint what is not working. /private/var/spool/cups/ cannot be opened by my regular user here, I need root access.

---

