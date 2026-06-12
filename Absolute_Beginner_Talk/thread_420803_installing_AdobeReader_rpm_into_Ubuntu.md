---
title: "installing AdobeReader rpm into Ubuntu"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by gzone on 2007-04-23
I am running Ubuntu 6.10 and wanted to install AdobeReader...I downloaded the rpm version and tryed to install it. As I'm new to this I need all the help I can get.

---

### Post by LaurelLynn on 2007-04-23
Dear gzone,

You can get Acrobat from a debian repository (I did), it will be easier and more compatible then an rpm file.   These instructions are copied from another thread:

I'm happy to announce that I've got acrobat reader 7 working as well . I think the easiest way to do this is to add the following lines to the /etc/apt/sources.list file:


# Acrobat Reader
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main


Then simply update the package list and install the acroread package:


sudo apt-get update
sudo apt-get install acroread

---

### Post by gzone on 2007-04-24
Thank you LaurelLynn, I'll give it a try...will keep you all posted.

---

### Post by gzone on 2007-04-24
The link gave me a error 550 can't change directory or no such directory...thank you for your effort.

---

### Post by kittyhawk63 on 2007-04-24
> **gzone said:**
> The link gave me a error 550 can't change directory or no such directory...thank you for your effort.

I got the same error gzone. It appears to be the marillat.
kh

---

### Post by gzone on 2007-04-24
Thank you KittyHawk63....I'll keep waiting and searching. Do you think version 7 will be better?

---

### Post by LaurelLynn on 2007-04-24
You might also try using the Firefox pluggin of version 7.  The following link has instructions wil screenshots of the whole process:

[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox.html)

I´ll keep my eye out for a working repository with  the standalone version, so check back latter.

---

### Post by kittyhawk63 on 2007-04-24
gzone,
I sent you a private message to help you install AdobeReader.
kh

---

### Post by AlexenderReez on 2007-04-24
you can get that from medibuntu.com  too...    :KS

---

### Post by girlfreddy on 2007-04-25
I tried this method to get Acroread but this is what comes up.

$ sudo apt-get install acroread mozilla-acroread acroread-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acroread is already the newest version.
Package mozilla-acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-acroread has no installation candidate

Does anyone know where to get this?

---

### Post by kittyhawk63 on 2007-04-25
> **girlfreddy said:**
> I tried this method to get Acroread but this is what comes up.

$ sudo apt-get install acroread mozilla-acroread acroread-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acroread is already the newest version.
Package mozilla-acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-acroread has no installation candidate
Does anyone know where to get this?

You can get **Acrobat Reader** through the use of **Automatix**.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

After you install **Automatix**, you can start it under **Applications->system Tools**. Agree to the pop up and then it will install the latest releases. You will find Acrobat Reader under **Office**.
Hope this helps.
kh

---

### Post by gzone on 2007-04-28
Hi everyone
Hope your weekend is going well. Anyway sorry for taking so long to update you all on the progress of installing AdobeReader.

I recieved information on a package installer called "Aotomatrix". This past Thursday I installed (a clean install) Ubuntu 7.04 the installation went well and I happy to report that the features that are important to me runs as well if not better then on version 6.XX.

I downloaded "Aotomatrix" and intalled it to the system...life is sweet. Coming from Windblows is not a good thing, all that system does is teach one to accept or to settle for less then the best possible from ones investment in technology.

One of the features of linux that I look forward to is getting in to the "guts" of both hardware and software...in a nut shell taking back control.

Thank you all for all you helpful suggestion it is heart warming.

---

