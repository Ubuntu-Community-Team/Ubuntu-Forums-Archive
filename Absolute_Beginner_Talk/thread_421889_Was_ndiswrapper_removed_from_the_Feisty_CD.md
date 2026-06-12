---
title: "Was ndiswrapper removed from the Feisty CD?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Supercross on 2007-04-24
Can anyone confirm that ndiswrapper wasn't included on the Feisty installation cd?  I need ndis to get my wifi up and running and its no where to be found in the package manager and I find one post here where someone stated it wasn't included on the cd, but why was this done by Ubuntu?  Also, since I have a dual boot Xp/Ubuntu, can I just download the files onto a windows partition then mount that partition in Ubuntu and install it manually that way?

---

### Post by Bachstelze on 2007-04-24
I didn't know ndiswrapper was removed from the Feisty CD but yes, you can download the packages from Windows and manually install them in Ubuntu. Download the packages form [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them with

```
sudo dpkg -i filename.deb
```

---

### Post by Kobalt on 2007-04-24
Yes I've also read somewhere that ndiswrapper wasn't on the Feisty CD... sad. 
You can download packages from another OS, from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then import and install them under Ubuntu.

---

