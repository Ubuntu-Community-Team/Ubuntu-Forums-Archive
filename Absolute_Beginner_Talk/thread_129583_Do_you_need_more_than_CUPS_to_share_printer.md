---
title: "Do you need more than CUPS to share printer?"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-14
Can I share a printer through the CUPS administration web interface at [http://server:631?](http://server:631?) Or must I install SAMBA to share any printer?

Thanks !

---

### Post by AndyCooll on 2006-02-14
I'm at work right now so I apologise that I can't give you exact details. Theoretically you can share a printer with just CUPS. And you certainly shouldn't need to install Samba if your just sharing your printer with other Linux pc's. 

IIRC you may well need to modify the CUPs config file and change one of its settings so that it broadcasts on the network (i.e. making it browseable) for others to share it.

---

### Post by skirkpatrick on 2006-02-14
You can't install a printer through CUPS admin interface unless you change RunAsUser to No in /etc/cups/cupsd.conf.  However, when you add/change a printer through System->Administration->Printing, it changes it in CUPS.

You don't need to install Samba so share the printer.  I share my printer through both CUPS and Samba because the Win98 machines in my house get a faster response through the Samba share while the WinXP machines get a faster response through CUPS.  To have your Windows machines access the printer through CUPS, they should install the printer as an Internet printer using "http://machine_name:631/printers/printer_name" as the URL, with the appropriate machine_name and printer_name.

You'll also need to change the section called "Network Options" to look like the one below then restart CUPS:
> 
########
######## Network Options
########

#
# Ports/addresses that we listen to.  The default port 631 is reserved
# for the Internet Printing Protocol (IPP) and is what we use here.
#
# You can have multiple Port/Listen lines to listen to more than one
# port or address, or to restrict access:
#
#    Port 80
#    Port 631
#    Listen hostname
#    Listen hostname:80
#    Listen hostname:631
#    Listen 1.2.3.4
#    Listen 1.2.3.4:631
# 
# NOTE: Unfortunately, most web browsers don't support TLS or HTTP Upgrades
# for encryption.  If you want to support web-based encryption you'll
# probably need to listen on port 443 (the "https" port...)
#
# NOTE 2: In order for the command-line and web interfaces to work, you
# must have at least one Port or Listen line that allows access from the
# local loopback address (localhost).
#

#Port 80
#Port 443
Port 631
#
#Listen 127.0.0.1:631


---

