---
title: "ndiswrapper"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Radovitch on 2007-02-26
Can anyone tell me if:

ndiswrapper-utils
ndiswrapper-common
ndiswrapper-utils-1.8

are in fact three separate packages, all of which have to be downloaded and installed before installing the wireless driver? The reason I ask is because the only one of the three on my Dapper Drake CD is the utils-1.8 and it refuses to recognise the Speedtouch driver as valid even though it was downloaded from the official Speedtouch link found at the ndiswrapper site. Without an internet connection for Linux I can't use the apt-get command.
Thanx

---

### Post by kilroy423 on 2007-02-26
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

just grab the tarball on your "internet" computer and burn it to a disk....or like what I did is plug an ethernet cable in and go through the packet manager

if your worried about the version of ndiswrapper try a 

```
ndiswrapper -v
```

not on linux atm so run a man ndiswrapper and see if v is the correct option

---

