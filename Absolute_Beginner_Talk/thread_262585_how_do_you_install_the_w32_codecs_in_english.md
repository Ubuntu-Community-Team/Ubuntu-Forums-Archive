---
title: "how do you install the w32 codecs in english"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by colin_of_da_loops on 2006-09-21
i dont understand how to do anything code or complicated like that but how do you get the w32 codecs on ubuntu thanks

---

### Post by dmizer on 2006-09-21
> **colin_of_da_loops said:**
> i dont understand how to do anything code or complicated like that but how do you get the w32 codecs on ubuntu thanks

open a terminal.  there are several ways to do this depending on your platform.  if you're using the default gnome, it's under applications > accessories > terminal

copy the following lines one at a time into the terminal and hit enter after every one:
```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
```

now you have w32 codecs.

---

### Post by blx_286 on 2006-09-21
You can also use Automatix to install those codecs, flash, acrobat and a host of other apps.

---

### Post by james_san on 2006-09-21
There is a very good page explaining this and other codecs here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Basically you need to download the file "http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb"
(just paste it into your firefox address bar and it should start downloading. save it to the desktop or something).

Then just double-click on it, and press install. After it is installed you can delete the file.

Almost all other codecs can be installed using "Synaptic Package Manager", which is found in the preferences menu. Just follow the instructions on the aforementioned page for a list of all the good packages to install.

---

