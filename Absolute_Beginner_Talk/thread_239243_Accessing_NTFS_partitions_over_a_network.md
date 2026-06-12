---
title: "Accessing NTFS partitions over a network"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by WeeGraeme on 2006-08-19
Several times now, I've tried to view XP drives and directories over the network.  I can get it to work, but then find that after a short period of time, I can no longer access them over my network.  I want to learn how to fix all this myself, but I don't even know what programme, utility, or whatever it may be is responsible for this type of network activity.

I still have the shortcuts on my Ubuntu desktop, but when I click on the icon, I receive an error message saying that it's unable to read all the contents.  (It doesn't display any of the contents.)

At the same time as this disappears, if I try to setup a connection to another server, and I click on "Browse network" then "Windows Network", all the machines which were previously visible are no longer there.  (I'm adding all this in the hope that it clarifies for someone what I'm trying to describe, not so that you can give me a quick fix.)

---

### Post by seshomaru samma on 2006-08-19
I think you need to install Samba
Please follow [this]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba") guide

---

### Post by secretlondon on 2006-08-19
> **WeeGraeme said:**
> Several times now, I've tried to view XP drives and directories over the network.  I can get it to work, but then find that after a short period of time, I can no longer access them over my network.  I want to learn how to fix all this myself, but I don't even know what programme, utility, or whatever it may be is responsible for this type of network activity.


I'm a real noob with this myself but the program that deals with windows network shares is called SAMBA. [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

However that says for what you want (accessing shared files on windows computers) you only need the smbfs plugin. Alas the page the wiki links to for intructions seems to have been moved/deleted - but I've found it here:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29")

---

### Post by secretlondon on 2006-08-19
> **seshomaru samma said:**
> I think you need to install Samba
Please follow [this]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba") guide

I *think* they just need the plugin, as they are being a client not a server.

---

