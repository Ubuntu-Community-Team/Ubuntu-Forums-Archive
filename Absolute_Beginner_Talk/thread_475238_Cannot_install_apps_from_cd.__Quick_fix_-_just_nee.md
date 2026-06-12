---
title: "Cannot install apps from cd.  Quick fix - just need direction!!!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ejw2076 on 2007-06-15
I know there is a way to set up ubuntu to only install software from repositories on the internet, but I can't find it anywhere.  Can someone please post the link or give me a quick tutorial?

---

### Post by vpjr on 2007-06-16
hi,

(I'm assuming you're using Ubuntu 6.10)

Try clicking the following:

System -> Administration -> Software Sources

The repositories menu should come up then.  Left click on what you want to source apps from and then apply.  Afterwards:

Applications -> Add/Remove

Which should make bring up the Add/Remove Application menu where you can now pick and choose what application you want installed. 

regards,

ven

---

### Post by seshomaru samma on 2007-06-16
if you want software only from repositories all you need to do is disable the CD repository in your sources list.
```
sudo gedit /etc/apt/sources.list
```
look for a line that says Ubuntu CD or something similar ,like this:
```
 deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```
 and put a # in front of it, like this:
```
 # deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```
next update your sources list :
```
sudo apt-get update
```

---

