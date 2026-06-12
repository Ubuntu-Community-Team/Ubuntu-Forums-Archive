---
title: "help with sharing printer using CUPS"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by bigmista on 2006-12-18
HELP!!

I've tried and tried but I can't get my laptops to recognize a printer connected to the Ubuntu desktop. Here are the Details:

Printer: HP Officejet 5610xi with USB connection
Desktop: Ubuntu 6.10 wired to D-Link wireless router
Laptop1: Hp running windows XP media center connected wirelessly to D-Link Router
Laptop2: Hp running windows XP connected wirelessly to D-Link Router

All computers are in the MSHOME workgroup. All computers can ping each other. When I tried to telnet to 192.168.0.105 631(the desktop) I got a message that said "Could not open connection to the host on port 631: Connection Failed"

Here is what is in my cupsd.conf file:

[FONT="Courier New"][COLOR="Blue"]#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen *:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#
Allow From 192.168.0.*[/COLOR][/FONT]

I've scoured the forums looking for more answers but I can't find any. Please Help!

---

### Post by dbbolton on 2006-12-18
samba ?

---

### Post by bigmista on 2006-12-18
What can I tell you about Samba? I'll post any files I need to.

---

### Post by bigmista on 2006-12-18
bump

---

### Post by Rumor on 2006-12-18
I have a similar set up and home except that my laptops are desktops runing Windows XP. I have my HP Deskjet printer connected to my ubuntu computer and shared so that the XP boxes can print to it. I hope what I did works for you as well.

I have edited my /etc/cups/cupsd.conf file to include
```
    Port 631
    Include cupsd-browsing.conf
    BrowseAddress @LOCAL
    BrowseAddress 192.168.1.*
     
    <Location />
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 192.168.1.*
    </Location>
    
    <Location /jobs>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 192.168.1.*
    </Location>
    
    <Location /printers>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 192.168.1.*
    </Location>
    
    <Location /admin>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 192.168.1.*
    </Location>

```
 and my /etc/cups/cups.d/ports.conf file
```
Listen localhost:631
Listen /var/run/cups/cups.sock
```

Then restart cups and you should be able to print from your laptops by adding a printer where you specify the printer address [http://192.x.x.x:631/printers/name_of_printer](http://192.x.x.x:631/printers/name_of_printer) specifying your network addressing and printer name.

I hope this helps.

---

### Post by gigaferz on 2006-12-22
Hey bigmista !

Did it work??

---

### Post by BackInTimeMan on 2006-12-23
> **bigmista said:**
> bump

If you haven't got it sorted yet, you might want to listen to this podcast:

Episode 29 - Printer Networking

[http://www.linuxreality.com/page/3/](http://www.linuxreality.com/page/3/)

Heck, listen to them all, they're really good.

---

### Post by gcblig on 2007-01-13
This worked for me - many thanks

---

