---
title: "Internet doesn't work on Ubuntu"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Sordelka on 2007-11-30
Well, it works on Windows. I use D-Link Wireless USB Adapter and triesd all the stuff usual guides for installation say. Nothing worked...what to do?

---

### Post by gigaferz on 2007-11-30
what did you do?

did you try ndiswrapper?

install it from the repositories (synaptic package manager)and get the drivers ready.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

go to the install windows driver section, read carefully and keep going.

 after entering the information to your device you need to type "sudo dhclient wlan0" to activate the adapter.

---

### Post by insineratehymn on 2007-11-30
> **gigaferz said:**
> what did you do?
Indeed.

---

