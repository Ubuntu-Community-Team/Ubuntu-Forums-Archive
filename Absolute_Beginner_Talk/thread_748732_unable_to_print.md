---
title: "unable to print"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by ockron on 2008-04-07
Hi all.

I installed Feisty on my desktop that I share over a wireless network with 2 XP laptops.
I attached my printer to the desktop and created a shared drive on the desktop.
I was able to solve the pw problem when trying the browse the desktop.

I am still unable to share the printer.
I have tried this thread [https://help.ubuntu.com/community/Ne...ntingFromWinXP](https://help.ubuntu.com/community/Ne...ntingFromWinXP)
BUT my cupsd.conf file does not have the "Listen" configurations.

> LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
# Allow shared printing...
Order allow,deny
Allow @LOCAL
</Location>
<Location /admin>
Encryption Required
Order allow,deny
Allow localhost
</Location>
<Location /admin/conf>
AuthType Basic
Require user @SYSTEM
Order allow,deny
Allow localhost
</Location>
<Policy default>
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
AuthType Basic
Require user @SYSTEM
Order deny,allow
</Limit>
<Limit Cancel-Job CUPS-Authenticate-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit All>
Order deny,allow
</Limit>
</Policy>
Printcap /var/run/cups/printcap

Is there anyone that can help me please.

Thanx!!

---

### Post by stchman on 2008-04-07
> **ockron said:**
> Hi all.

I installed Feisty on my desktop that I share over a wireless network with 2 XP laptops.
I attached my printer to the desktop and created a shared drive on the desktop.
I was able to solve the pw problem when trying the browse the desktop.

I am still unable to share the printer.
I have tried this thread [https://help.ubuntu.com/community/Ne...ntingFromWinXP](https://help.ubuntu.com/community/Ne...ntingFromWinXP)
BUT my cupsd.conf file does not have the "Listen" configurations.



Is there anyone that can help me please.

Thanx!!

If you are wanting to share a printer attached to an Ubuntu machine over a network that is actually really easy.  Samba is not needed.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

---

### Post by superprash2003 on 2008-04-07
go to the terminal and type sudo gedit /etc/samba/smb.conf

then look for this line
;  printing = cups
 ;  printcap name = cups

replace it by removing the ; from the line
  printing = cups
   printcap name = cups

save it and reboot samba by typing sudo /etc/init.d/samba restart

---

### Post by ockron on 2008-04-07
> **superprash2003 said:**
> go to the terminal and type sudo gedit /etc/samba/smb.conf

then look for this line
;  printing = cups
 ;  printcap name = cups

replace it by removing the ; from the line
  printing = cups
   printcap name = cups

save it and reboot samba by typing sudo /etc/init.d/samba restart

I followed the instructions, but allas when I open the printer in XP it tells me "access denied, unable to connect".

---

### Post by superprash2003 on 2008-04-08
have you setup samba correctly? like creating samba users and adding them to the list? check here [http://ubuntuguide.org](http://ubuntuguide.org) -follow the samba tutorial

---

### Post by stchman on 2008-04-08
> **superprash2003 said:**
> have you setup samba correctly? like creating samba users and adding them to the list? check here [http://ubuntuguide.org](http://ubuntuguide.org) -follow the samba tutorial

You don't need Samba to print to a printer attached to an Ubuntu machine.

---

