---
title: "HPLIP Toolbox and Hp Deskjet 5940"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Healey on 2006-09-04
Hi
I have recnetly purchased a printer - HP Deskjet 5940

I have installed it in gnome using SYSTEM, Admin - Printing, Then ADD Printer.

All is well, I selected local printer (The printer is connected directly to the USB port) and it worked stright away and I have a nice test page.

I also did the same thing with my laptop over a wireless network - the only difference is that I selected network printer using samba and that worked perfectly too. So I am very happy

The trouble is I would like to use HPLIP Tolbox so that I can set the printer up and moinitor ink levels and so on. 
 When I use the HPLIP it tells me that "No installed HP Devices found and it tells me that I must go to the CUPS Web interface. If I click to go there, the web page can see my printer perfectly

What am I doing wrong ???

I am using Dapper 

Best regards

Healey

---

### Post by Healey on 2006-09-04
Hi

For anyone interested in this thread 

After even more time with google i have found a solution

When Installing the printer as above two options for driver are listed for this printer. One with undescores and one without.

I originally chose the first one - HPLIP Toolbox did not work

I then chose the second choice with underscores - It DID work

I dont know how accurate the ink levels are - Time will tell I guess

Thanks

Healey

---

### Post by jbonll05 on 2006-09-04
Healy;

   Thanks for the research, I have two HP printers and was getting ready to try to get the "Tool gox" working in U-6.06.1. 
JB, Ubuntu user

---

### Post by lightubun on 2006-09-04
you can find the answer here [https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

summary
befor you add printer
type 
> $ lpinfo -v
network socket
network beh
network bluetooth
direct usb://HP/DeskJet%203820?serial=CN2A61N13N18
direct [COLOR="RoyalBlue"]**hp:/usb/DESKJET_3820**[/COLOR]?serial=CN2A61N13N18
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
direct canon:/dev/usblp0
direct epson:/dev/usblp0
network smb

in autodetect choose.. in your case
HP DESKJET_5940
not
HP Deskjet 5940

in model choose
Deskjet 5940

good luck

---

### Post by Healey on 2006-09-04
Hi

Thanks for that - works a treat

Regards

Healey

---

### Post by almalaci on 2006-11-10
I have my printer installed over the network manually and hp-toolbox doesn't find a device. It prints, scans fine but there is no printer autodetect during setup and lpinfo -v doesn't bring back anything useful about my printer (other than direct hp:/no_device_found).
So the above method didn't work for me.
Any other ideas how to get hp-tools detect my printer/scanner?

---

