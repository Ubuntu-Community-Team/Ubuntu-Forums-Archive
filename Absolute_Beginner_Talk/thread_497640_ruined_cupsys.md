---
title: "ruined cupsys"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by jshalvi on 2007-07-10
I tried setting up network printing, and corrupted my cupsd.conf in the process.  And of course I didn't back it up.

I tried reinstalling the package through add/remove, synaptic, and apt-get, but all failed.  It seems the actual reinstallation doesn't happen, as cupsd.conf is the same corrupted file, and cupsd fails when starting.

Any suggestions on how to completely reinstall a package?

---

### Post by Cypher on 2007-07-10
From the terminal
```

sudo apt-get remove cupsys
sudo dpkg --purge cupsys

```
This will un-install and remove all configuration files. You can now re-install it through Synaptic or APT-GET and have the default files back..

---

### Post by Seisen on 2007-07-10
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
**Listen localhost:631**
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

#
# Printcap: the name of the printcap file.  Default is /etc/printcap.
# Leave blank to disable printcap file generation.
#

Printcap /var/run/cups/printcap

#
# PrintcapFormat: the format of the printcap file, currently either
# BSD or Solaris.  The default is "BSD".
#

#PrintcapFormat BSD
#PrintcapFormat Solaris

#
# PrintcapGUI: the name of the GUI options panel program to associate
# with print queues under IRIX.  The default is "/usr/bin/glpoptions"
# from ESP Print Pro.
#
# This option is only used under IRIX; the options panel program
# must accept the "-d printer" and "-o options" options and write
# the selected printer options back to stdout on completion.
#

#PrintcapGUI /usr/bin/glpoptions
```

Here is mine the only thing i changed in it was what I put in bold.

---

### Post by jshalvi on 2007-07-10
great, thanks!

---

