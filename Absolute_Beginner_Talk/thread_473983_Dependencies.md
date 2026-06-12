---
title: "Dependencies"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ArtesMagae on 2007-06-14
As I install applications through either Synaptic or the GNOME Add/Remove, I notice some applications require a fair amount of dependencies. When I go to uninstall the applications, no mention of the dependencies being removed is made. I discovered the command "sudo apt-get remove <package> --auto-remove" which removes more then Synaptic or Add/Remove, but I don't think it gets everything. Is there a way to uninstall all these dependencies so that a year from now I don't have half a million unused libraries? 

Feel free to tell me I am just simply making a big deal out of nothing!

Thanks in advance.

---

### Post by w4ett on 2007-06-14
try sudo apt-get autoremove

---

### Post by arvevans on 2007-06-14
These URLs 

[http://www.cyberciti.biz/tips/debian-linux-remove-unwanted-packages-and-files-to-reclaim-disk-space.html]("http://www.cyberciti.biz/tips/debian-linux-remove-unwanted-packages-and-files-to-reclaim-disk-space.html")

[http://www.debian.org/doc/FAQ/ch-pkgtools.en.html]("http://www.debian.org/doc/FAQ/ch-pkgtools.en.html")

address some of your concerns.
_._

---

