---
title: "Truecrypt W/ USB Thumbdrive. Please Help."
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by junglist313 on 2007-12-28
Ok got a new Thumb Drive for X-mas (disk go Edge 8GB) the first time it plugged it in it opened to file browsers one named "disc" the other "Secure Guard" I noticed that the drive came with some windows encryption software pre-installed. I deleted those files and then ran gparted to check the setup of the drive. The drive was split into 2 partitions, /dev/sdc/  and   /dev/sdd/ repectivley. After a little tinkering in gparted I managed to adjust one of the partitions to be 7.68GB (thats as big as it would go) and shrink the other to the remainder to an unremebered amount (still didn't add up to 8 though). I attempted to create a Truecrypt container on the drive through the command line but only succeded in creating something called dev/mapper/truecrypt0. I am still a little confused when it comes to devices and mounting. 
Can someone help me create a truecrypt container on this drive? Or better yet how to encrypt the entire drive/partition?  Also the size of dev/mapper/truecrypt0 was 2GB (the size i specified) but since it's not "in" the usb drive does that mean it's eating HD space? Also now for some reason the dev/mapper/truecrypt no longer shows up when I scan devices with gparted. Also the drive is no longer recognized as soon as I plug it in. I am very confused. I have the 7.68GB partition on dev/sdc formated as fat32. 

Thank you in advance for your help, and sorry for rambling.

---

### Post by junglist313 on 2008-02-28
Yeah, still have not figured this out. Any help? Hello?  :k

---

