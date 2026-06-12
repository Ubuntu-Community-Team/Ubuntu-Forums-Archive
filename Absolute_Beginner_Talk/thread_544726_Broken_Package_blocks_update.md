---
title: "Broken Package blocks update"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Abetorius on 2007-09-06
I've got broken package 'gnome-btdownload'. When I try to update Feisty system freezes when trying to reinstall this package.
I tried to remove it manually but I ge message that it should be reinstall before removing.
After some digging I've found option for dpkg that forces package romoval without reinstalling it (remove-reinstreq) but I cannot get syntax right.
Anyone can help me with that?

---

### Post by Harpoon on 2007-09-06
dpkg --force-remove-reinstreq ???

never had to use it, myself.  look in dpkg --force-help

---

### Post by Abetorius on 2007-09-07
After some sleep I've figured it out:

> sudo dpkg --remove --force-remove-reinstreq gnome-btdownload

---

