---
title: "HELP! not detecting modem-line error-going futz"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by diogenes on 2005-09-16
Okay -just installed Ubuntu two days ago and work off a dial up line.
after figuring out where to put my ISP info (modem Properties) and setting up network info through command line.  I realized wvdial is not installed.  tryied to install it through synaptic and recieved the following error:

E: malformed line 1 in markings file
E: malformed line 1 in markings file
E: malformed line 1 in markings file
E: Unable to lock the download directory

any attempted install through synaptic gives this result.

help?

---

### Post by towsonu2003 on 2005-11-24
try ```
sudo apt-get update
sudo apt-get wvdial
```with the install CD in the CD drive... But weird, because wvdial was already installed in my first ever install... I know bc I don't have any other means of connecting & downloading with this @$%#@$%@#$% winmodem...

edit: remembering you don't have internet, you may need to look around on how to get it in.deb format... have no idea about that...

---

