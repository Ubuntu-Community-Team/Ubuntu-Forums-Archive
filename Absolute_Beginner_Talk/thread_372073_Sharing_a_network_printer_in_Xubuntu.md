---
title: "Sharing a network printer in Xubuntu"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by majkball on 2007-02-27
I am trying to share my HP Laserjet 5P printer connected to my Xubuntu machine through the network, so that I can print from my Windows XP laptop. 

Just before I installed Xubuntu 6.10 I had Ubuntu 6.10 installed and actually managed to get the printer sharing to work, but I needed to change to Xubuntu because my machine was too slow, and now I can't get it to work anymore. :(

My laptop has ip (192.168.0.10) and at the "add printer wizard" I specified the url for the printer to ([http://192.168.0.20:631/printers/HP-Laserjet-5P](http://192.168.0.20:631/printers/HP-Laserjet-5P)) were 192.168.0.20 is the ip to my Xubuntu machine. When I specify this url I just get a fault message telling me that windows cannot connect to the printer, operation could not be completed. And yes I have tried to ping my machines and it seems to work that way... so probably there is some setting needed to be made.

My Xubuntu 6.10 is a fresh install and I have updated to the latest through the update-manager. I haven't installed samba or anything like that.

Here is a copy and paste from my "cupsd.conf":

```
# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Allow remote access
Listen 192.168.0.*:631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow From 192.168.0.10
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
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
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

---

### Post by crispy_420 on 2007-02-27
You will need to install samba to allow windows to see your printer, I think.

Start there and enable sharing in that config file for the printer.

---

### Post by majkball on 2007-02-28
I tried to install Gsambad... 

When I try to run Gsambad from the menu I get error that I need to be root to run it.
So when I run it from a terminal window with command

```
gksudo gsambad
```
I get:
```
** (gsambad:4825): WARNING **: Couldn't find pixmap file: gsambad.png

(gsambad:4825): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```
And a lot of other fault messages, anyway nothing seems to work when I change some settings. Am I using the wrong samba or where am I doing wrong?

Well I googled a bit on CUPS and found out there are some error_logs aswell... well this is an interesting part from my error_log:
```
E [28/Feb/2007:22:03:06 +0100] Hostname lookup for "192.168.0.*" failed!
E [28/Feb/2007:22:03:06 +0100] Bad Listen address 192.168.0.*:631 at line 5.
I [28/Feb/2007:22:03:06 +0100] Listening to /var/run/cups/cups.sock (Domain)
I [28/Feb/2007:22:03:06 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
E [28/Feb/2007:22:03:06 +0100] Creating missing directory "/var/run/cups/certs"
W [28/Feb/2007:22:03:06 +0100] Repairing ownership of "/var/run/cups/certs"
W [28/Feb/2007:22:03:06 +0100] Repairing access permissions of "/var/run/cups/certs"
```

Seems to me CUPS have problems with the 192.168.0.*:631  Have I done any typo?

Finally... I have seen other screendumps where people are able to configure CUPS through a webbrowser window. By typing in the webadress "http://localhost:631/admin" or similair... this doesnt work for me. Why?

Thank you for any answer or thoughts... I got it working on Ubuntu but this Xubuntu seems to only offer me problems!!

---

### Post by lukemack on 2007-03-28
I'm having the same problem on Ubuntu Server 6.10. Did you get this working?

---

### Post by dstew on 2007-03-28
Is the printer truly a network printer, or is it plugged into the computer as a local printer that you want to share? If it is the latter, I think you need to use samba to share the printer.

EDIT: I had to also install some CUPS software to share a printer, if I remember correctly. My [http://localhost:631](http://localhost:631) works fine, I get the CUPS administration web screen.

---

### Post by lukemack on 2007-03-28
sorry - i meant the gsambad error!

---

### Post by compmodder26 on 2007-03-28
Have you opened port 631 in your firewall?  Without doing that, you won't be able to connect.  With XP, you shouldn't need SAMBA.  It should support ipp.

---

