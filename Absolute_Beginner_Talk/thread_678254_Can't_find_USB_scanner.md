---
title: "Can't find USB scanner"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Over the hill on 2008-01-25
Hello All,

I am new to Ubuntu and recently installed 7.10. I've managed to stagger my way through most things but I cannot install my Mustek 1248 UB scanner. When I launch xSANE  Image scanner,I get an error message  that says "Failed to open device gt68xx:libusb:001:002.
I have installed a number of extras such as :- Libsane, Libsane-extras, Sane utils, Xsane common etc. but to no avail. Any help would be appreciated.

---

### Post by linuxwizard on 2008-01-25
Read over this, may have to change configuration file.

[http://www.sane-project.org/man/sane-gt68xx.5.html](http://www.sane-project.org/man/sane-gt68xx.5.html)

---

### Post by Over the hill on 2008-01-26
Thank you for your reply. I have downloaded the firmware file (SBSfw.usb). The instructions on the website are to install it to either :-
/usr/local/share/sane/gt68xx
or
/usr/share/sane/gt68xx  (If I use a sane package that came with the distribution)

As far as the first address goes, there is no sane directory in /usr/local/
I can access the second address but when I try to install the file I get the following error message,

 "Error while copying to '/usr/share/sane/gt68xx/' You do not have permission to write to the folder"

I'd be grateful for any suggestions.

---

