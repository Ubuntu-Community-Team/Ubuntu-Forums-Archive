---
title: "vmware server"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by chrisderuijter on 2006-09-25
How do i completely remove vmware server (and all vmware data) from my system i successfully removed the program bu all the data is still there (/etc/vmware etcetera..).

---

### Post by bluefrog on 2006-09-25
sudo rm -rf /etc/vmware (be careful at what is written before hitting Enter...)

or use gksudo nautilus and explore your computer from there with root access/rights

James

---

### Post by Mime on 2006-09-25
There's an uninstall script included with the install files.  Run that as root and it should remove all the files and stuff that was installed.  That might be safer than nuking everything manually.

If you have the web based interface installed also, there's a separate uninstall script for that.

---

