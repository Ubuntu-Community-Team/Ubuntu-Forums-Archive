---
title: "cups error print share"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-12-20
I thought I was close to print sharing with a windows machine via samba server. Followed this guide to get the windows machine set up to allow me to share: [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

However, I also seem to have messed up cups.conf. Previously when I ran the Printer Configuration GUI I was seeing the shared printer, but now I am not, and I get the message shown in the screenshot below. Any help would be greatly appreciated.

---

### Post by spiderbatdad on 2007-12-20
```
#
# "$Id: cupsd.conf.in 6720 2007-07-25 00:40:03Z mike $"
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
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing on
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress all

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow all
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow all
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow all
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
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
# End of "$Id: cupsd.conf.in 6720 2007-07-25 00:40:03Z mike $".
#
```

---

### Post by spiderbatdad on 2007-12-20
bump

---

### Post by spiderbatdad on 2007-12-20
one problem might be the cupsd.conf lines: 
Listen localhost:631
Listen /var/run/cups/cups.sock

I'm getting an error msg in the samba log that says no such file or directory exists. Can I just create it? Or does it need to have something in it?
Tried creating, but didnt solve problem. Always same error: httpConnectionEncryptFailed from cups server dialogue

---

### Post by spiderbatdad on 2007-12-20
bump

---

