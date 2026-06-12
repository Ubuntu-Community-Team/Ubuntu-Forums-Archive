---
title: "Gimp help not working"
date: 2007-01-11
forum: Art &amp; Design
---

### Post by beanbrain on 2007-01-11
Hello,

I downloaded gimp-help and the related "-en" and "browser" packages using Synaptic but Gimp help still isn't working. Originally I received a message that help files weren't installed, but now I get no response when accessing help (despite restarting The Gimp).

This is on 6.10. Would anyone happen to know how to fix this?

Thanks.

---

### Post by zgornel on 2007-01-12
Go To File/Preferences/Help System and choose at Help Browser, **GIMP Help Browser**. You have to have the gimp-helpbrowser, gimp-help-common and gimp-help-en packages installed.

---

### Post by beanbrain on 2007-02-04
Hello zgornel,

I just followed your instructions to select "GIMP help browser" as the help system, and I'm now able to view GIMP help files.

Thanks!

---

### Post by SherpaDoug on 2007-02-18
> **zgornel said:**
> Go To File/Preferences/Help System and choose at Help Browser, **GIMP Help Browser**. You have to have the gimp-helpbrowser, gimp-help-common and gimp-help-en packages installed.

How do I load the Gimp Help Browser and other packages?  I have the default Dapper Drake installation and Gimp itself seems to run fine, but I get "

The GIMP help files are not installed. Please make sure gimp-help-en is installed, or the appropriate gimp-help package for your language.

Could not open '/usr/share/gimp/2.0/help/en/gimp-help.xml' for reading: No such file or directory

Please check your installation."

if I try to use Help.  Add/Remove applications doesn't seem to offer any assistance.

---

### Post by zgornel on 2007-02-18
> **SherpaDoug said:**
> How do I load the Gimp Help Browser and other packages?  I have the default Dapper Drake installation and Gimp itself seems to run fine, but I get "

The GIMP help files are not installed. Please make sure gimp-help-en is installed, or the appropriate gimp-help package for your language.

Could not open '/usr/share/gimp/2.0/help/en/gimp-help.xml' for reading: No such file or directory

Please check your installation."

if I try to use Help.  Add/Remove applications doesn't seem to offer any assistance.

Search for the package with synaptic. (gimp-helpbrowser, gimp-help-common, gimp-help-en)

---

### Post by smartboyathome on 2007-03-30
I tried this on Dapper Drake, but all I got was:

> 
gimp-helpbrowser:
  Depends: gimp (=2.2.11-1ubuntu3) but 2.2.11-1ubuntu3.1 is to be installed


Is there any way to update this?

---

### Post by courtier on 2007-07-19
When I found Gimp Help not working I...

1) set the Help Browser to be the Gimp Help browser
    File - Preferences - Help System
    Use Drop down box under Help Browser to select Gimp Help Browser

2) System - Administration - Synaptic Package Manager
   Search for gimp-help-common and if not marked present, mark it for loading
   Search for gimp-help-en and if not marked present, mark it for loading
   Search for gimp-helpbrowser and if not marked present, mark it for loading
   Apply the packages to ubuntu

This worked for me, a very newbie with a freshly mounted ubuntu workstation.

Thank you everybody.

---

### Post by Exom on 2008-02-01
> **courtier said:**
> When I found Gimp Help not working I...

1) set the Help Browser to be the Gimp Help browser
    File - Preferences - Help System
    Use Drop down box under Help Browser to select Gimp Help Browser

2) System - Administration - Synaptic Package Manager
   Search for gimp-help-common and if not marked present, mark it for loading
   Search for gimp-help-en and if not marked present, mark it for loading
   Search for gimp-helpbrowser and if not marked present, mark it for loading
   Apply the packages to ubuntu

This worked for me, a very newbie with a freshly mounted ubuntu workstation.

Thank you everybody.

Thanks

---

### Post by Ron O on 2010-08-14
Here it is, August 2010 and I had the same problem with gimp help files in Ubuntu Lucid, and these posts fixed me right up.

---

