---
title: "Mac can't connect to Ubuntu 7.1 network printer"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Chasing_Mosby on 2007-12-27
I set-up a HP 1310 printer on an old PC running Ubuntu 7.10 (Gutsy) . In System>Administration>Printing, I activated "Share published printers connected to this System" . Under the local printer tab "policies states the boxes for "Enabled", "Accepting jobs" and "Shared" are all checked. My MacBook cannot see the printer in the "add printer" box. The CUPS config in Ubuntu looks like this:

LogLevel info
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
# Restrict access to the admin pages...
Order allow,deny
Allow localhost
</Location>
<Location /admin/conf>
AuthType Default
Require user @SYSTEM
# Restrict access to the configuration files...
Order allow,deny
Allow localhost
</Location>
<Policy default>
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes
Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job
Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-
Class CUPS-Set-Default>
AuthType Default
Require user @SYSTEM
Order deny,allow
</Limit>
<Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job
Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-
Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
AuthType Default
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

I'm wondering if "Listen /var/run/cups/cups.sock" is correct? In previous posts configs have been changed to "Listen 631" - but that was for a older version of Ubuntu (and CUPS?) 
Any suggestions?

---

### Post by spiderbatdad on 2007-12-27
i have seen Listen Localhost:631 or Listen Localhost@631

you can try changing and saving those values. The best way is to comment the existing line, so you dont forget what it was. Then add the new line with a comment below # line above by me. You might have to reinstall cups for it to ever be right.

---

### Post by Tyke91 on 2007-12-27
also, its a good thing to know the ubuntu naming convention. Versions are based on the year and the month, so 7.04 came out 4/07 (april 2007), 7.10 came out in october. 7.1 would be january, which is incorrect. 

sorry to be nitpicky, but it's a pet peeve of mine and I'm sure it made some people cringe. 


anyway, listen to spidey   :)

---

### Post by Chasing_Mosby on 2008-01-03
Listen Localhost:631 or Listen 631 doesn't work. Will try and re-install CUPS

---

### Post by dr.nixon on 2008-01-08
Had the same problem, it drove me nuts. Try explicitly telling your server to listen to the IP address of your NIC. I have this working on my server but take note that using the config file below will allow all local users to access your printer. You will only be prompted to authenticate when adding or removing printers. All users will have full control of printers. With these settings both my OS X laptop and WinXP desktop can access the printer via IPP at [http://my.server.name:631/printers/name_of_printer](http://my.server.name:631/printers/name_of_printer)

Good luck with it. Again this works but is not secured. Fine on a closed network but otherwise use at your own risk.

ServerName your.server.name
ServerRoot /etc/cups
LogLevel warning
SystemGroup lpadmin
# Allow remote access, disable this if you want more security
Listen localhost:631
Listen your.eth0.ip.address:631
# If more than one NIC...
Listen your.eth1.ip.address:631
# etc., etc. - don't include eth0 if you are using server as a router unless you want external access to the printer
# If all else fails, just uncomment the following to listen on all NICs
# Listen *:631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
DefaultEncryption Never
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    # Require user @OWNER @SYSTEM
    Allow from All
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    # Require user @OWNER @SYSTEM
    Allow from All
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
    Allow from All
</Limit>
</Policy>

---

### Post by Chasing_Mosby on 2008-01-22
Thanks Dr Nixon...

but... I reinstalled CUPS after my last posting and no luck. Mac still couldn't find my  printer. Last week I installed 2 CUPS Ubuntu updates and DING DING DING, the Mac sees the remote printer in the drop down print box and I can print remotely ! The CUPS config still shows "Listen /var/run/cups/cups.sock" so whatever that fix was - it fixed my printer issue - thank you Ubuntu gurus!

---

### Post by stchman on 2008-01-22
> **Chasing_Mosby said:**
> I set-up a HP 1310 printer on an old PC running Ubuntu 7.10 (Gutsy) . In System>Administration>Printing, I activated "Share published printers connected to this System" . Under the local printer tab "policies states the boxes for "Enabled", "Accepting jobs" and "Shared" are all checked. My MacBook cannot see the printer in the "add printer" box. The CUPS config in Ubuntu looks like this:

LogLevel info
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
# Restrict access to the admin pages...
Order allow,deny
Allow localhost
</Location>
<Location /admin/conf>
AuthType Default
Require user @SYSTEM
# Restrict access to the configuration files...
Order allow,deny
Allow localhost
</Location>
<Policy default>
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes
Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job
Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-
Class CUPS-Set-Default>
AuthType Default
Require user @SYSTEM
Order deny,allow
</Limit>
<Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job
Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-
Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
AuthType Default
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

I'm wondering if "Listen /var/run/cups/cups.sock" is correct? In previous posts configs have been changed to "Listen 631" - but that was for a older version of Ubuntu (and CUPS?) 
Any suggestions?

Now that you have your printer shared in Gutsy you will need to enter the following line in whatever PC you want to connect to that printer in the networked printer URL box.

```

http://hostname:631/printers/<printer name>
```

Where hostname is the IP address of the PC that the printer is attached to.

<printer name> is the EXACT name of the printer Ubuntu has assigned to it.

ex:
Lets say the IP address of teh PC is 192.168.1.185 and the printer is named LaserJet-1000

```
http://192.168.1.185:631/printers/LaserJet-1000
```

Trust me this works.

I have a more detailed tutorial.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

---

### Post by Chasing_Mosby on 2008-01-23
Thanks Stchman !

Thats good to know - but the printer IS connected to the PC (win2k/Ubuntu dual boot) and I have no other, only MacBooks !
BTW - your website rocks - like to try to get those MS fonts set up in Ubuntu - great work!:)

---

### Post by stchman on 2008-01-23
> **Chasing_Mosby said:**
> Thanks Stchman !

Thats good to know - but the printer IS connected to the PC (win2k/Ubuntu dual boot) and I have no other, only MacBooks !
BTW - your website rocks - like to try to get those MS fonts set up in Ubuntu - great work!:)

Are you able to get the printer to print from your Mac?  I don't know how to add a network printer on a Mac but I am reasonably sure that it is similar to another OS.

Just use that URL.

Also give your PC a static IP so a router cannot change it, and remember to give it a static IP outside the DHCP.

---

### Post by Chasing_Mosby on 2008-02-13
Ops, it did it again....
 
Upgraded the MacBook to Leopard 10.5  - now printer and Ubuntu box not showing up in network.  Shared folders all turned on in Ubuntu - set up the SMB like before, in fact EVERYTHING set up in Ubuntu like before the upgrade ( when it worked) . So, how does one change Ubuntu to a static IP address . I think this is the issue.

---

