---
title: "Uninstalling Ubuntu 5.10 (completely)"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by BIKO on 2006-06-13
I installed Ubuntu 5.10 and used the 'Terminal' application for the first time this morning. How do Uninstall it, to do it all over again. I cant use Ubuntu 5.10, yet, I think.

---

### Post by echo $USER on 2006-06-13
Uninstall terminal or OS?  If you mean the OS just put another OS disk in and install the new one.  When it formats the disk it is "uninstalling the OS", sorta.

---

### Post by ajgreeny on 2006-06-13
It appears you may have installed the server only and tp uninstall will depend on whether or not you have a dual boot system with Windows, and how your partitions are set up.  Give us more information and we'll help as much as possible.

Alternatively, if you mean you want to keep ubuntu, you could simply login using the user name and password you set up at install, the type "startx" without the quotes to see if you have a desktop environment available such as GNOME.

If you don't, then just type "sudo apt-get install ubuntu-desktop" and assuming you have the machine connected to the internet, it will download and install the desktop for you.  If you have no internet for the machine, perhaps you need to install again.  There is no need to uninstall first, as your current install will be wiped off as you reinstall.

This time however make sure you install the full system, not just the server.  If you just hit enter when the CD has booted it should do it automatically for you.  Good luck!

---

