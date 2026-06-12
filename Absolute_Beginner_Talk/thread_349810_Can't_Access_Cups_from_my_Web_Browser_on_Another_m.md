---
title: "Can't Access Cups from my Web Browser on Another machine."
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by peejaygee on 2007-01-30
Dear All, 

Can anybodyhave look at this config, and tell me what is going wrong, I followed the tutorial about [http://www.howtoforge.org/samba_setup_ubuntu_5.10](http://www.howtoforge.org/samba_setup_ubuntu_5.10) and changed relevant parts.

I got to [http://www.howtoforge.org/samba_setup_ubuntu_5.10_p5](http://www.howtoforge.org/samba_setup_ubuntu_5.10_p5) installing CUPS (now admitadly I don't have a printer connected yet, as I'm setting up the machine first, but putting it place, additional hardware etc)

It says about adding bits to Network Options and Security Options, but I couldn't find that within the cupsd.conf.

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
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 192.168.1.4:631

# Show shared printers on the local network.
Browsing On
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
  Allow 192.168.1.4:631
</Location>

# Restrict access to the admin pages...
<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks. You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass Group
AuthGroupName shadow

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.4

#Encryption Required
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
```

I've done the adduser cupsys shadow, and restarted, but when I checked to see if the machine was listening on 631 (netstat -l) and it isn't.

---

