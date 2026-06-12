---
title: "Scanner Issue"
date: 2007-06-24
forum: Arkansas Team - US
---

### Post by lchowell on 2007-06-24
I bought a new all in one printer from Canon. It is a PIXMA MP180. I'm able to get everything to work on it except the scanner. The xSane says that it does not recognize the scanner. How can I get the scanner working on Ubuntu 7.04. Thanks for any help.


Lance

---

### Post by Tommy on 2007-06-25
> **lchowell said:**
> I bought a new all in one printer from Canon. It is a PIXMA MP180. I'm able to get everything to work on it except the scanner. The xSane says that it does not recognize the scanner. How can I get the scanner working on Ubuntu 7.04.

I just looked your scanner up on the SANE database [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html) and it's listed as "untested." The online man page [http://manual.cream.org/index.cgi/sane-pixma.5](http://manual.cream.org/index.cgi/sane-pixma.5) says:

> 
 The following models are not well tested and/or the scanner sometimes hangs and must be switched off and on.  ... PIXMA MP180, ...I see with a Google search that someone is actively developing a PIXMA driver [http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/) so you might make contact with that person (probably by finding out which SANE email list or forum they monitor) and learn what you can do to help test your model.

Unfortunately, Canon is a manufacturer that continually refuses to provide open source support for their products by not releasing the necessary technical information. The support for Canon products in linux comes about due to lots of tough investigation by individuals with no assistance from the manufacturer. It seems like Canon would want to encourage people to use their products on linux! You might try sending a message directly to Canon in the hopes that they will eventually hear the message.

The best way to be sure a scanner or multifunction device will work without trouble in linux is to check the SANE and CUPS documentation. ALTERNATIVELY, you may find a non-free driver such as TurboPrint for printing or VueScan for scanning. The downside to using these is your license payment to the publisher does nothing to improve the built-in support for the devices in linux. 

If you make progress in getting yours to work, be sure to get the SANE information updated so others can benefit!

Good luck!

---

