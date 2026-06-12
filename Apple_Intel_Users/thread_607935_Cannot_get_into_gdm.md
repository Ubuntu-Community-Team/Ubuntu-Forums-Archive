---
title: "Cannot get into gdm"
date: 2007-11-09
forum: Apple Intel Users
---

### Post by schauerlich on 2007-11-09
I'm on an iMac (specs in signature), and I need to install the fglrx driver. However, I can't get into gdm, and when I try to download the drivers via the command line (following [these instructions]("http://ubuntuforums.org/showpost.php?p=3641579&postcount=9">these instructions")), but I get a "could not resolve" error after the second line. What do I need to do to be able to get in GNOME?

---

### Post by cyberdork33 on 2007-11-09
> **EDavidBurg said:**
> I'm on an iMac (specs in signature), and I need to install the fglrx driver. However, I can't get into gdm, and when I try to download the drivers via the command line (following [these instructions]("http://ubuntuforums.org/showpost.php?p=3641579&postcount=9%22%3Ethese%20instructions")), but I get a "could not resolve" error after the second line. What do I need to do to be able to get in GNOME?

This should start gnome directly:
```
sudo /etc/init.d/gdm stop
startx
```

---

