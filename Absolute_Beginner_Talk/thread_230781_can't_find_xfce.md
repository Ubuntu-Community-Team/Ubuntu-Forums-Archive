---
title: "can't find xfce"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by cebobbitt on 2006-08-06
Hi all, I installed xfce and IceWM yesterday. Played around with them and made some cosmetic changes, font size, ect.  The update manager tells me that I have 145 updates to install. So last nite I left my machine on and this morning I only had 17 left to update. So I rebooted my machine and when It got to the log on screen I chose my session. It showed gnome and IceWM, but no xfce. I looked in the file system and it still shows xfce, but when I type xfce in the run box on alt+F1 it says it can't open xfce in the metacity window manager. So how do I get to it?  I'm new to Linux and computers in general. Also, if the update manager says that you have new kernels to update is this a real necessity? I'm so afraid of hosing my system. Thanking you in advanced for your help

---

### Post by orb9220 on 2006-08-06
You should NEVER Reboot during an update it has to download ALL the packages before it can begin to install and configure them on your system.

Sorry but that's the way I understand it.

---

### Post by catlett on 2006-08-06
You do not need to update kernels. If you wanted to you could keep the same one forever but they keep updating, patching and improving the kernel so it is usually a good idea to take the new kernel. You may have to reconfigure some things when you get a new kernel. For instance your nvidia drivers depending on your installation method will have to be reinstalled.
Anyways, xfce should be there at login when you select session. The updater may have been in the process of updating it. Try updating/upgrading with aptitude. Aptitude should sort it all out.
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

