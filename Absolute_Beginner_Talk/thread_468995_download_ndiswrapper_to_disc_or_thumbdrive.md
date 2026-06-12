---
title: "download ndiswrapper to disc or thumbdrive?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Stew2 on 2007-06-09
Hi all, quick question. I'm sure its been asked  before but I couldn't find it :). I was wondering if it is possible to download the ndiswrapper package for feisty and save it to a disc or thumbdrive so that I can install it on a machine with no internet access to download it itself. Seems the ndiswrapper package is not included in the default Feisty install and the only net access I have on that computer is wireless. Is there a way to do this? Thanks in advance :D

---

### Post by Outrunner on 2007-06-09
I think it is included on the CD

```
sudo apt-cdrom add
```

```
aptitude search ndiswrapper
```
```

sudo aptitude install <program>
```

EDIT: If it isn't on the CD, you can download it from here [http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main)

---

### Post by Stew2 on 2007-06-09
Thanks Outrunner, I'll check it out :D

---

### Post by Stew2 on 2007-06-09
I downloaded it to my thumbdrive just in case it isn't on the disc. Exactly what I was looking for. Thanks again!

---

