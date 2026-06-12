---
title: "re-install ubuntu desktop over ubuntu server"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by mcbenton on 2007-05-31
Hi,

I'm a linux newbie.  (probably obvious since I'm posting in this forum)

I just installed Ubuntu Server Edition on an older PC.  All I really wanted was a LAMP server with a GUI desktop to manage it from.  Didn't realize that this edition didn't include a desktop.

So I burned the Desktop edition CD and tried to install, but instead of installing, Ubuntu just appears to be running from the CD.

How can I get rid of the Server edition install, and start over with the Desktop edition?

Thanks,
Morgan

---

### Post by xela321 on 2007-05-31
You should be able to run:
```
sudo apt-get install ubuntu-desktop
```
This will install GNOME and allow you to use the machine as a desktop.

Hope that helps

---

### Post by lazyart on 2007-05-31
You can add a GUI to the server -```
sudo apt-get install ubuntu-desktop
```
or kubuntu or xubuntu.

---

### Post by GabrielDunn on 2007-05-31
If you want to make the switch boot with the g-parted live CD and format then boot from the desktop cd and do a fresh install.

---

