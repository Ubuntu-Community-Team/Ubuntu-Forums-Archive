---
title: "I am having troubles installing a .deb package via the terminal for nidswrapper."
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by GregoryMA on 2007-06-03
I am going through the ndiswrapper installation process ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)) but when I try to install the ndiswrapper-utils_1.8-0ubuntu2i386.deb package I get this error.

gregory@gregorylaptop:~/Desktop$ sudo dpkg -i ndiswrapperutils_*.deb
dpkg: error processing ndiswrapperutils_*.deb (install):
cannot access archive: No such file or directory
Errors were encountered while processing:
ndiswrapper-utils_*.deb

The file is on the desktop so I do not know why it isn't working.  Any suggestions would be appreciated.

Thanks, Greg.

---

### Post by dfreer on 2007-06-03
try installing it with the actual filename and not with the wildcard in there, and then post your results.

EDIT: also, you typed the command wrong, there should be an - in between ndiswrapper and utils

---

### Post by PilotJLR on 2007-06-03
You can also double-click it on your desktop to install it.


Here's a vital command line trick... type out the first few letters of a file (enough to make it unique), and press the Tab button, and bash will fill in the rest for you.

---

### Post by GregoryMA on 2007-06-05
Thanks for the help.  I gave it another go and it worked.  I am not sure what I did differently but all's well that ends well.

---

