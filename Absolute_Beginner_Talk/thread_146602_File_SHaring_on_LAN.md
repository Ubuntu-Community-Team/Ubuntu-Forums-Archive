---
title: "File SHaring on LAN"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Squatpuke on 2006-03-18
.
.
I have 3 PC's (W2kP, Ubuntu, XP) running under one DLink/DHCP soho router...

The ubuntu box does not show in Computers Near Me, nor does the MS boxes show under "WIndows Network" in Network Servers...

What needs to be done to enable this?


Yes...I'm a noob.

---

### Post by Stealth on 2006-03-18
Install Samba:

sudo apt-get install samba

Then I believe you will need to set up a Samba password so you can access your Ubuntu machine from the Windows machines...

smbpasswd

You'll get a dialog for username and p/w when accessing the Ubuntu machine from Windows, with username being ur current one, and p/w being the one you just set...:mrgreen:

---

### Post by Treebeard on 2006-03-18
See [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba) for more info.

---

