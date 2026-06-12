---
title: "Network Manager"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by mjbjer333 on 2007-04-28
In setting up my wireless network with a Linksys wireless router on Xubuntu edgy eft, I am unable to get NetworkManager to recognize the wireless network. The Icon is showing in the system tray, but only displays enable networking and about as options. I have read the following info, but am not finding the information that I needed: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) Any suggestions?

---

### Post by spd106 on 2007-04-29
Which wifi card do you have?
The output of these commands will give you a clue
```
lspci
```
```
iwconfig
```

Please ensure that all interfaces (except lo) that you want to manage have been commented out in the /etc/network/interfaces file and that you have either rebooted or restarted dbus.

---

