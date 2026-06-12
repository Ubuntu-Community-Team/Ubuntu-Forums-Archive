---
title: "wireless-tools &gt;=28pre9 error"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by holy*cow on 2007-03-20
hello
please help I am trying to connect to a wireless internet and am trying to install gnome network manager. I am running Ubuntu 6.10. When I try to configure I receive the message
configure: error: wireless-tools >=28pre9 not installed or not functional.
I have downloaded and installed libiw-dev and I still receive this message. I do not have a way to easily connect to the internet on the Ubuntu machine and am posting and downloading from a windows machine.
please help I am new to Ubuntu and Linux.

---

### Post by seltak on 2007-06-11
```
sudo apt-get build-dep network-manager
```
this did the trick for me. And there is how to compile the network manager from cvs
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

