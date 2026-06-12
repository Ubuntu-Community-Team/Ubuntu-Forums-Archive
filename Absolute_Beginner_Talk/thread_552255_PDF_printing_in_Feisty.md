---
title: "PDF printing in Feisty"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2007-09-16
Hi Ubuntu-ers:

There is a "HowTo" on how to print to pdf files at [URL="http://ubuntuforums.org/showthread.php?t=188860"] . It is nice, but it was posted in 2005. I've wondered whether my inability to make that HOWTO work is because Ubuntu has changed since then.

I've scoured the forum for help on solving my inability to print to PDFs... I cannot find anything that works for me.

Is there an updated HOWTO, or does anyone know how to set up printing to PDFs correctly with an up-to-date version of Feisty?

Thanks!
Phil Smith
Duluth, GA

---

### Post by southernman on 2007-09-16
What sort of document are you trying to print?

---

### Post by kevstar31 on 2007-09-16
[Try this guide.]("https://help.ubuntu.com/community/PDFPrinting")

---

### Post by Old Jimma on 2007-09-16
Hi Kevstar31:

Thanks for your reply. I looked at the documentation, and followed it exactly. When I follow the instruction to right click on the newly created print, then select properties, and then press on "print a test page", it prints a test page perfectly and winds up in my PDF folder.


However, if I am in Firefox, and want to print a pdf of the current web page, when I go to file > print and then check "print as file", I don't see any options other than to print a post-script file. In fact when I print a file from Firefox this way, when I right click on the file, and look at the file's properties, it is shown to be a postscript file.

How to I print a pdf from Firefox?

Thanks!
Phil Smith 
Duluth, GA

---

### Post by kevstar31 on 2007-09-16
To Firefox it appears to be a regular printer so you need to change it to print to the pdf printer and not check print to file.

---

### Post by rbprogrammer on 2007-09-17
> **kevstar31 said:**
> [Try this guide.]("https://help.ubuntu.com/community/PDFPrinting")
i am having trouble printing to a pdf too, i have went through this very easy step-by-step, but for some reason it does not make any .pdf file in my home directory.

i have tried other methods, but nothing seems to be up to date with feisty.  for example, a few places tell me to change a line in my /etc/cups/cupsd.conf that begins with "RunAsUser", but there is no such line in my config file.

here is my cupsd.conf file if it helps with my problem:
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

---

### Post by Old Jimma on 2007-09-18
Kevistar:

There is no option to choose a pdf printer from file > print in Firefox, even after "installing" the pdf printer.

Phil

---

### Post by qpieus on 2007-09-18
How 'bout this thread? I didn't compare it to the thread you linked, so maybe it's the same method. Worth a look though as several people have added that it works for fiesty.

[http://ubuntuforums.org/showthread.php?t=283198](http://ubuntuforums.org/showthread.php?t=283198)

Here's another one for kubuntu:

[http://ubuntuforums.org/showthread.php?t=279647](http://ubuntuforums.org/showthread.php?t=279647)

I use kubuntu as well and I remember that the guide you linked to didn't work for me either. I somehow fixed the problem and can now print to pdf from firefox, but unfortunately that was quite a while ago and I cannot remember how I did it. If I remember I'll post again.

---

### Post by Old Jimma on 2007-09-25
Hi Qpius:

Thanks for that post. I have seen it many times and tried it many times. It still does not work.

Best regards,
Phil Smith

---

