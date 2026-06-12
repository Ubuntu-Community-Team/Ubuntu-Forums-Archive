---
title: "problem with installing network-manager!help!"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by jaywee on 2007-05-11
I down the souce package of networkmanager from gnome ftp,while I run ./configure,there is a error:
```
checking for wireless-tools >= 28pre9... no
configure: error: wireless-tools >= 28pre9 not installed or not functional
jaywee@Cheung:/media/sda6/NetworkManager-0.6.5 (2)$ 
```
then I run sudo apt-get install wireless-tools, it told me wireless-tools is already the newest version.
Faint! I am really anxious about this, hope someone may help me !!!THX!!

---

### Post by mfichifichi on 2007-05-11
check your package manager for some kind of 28pre9-dev headers or download the header files? Just guessing.

---

### Post by jaywee on 2007-05-12
Thanks but it doesn't work!

---

### Post by seltak on 2007-06-11
```
sudo apt-get build-dep network-manager
```
this did the trick for me. And there is how to compile the network manager from cvs
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

