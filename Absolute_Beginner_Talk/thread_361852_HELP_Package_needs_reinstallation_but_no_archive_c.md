---
title: "HELP Package needs reinstallation but no archive can be found for it!!!"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by wantime on 2007-02-14
Hi,

I get this message:

 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc440cncupswrapper needs to be reinstalled, but I can't find an archive for it.

from an apt-get install ...

I can't use synaptic either at the moment.  Does someone know where I can look to find the offending package information??  The package is mfc440cncupswrapper for a printer.

Thanks

---

### Post by chuckyp on 2007-02-15
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by sardion on 2007-02-15
I suspect you want ot look here:

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de)

But I think maybe you should do:

sudo apt-get remove mfcwhateveritis

first and then

sudo apt-get -f

to make sure your system is ok.

---

### Post by wantime on 2007-02-15
Thanks Sardion,

I couldn't uninstall the driver and it was jamming Synaptic, in the end I recursively removed the directory in /usr/local/Brother to get Synaptic back again.

After that I removed all the MFC440CN* entries in /var/lib/dpkg/info

Then I could reinstall the drivers (FIRST lpr and THEN the cups)  this got me back to square one and a working printer on USB.

I still can't network the printer though.  I plug it into the router and it receives an IP address, I go to /localhost:631 and try to add the printer (it sees MFC440CN) but it doesn't ever find it on the network. Hmmm.  My cups.conf file is:

```
wantime:~$ cat /etc/cups/cupsd.conf
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
```


Got any ideas on that one?? I'm trying to be careful not to have it completely wig out on me again.

Thanks

---

