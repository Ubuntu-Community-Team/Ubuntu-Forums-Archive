---
title: "printing from xp problems"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by dfor50 on 2006-07-17
Hello,

This is a long post sorry, but it might help.

I have been at this for days now and is really the only thing switching over to ubuntu totally on my main computer. Before I can do that my other family members need to be able to print from their computers to the one hooked up to the ubuntu machine. The printer is a canon piuxma ip3000 but there is no linux driver so I am using a BJC7000 driver which works OK. 

I can see the printer from the xp machine and when I go to use it XP says the driver is incorrect and do I want to download the proper driver. I select the BJC7000 driver and installation goes ahead, The test page is a failure with "test page failed to print". Here is my smb.conf file

# Sample configuration file for the Samba suite for Debian 
# GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]
log file = /var/log/samba/log.%m
printer = BJC-7000
guest account = nobody
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
socket options = TCP_NODELAY
obey pam restrictions = yes
map to guest = Bad User
interfaces = 10.0.0.0/24
encrypt passwords = true
passwd program = /usr/bin/passwd %u
dns proxy = no
netbios name = ubuntu
server string = %h server (Samba, Ubuntu)
invalid users = root
workgroup = winners
comment = Impressora
security = share
syslog = 0
panic action = /usr/share/samba/panic-action %d
max log size = 1000
wins support = no

[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
public = yes
guest ok = yes
writable =yes
create mode = 0700
printing = cups
printcap name = cups
use client driver = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /tmp
browseable = yes
read only = yes
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
; write list = root, @ntadmin

[sparker]
path = /home/sparker
available = yes
browseable = yes
public = yes
writable = yes
users = sparker, daisydog, steve


and here is my cupsd.conf

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
User cupsys
SystemGroup lpadmin
RunAsUser yes
Port 631

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631

Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
Browsing On
#BrowseOrder allow,deny
BrowseAllow @LOCAL
#BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...

<Location />
  Order Deny,allow
Allow from @LOCAL
Allow from 127.0.0.1

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


I hope someone can come up with a simple solution or steer me in the right direction.

Thanks

---

