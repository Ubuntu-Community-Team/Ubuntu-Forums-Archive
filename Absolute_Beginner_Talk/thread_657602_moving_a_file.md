---
title: "moving a file"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-03
I am trying to move my azureus folder from my Desktop to /usr/bin.  I tried another way of getting it in there by downloading it directly in /usr/bin.  Got an error about the contents not modifiable.  So I tried again to cp it from the desktop.  I get an error saying that the folder is being removed.  It doesn't ever remove it though.  Any help is appreciated.

jhvillegas2

---

### Post by Dr Small on 2008-01-03
Use sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2008-01-03
If you want to move files/directories to anywhere outside your $HOME directory, you need root privilege.  Therefore, you need to use sudo from a terminal or run nautilus as

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

