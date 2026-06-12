---
title: "copying applications into another ubuntu installation"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by shishirmk on 2007-09-06
i wanted to know how to transfer applications i have downloaded and installed in my ubuntu installation to another(my frns comp's installtion)i mean i have to copy wht files and paste them  where.??:confused:

---

### Post by meborc on 2007-09-06
(i'm guessing the other computer doesn't have a internet connection for some reason, otherwise just install the program via apt)

the best way is to download the program .deb file to your computer, then transfer it (cd, floppy, usb) to the other computer

then just "sudo dpkg -i package.deb" as usual

i'm not sure if just copying program related files form your comp to his is a good idea :) you can look what files are installed by the program with synaptic, or with "whereis package" command

---

### Post by Voland on 2007-09-06
Try APTonCD. This is program for CD-repository creation. You can simply add your CD-repo via "Software sources" menu item and install software without risk of broken dependencies.

---

### Post by shishirmk on 2007-09-06
mebroc where to download the .deb files from i think they will be our system also somewhere in file system please give proper info urgent

---

### Post by Voland on 2007-09-08
Applications downloaded and installed via apt-get are in /var/cache/apt/packages/

---

