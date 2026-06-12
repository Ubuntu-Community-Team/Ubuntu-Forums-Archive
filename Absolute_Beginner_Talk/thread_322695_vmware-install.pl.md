---
title: "vmware-install.pl"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by dagamer on 2006-12-20
can anyone tell me how to install a .pl file for vmware it would be very much appreciated.

---

### Post by GuitarFingers on 2006-12-20
Go to a command line and from the directory where the file is type:

sudo ./vmware-install.pl

This assumes you have perl installed which you should have by default or you can install it using synaptic. Also it assumes the file is executable. If it isn't then from the same directory type:

sudo chmod ug+x vmware-install.pl

and then run the first command.

---

