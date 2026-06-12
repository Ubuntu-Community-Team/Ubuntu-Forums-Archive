---
title: "install flash"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by entropy7 on 2006-07-08
hi all-
i was trying to install Flash on 5.10. well i found the how-to and it says to type the following command:

sudo apt-get install flashplugin-nonfree

that returned the message:

E: Couldn't find package flashplugin-nonfree

I downloaded something called:flashplugin-nonfree_7.0.63.5_i386.deb

when i type:
sudo apt-get install flashplugin-nonfree_7.0.63.5_i386.deb

it still says it can't find it,   Please help me out here, thanx

---

### Post by woedend on 2006-07-08
use
sudo dpkg -i *.deb
where * is is the name(or you can use * if you want)
instead of apt-get to install a deb on your hard drive

---

### Post by entropy7 on 2006-07-08
OK, that is getting better. Still seems to be a problem though:

Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 61341 files and directories currently installed.)
Unpacking flashplugin-nonfree (from flashplugin-nonfree_7.0.63.5_i386.deb) ...
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on gsfonts-x11; however:
  Package gsfonts-x11 is not installed.
dpkg: error processing flashplugin-nonfree (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree

---

### Post by entropy7 on 2006-07-08
is gsfonts installed - i shoulda checked before sending the post:rolleyes:

---

### Post by aysiu on 2006-07-08
> **entropy7 said:**
> hi all-
i was trying to install Flash on 5.10. well i found the how-to and it says to type the following command:

sudo apt-get install flashplugin-nonfree

that returned the message:

E: Couldn't find package flashplugin-nonfree Make sure you have the right repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by entropy7 on 2006-07-09
is there more than one repository?

other than that, flash now works my the linux system, thanx

---

