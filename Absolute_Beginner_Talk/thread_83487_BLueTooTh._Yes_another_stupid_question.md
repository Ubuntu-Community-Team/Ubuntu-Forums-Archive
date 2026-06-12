---
title: "BLueTooTh. Yes another stupid question"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-28
I am using GNOME and was wondering which Bluetooth app to install ?
I installed gnome-bluetooth but i can't seem to find my device with it (using an ericcson T610).

I was using Bluez under KDE but I uninstalled KDE.

---

### Post by joselin on 2005-10-28
I have the same phone.

You must install the following packages:
bluez-pin
bluez-utils

You can see the configuration files on /etc/bluetooth

Regards

---

### Post by nitricacid on 2005-10-28
along with gnome-bluetooth?
It won't find my phone and my phone will not find my pc.

---

### Post by skydvrgrl on 2005-10-28
When I configured my bluetooth for my mouse I just installed all the bluetooth stuff! Yeah its a noobish thing to do but I am a noob, and besides it was the only way to get my mouse connected. I also used 

sudo hidd --server --search

that connects the item. 

If that helps I am glad, if not oh well! :D

---

### Post by joselin on 2005-10-29
You must activate the bluetooth in your phone, then go Applications, System Tools, Bluetooth Manager and from there, File - Scan. Your phone must appear.

Regards,

---

### Post by nitricacid on 2005-10-29
[QUOTE=joselin]You must activate the bluetooth in your phone, then go Applications, System Tools, Bluetooth Manager and from there, File - Scan. Your phone must appear.

Regards,[/QUOTE]

Did all that and nothing. My computer finds the fone but my fone does not find the computer and i can't transfer anything.

---

### Post by joselin on 2005-10-31
[QUOTE=nitricacid]Did all that and nothing. My computer finds the fone but my fone does not find the computer and i can't transfer anything.[/QUOTE]

Check the configuration files under /etc/bluetooth, you probably must modify hcid.conf

Read this post too --> [http://ubuntuforums.org/showthread.php?t=75978]("http://ubuntuforums.org/showthread.php?t=75978")

---

