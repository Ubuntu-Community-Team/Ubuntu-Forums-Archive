---
title: "Removing Debian Menu"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by Burgresso on 2005-11-06
I recently installed Debian menu...but I don't like it. How may I uninstall it (what is the package name?) And since it is better to teach a person how to fish, how could I have figured it out ? Thanks a bunch! :)

---

### Post by Xian on 2005-11-07
[QUOTE=Burgresso]I recently installed Debian menu...but I don't like it. How may I uninstall it (what is the package name?) [/quote]

$ sudo apt-get remove menu-xdg

[QUOTE=Burgresso]And since it is better to teach a person how to fish, how could I have figured it out ? [/QUOTE]
By remembering what you installed. :)

$ sudo gedit /var/log/dpkg.log

---

### Post by Burgresso on 2005-11-07
Thanks Xian!

---

