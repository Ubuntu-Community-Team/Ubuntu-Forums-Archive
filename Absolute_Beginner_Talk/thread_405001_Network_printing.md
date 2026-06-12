---
title: "Network printing"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by koenie53 on 2007-04-09
I screwed up my /etc/cups/cupsd.conf file while trying to install a network printer. Can someone send me a copy I can paste in here. If I go to System=> Administration=> Printing.....the screen does not pop up so that I can not set up the printer.
I got a HP Deskjet 1220C connected to my Ubuntu box and my wife got XP on her pc but we want to use both this printer. I got ADSL rooter with ethernet connections to both PC's......will this do as a network between the 2 PC's as well???
Followed all the instruction on the Documentation and Community section but no luck
Can someone please help???  anyone also experienced automatix2 update problems???

---

### Post by freebeer on 2007-04-09
Here's mine.  I hope it helps.



```
#
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
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
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

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#

```

---

### Post by koenie53 on 2007-04-09
Sytem => Administration=> Printing 
Does not work yet and dissapears quickly before I can even setup a new printer. What have I done wrong??? I am totally screwed

---

### Post by 11hjpphty76lkjj on 2007-04-09
What happens if you go to:

```
http://localhost:631
```

and what happens if you run

```
sudo /etc/init.d/cupsys restart
```

A

---

### Post by koenie53 on 2007-04-12
[http://localhost:631](http://localhost:631). Error cant find it

sudo /etc/init.d/cupsys restart I get:
* Restarting Common Unix Printing System: cupsd                         [ ok ]

---

### Post by 11hjpphty76lkjj on 2007-04-12
If you restart cupsys and still can't get to localhost:631 this would seem to indicate a problem with cups.  You may need to post as a cups question/problem, or ask in the cups forums.  Sorry I couldn't help more!

A

---

