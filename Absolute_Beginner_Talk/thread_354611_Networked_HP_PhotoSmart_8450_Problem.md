---
title: "Networked HP PhotoSmart 8450 Problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2007-02-06
I have an HP PhotoSmart 8450 connected directly to my home network using the RJ-45 port on the printer.  I have assigned the printer an IP (static) address which is in my subnet mask range.  The printer IP address may be successfully 'pinged'.  The printer also works in (dare I say it) Windows XP. I have seen post on this forum from the past indicating that some of you have this same printer working successfuly.  My first question would be: Does anyone have this printer working as a network printer rather than the USB port on the printer?

I suspect I am soing something wrong on adding the printer.  My procedure:
Double click "New Printer"
Click Network Printer with "CUPS Printer (IPP) selected in the drop-down.
Enter the IP address of the HP PhotoSmart 8450
Click Forward
Select "HP" in Manufacturer, and "PhotoSmart 8400" in Model
The only driver is: hpijs (recommended) - HPLIP 0.9.7 (Suggested)
Click Forward
Type in the Description and Locations of the printer
Click Apply

At this point the "Printers" windows shows the PhotoSmart-8400 as Ready.  However, when I right-click the printer ICON, and then select Properties, and then click "Print a Test Page" is get absolutly nothing.  No printer activity, no activity on my HUB.  Do any of you experts see anything that I am doing incorrectly?  Any advice, solution, etc would be most appreciated.

---

### Post by edwardLS on 2007-02-09
Problem solved.  I now have the HP PhotoSmart 8450 connected directly to my network and working well.  I can print a Test Page, and I was able to print a photo using The Gimp.

It appears that the 8450's network connection is just like a Single Port JetDirect Print Server.  When I click "Network Printer" radio button, I then click the drop-down and select "JetDirect".  This action fills in the port "9100" and awaits an IP address.  I entered the IP address (static) that I have set on the 8450, and continue to select the "HP" and "PhotoSmart 8400".

---

### Post by AJB2K3 on 2007-06-27
Sorry for the thread revival but this has just help me get mine working.

---

### Post by jremigio on 2007-12-14
This solution also worked for me and my standalone network printer, the Lexmark T520.

---

