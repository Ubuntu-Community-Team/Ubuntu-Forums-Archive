---
title: "how to restore gdm.conf to it's original settings"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by iiker on 2007-02-07
The problem is that i made some changes in that file and now my ubuntu can't load graphical interface. any way to restore gdm.conf file to it's original contents?
thanks!

---

### Post by sunexplodes on 2007-02-07
in console: dpkg-reconfigure gdm

---

### Post by iiker on 2007-02-07
it didn't help!

---

### Post by sunexplodes on 2007-02-07
try the same command, but instead of gdm, try xserver-xorg

---

### Post by iiker on 2007-02-07
didn't help either :(

---

### Post by sunexplodes on 2007-02-09
okay, try

sudo apt-get install &#8211;reinstall xserver-xorg
sudo apt-get install &#8211;reinstall gdm

and see if that helps

---

