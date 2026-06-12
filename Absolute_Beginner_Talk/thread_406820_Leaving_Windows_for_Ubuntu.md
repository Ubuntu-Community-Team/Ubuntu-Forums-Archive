---
title: "Leaving Windows for Ubuntu"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by colonist on 2007-04-11
I have left Windows for Ubuntu and am reading several books on Ubuntu and Linux to try and figure out how to network my Ubuntu box to an existing Window Lan which has a network printer.
I am having a problem understanding what i need to do to install and configure Samba.

---

### Post by heimo on 2007-04-11
You don't need samba if you're only connecting to Windows shares. In that case you'll need smbfs.
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

[]("https://help.ubuntu.com/community/SettingUpSamba")This seems to be guide to print to printers shared by Windows:
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

Here's how to set up samba (in case you still need it):
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by oli888 on 2007-04-11
Hi,

Try this link - [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)

Oli

---

