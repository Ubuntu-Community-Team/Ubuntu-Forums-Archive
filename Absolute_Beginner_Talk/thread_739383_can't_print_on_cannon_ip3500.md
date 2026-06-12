---
title: "can't print on cannon ip3500"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-03-29
I am having trouble getting my printer to work correctly, i have a cannon ip3500.

on system -> administration ->  printing 

I clicked add a printer, and a list of printers was displayed, however under cannon, the model ip3500 was not listed, i chose the closest one ip3100, and it asked me to install a driver, i looked all over the cd that came with the printer and no PPD files were present.

I looked on cannon's page here
[http://software.canon-europe.com/software/0028475.asp](http://software.canon-europe.com/software/0028475.asp)
However inside these don't seem to be an y PPD files unless i am mistaken. I have installed most of the packages from those files that i could, however it didn't make a difference.

---

### Post by cmnorton on 2008-03-29
Have you tried printing to it using generic drivers? Try it as a plain text printer or a generic post script.

As to Cannon's web site, focus on looking for Linux drivers as opposed to PPDs. Cannon is a well-known name; unless this printer just came out, there is a probably a driver for it. If not, you should be able to use an older, compatible model driver.

As an aside, Ubuntu's print config is good, but I tend to like to use the CUPS web interface localhost:631. Just make sure you are in the lpadmin group. It's personal preference, but I find the interface a bit cleaner. For other distros we use -- especially Red Hat -- the CUPS web interface is mandatory.

---

### Post by Daveth on 2008-03-29
probably worth poking about in here...

[http://www.linuxprinting.org/printer_list.cgi?make=Canon](http://www.linuxprinting.org/printer_list.cgi?make=Canon)

---

