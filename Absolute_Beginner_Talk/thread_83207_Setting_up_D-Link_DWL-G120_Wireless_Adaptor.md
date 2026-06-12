---
title: "Setting up D-Link DWL-G120 Wireless Adaptor"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by LDearden on 2005-10-28
Im new to Linux, from what ive seen so far it looks great! Im running Ubuntu Linux v5.04 on an IBM ThinkPad 600e. In order to get this laptop onto the internet I need to attatch a D-Link DWL-G120 USB wireless adaptor, now D-Link don't distribute linux drivers for this model, however they provide links to pages with un-official drivers, I have the file dldrinstall.run which I believe is the correct file, but as I am a complete novice to linux I have no idea how to go about installing the drivers, could someone run me through a detailed installation process? This would be much appreciated.

Thanks,
LDearden

---

### Post by kane77 on 2005-10-28
Well it depends on what form are the drivers distributed... it can be:
1. source
2. debian package
You can distignuish by the extension of file (source has commonly .tar.gz ext, and debian has .deb)

The debian installation is easier you just type in terminal "sudo dpkg -i name of package.deb". (wite it without "") it should install it automaticaly...

The installation from source require some pacckages installed... so again 
1. terminal "sudo apt-get install build-essential" it should make you able to install from source... 
2. Now there are several methods: a) 1, "sudo apt-get alien"
                                                   2, in directory where the .tar.gz file is located "sudo alien -d filename.tar.gz" - it will create deb package of it...
                                               b) again in terminal in the directory where your file is present write "./configure" next "make" then "make install"
                                               C) use terminal "sudo apt-get install checkinstall", and use b) but in last step replace "make install" with "sudo checkinstall"

Let me know if this was helpful....

---

