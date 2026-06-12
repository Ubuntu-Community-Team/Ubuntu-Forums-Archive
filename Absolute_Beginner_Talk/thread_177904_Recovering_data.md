---
title: "Recovering data"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-17
I've installed kubuntu recently but i have another disk with ubuntu with some documents i need the retrive.I think that second disk is formated in ext3 but i can't access it.Can you help me please?I'm newbie with linux =X

---

### Post by aysiu on 2006-05-17
Paste this command into a terminal: ```
sudo fdisk -l
``` It'll tell you the location of your second hard drive. Let's just assume for this example that it's /dev/hb1 and ext3 ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hdb1 /recovery
gksudo nautilus
``` Go to the /recovery directory and copy those files over.

Of course, if it's not Ext3, substitute in the appropriate filesystem. If you're using KDE, do ```
kdesu konqueror
``` as the last command.

---

