---
title: "[SOLVED] Printing by ethernet"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Robert Ashley on 2008-02-14
My problem is getting my printer to work.
The printer is a HP Laserjet 5P, which has a parallel interface.
I wish to be able to print from Ubuntu Linux, from an ethernet port using a HP Jetdirect 170x converter, ethernet to parallel.
This connection works OK from Win XP dual boot on the same computer.
I have not been able to find the correct settings in linux to get linux to recognize the printer.
Here is a copy of the settings from smb.conf, that pertain to printing.
-----------------------------------------------------------------------
   load printers = yes
   printing = cups
   printcap name = cups
########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
  printing = cups
  printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = yes
   guest ok = yes
   writable = no
   create mask = 0775

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /etc/samba/drives
   browseable = yes
   read only = yes
   guest ok = no
   write list = root
-------------------------------------------------------------------------
Choosing "System",Administration,Printing,New Printer,AppSocket/HP JetDirect" in that order,
shows 8 choices for an HP LaserJet printer. None of those choices allow the HP to be recognized.
I am obviously missing something, or have made a bad choice.
If any one has been successful in getting a similar configuration to work, please tell me how it is done.

---

### Post by Tteddo on 2008-02-14
If you click on AppSocket/HP JetDirect you should be able to put the IP address of the printer in where it says host and just use the default port.
In Windows XP you can go to the printer properties and ports and you should be able to see the IP Address of the printer.

---

### Post by Robert Ashley on 2008-02-15
Thanks very much. It works just as you said.
You made my day!

---

### Post by Tteddo on 2008-02-15
Cool! Glad to help!!

---

