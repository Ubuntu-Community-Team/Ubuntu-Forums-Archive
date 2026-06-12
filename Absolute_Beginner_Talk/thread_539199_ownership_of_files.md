---
title: "ownership of files"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by bobbyross on 2007-08-30
I am trying to edit the /etc/network/interfaces file but it is read only.  I am a noob with any sort of linux, but I am the owner of the machine and it seems odd that I cant change files like I could in XP.  

All I am trying to do is follow the wireless card install here: [https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111#head-5067d4930d3df81e777290c62dc38d489f8ef1c5](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111#head-5067d4930d3df81e777290c62dc38d489f8ef1c5)

but cant get past the file edit.

SOS!

---

### Post by ThrobbingBrain66 on 2007-08-30
Open the file like this:

```
gksudo gedit /etc/network/interfaces
```

If you're using the command line and want to edit a system file use 'sudo'
if you're using a graphical program to edit a file use 'gksudo'

This is for any file not located in your /home directory

---

