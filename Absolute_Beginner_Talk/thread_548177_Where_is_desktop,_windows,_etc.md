---
title: "Where is desktop, windows, etc?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by rachlin on 2007-09-11
Just installed ubuntu-server. I have only a command line interface. How do I turn on windowing, graphical interface, etc?

---

### Post by Lacrimstein on 2007-09-11
the ubuntu server comes without any graphical interfaces (since many servers don't have graphical displays). but fixing that is easy. just type in:


sudo apt-get install ubuntu-desktop    //for GNOME
sudo apt-get install kubuntu-desktop  //for KDE
sudo apt-get install xubuntu-desktop //for Xfce

---

### Post by Chris S. on 2007-09-11
Or, reinstall using the Ubuntu Desktop CD.  You can easily install all the server components from there.

---

### Post by rachlin on 2007-09-11
The install attempt returned "package not found" for all three. WOuld thatbe because I don't yet have my network connectivity?

---

### Post by rachlin on 2007-09-11
If I install from the desktop CD, can I still run it as a server: namely run apache, ftp server, etc?

---

### Post by glotz on 2007-09-11
Yes and yes.

---

### Post by Chris S. on 2007-09-11
Look for HOWTOs on setting up a "LAMP server" in Ubuntu.  As I understand it, that's what you get when you install the Ubuntu Server version.  Someone help me with the acronym: LAMP = Linux, Apache, MySQL, PHP?

---

### Post by glotz on 2007-09-11
e.g. [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by BrendanM on 2007-09-11
Yeah, make sure your network connection is working. You can use **ifconfig** to see the configuration of your network interfaces. Once you get networking working, you can just do "sudo apt-get install ubuntu-desktop" to get a full GUI.

---

