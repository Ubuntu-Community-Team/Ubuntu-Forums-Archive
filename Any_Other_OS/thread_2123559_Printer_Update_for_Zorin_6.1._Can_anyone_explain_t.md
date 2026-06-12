---
title: "Printer Update for Zorin 6.1. Can anyone explain to me how to do this"
date: 2013-03-08
forum: Any Other OS
---

### Post by gregoryshock on 2013-03-08
There is still several reasons as to why I still hange onto windows.   But there are not very many reasons.  I need help trying to eliminate  one of them.  I have a HP Photosmart Premium 309a Printer.  This printer  is designed to print on both sides of a page.  But through Linux it  can't.  At least without an update to my Zorin-os-6.1-core-64.  It is  based on the Ubuntu.  I have narrowed my search down to this.  It looks  like I will need to perform the install through the terminal.  Can  anyone explain to me how this works?   [http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c309a_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c309a_series.html)

---

### Post by Cheesemill on 2013-03-08
Have you tried following the instructions on the site?

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by gregoryshock on 2013-03-23
Thank you for the Manual.  I tried it.  It sorta worked.  Since then I decided to reinstall Linux and start all over.  This time I started with what that Manual says and I got this message.

  	 	 	 	   g@g-DG965OT:~/Desktop$ sh hplip-3.13.3.run 
 Creating directory hplip-3.13.3 
 Verifying archive integrity... All good. 
 Uncompressing HPLIP 3.13.3 Self Extracting Archive.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................. 
  
 HP Linux Imaging and Printing System (ver. 3.13.3) 
 HPLIP Installer ver. 5.1 
  
 Copyright (c) 2001-13 Hewlett-Packard Development Company, LP 
 This software comes with ABSOLUTELY NO WARRANTY. 
 This is free software, and you are welcome to distribute it 
 under certain conditions. See COPYING file for more details. 
  
 Installer log saved in: hplip-install_Sat-23-Mar-2013_14:39:14.log 
  
 warning: zorin distro is not found in AUTH_TYPES 
 \ 
 note: Defaults for each question are maked with a '*'. Press <enter> to accept the default. 
 error: Auto installation is not supported for 'unknown' distro so all dependencies may not be installed.  
 Please install manually as mentioned in 'http://hplipopensource.com/hplip-web/install/manual/index.html' web-site 
  
 Press 'y' to continue auto installation. Press 'n' to quit auto instalation(y=yes, n=no*):

---

### Post by gregoryshock on 2013-03-23
Next:  I tried going to [http://hplipopensource.com/hplip-web/install/manual/index.html](http://hplipopensource.com/hplip-web/install/manual/index.html)  I looks confusing to me but here is what I tried.  It appears to have failed.

* My System is Ubuntu 12.04 so I tried the line that said it was for "Ubuntu 10.04 (Lucid) and above"

Press 'y' to continue auto installation. Press 'n' to quit auto instalation(y=yes, n=no*): n
Installation exit
g@g-DG965OT:~/Desktop$ sudo apt-get install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-1.0-0-dev wget python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsan
[sudo] password for g: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xsan
g@g-DG965OT:~/Desktop$ tar xvfz hplip-3.13.3.tar.gz
tar (child): hplip-3.13.3.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
g@g-DG965OT:~/Desktop$ 

**I'm not sure what to do now?**

---

### Post by Sef on 2013-03-23
Moved to other OS forum.

The problem is '[COLOR=#000000]Unable to locate package xsan'. Have you asked in the zorin forums for help with this issue?  HP does not say that it supports zorin.[/COLOR]

---

