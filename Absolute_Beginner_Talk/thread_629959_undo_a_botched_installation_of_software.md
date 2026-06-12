---
title: "undo a botched installation of software"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by yeehi on 2007-12-02
I tried to install java jdk.
It all went well, but i didn't complete the "i agree" section of the end user agreeement, by clicking on "OK" - I didn't understand that i had to use tab to navigate to the OK.

i aborted the installation by just quitting that terminal.

How do i uninstall this effort at jdk so that i can try and set it up again properly?

---

### Post by Threbus5 on 2007-12-03
If you attempt another installation, do you receive a message that the software is already installed? If not, then just reinstall.

If so, try a search for the software components and remove them. If the package is one that accepts removal from the remove/install package manager try that followed by another install.

If package uninstall fails consider the semi brute force method. Search for components using the file search from the gui and delete from the terminal window. But make sure that you remove components unique to the jdk.

Good luck.

---

### Post by yeehi on 2007-12-03
I tried to install jdk by using apt, which did a download.

How could i attempt reinstallation, without having to re-download?

---

### Post by jordanmthomas on 2007-12-03
It should automatically use the one you've already downloaded if you just try to install again.

---

### Post by yeehi on 2007-12-04
iiuc, i have again  been prompted to agree to the EULA. I think i am ok now :)

Thank you all.

---

