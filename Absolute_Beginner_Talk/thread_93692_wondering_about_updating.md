---
title: "wondering about updating"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by aresgoddess on 2005-11-22
Hi, I was wondering about updating from Hoary Hedgehog release to the Breezy Badger release. do i need to? if so, how do i do that? will i need to backup my files like when i switched from windows to ubuntu? any advice/help is greatly appreciated. =)

---

### Post by Brunellus on 2005-11-22
back up your files, just in case.

then 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.backup
```

that backs up your sources list for apt.  Then

```
 sudo gedit etc/apt/sources.list
```

wherever "Hoary" appears, replace it with "breezy".

save your new sources.list  then ```
sudo apt-get update
``` 
then
```
sudo apt-get dist-upgrade
```

sit back and watch it cook.

---

### Post by aysiu on 2005-11-22
If Hoary's working just fine for you, there's no reason to upgrade to Breezy. I'd upgrade to Dapper in April, though.

---

### Post by aresgoddess on 2005-11-22
[QUOTE=Brunellus]back up your files, just in case.

then 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.backup
```
[/QUOTE]

do i enter the code into a terminal? or somewhere else?

---

### Post by Axeface49 on 2005-11-22
yes, you enter that in console. :)

---

### Post by aresgoddess on 2005-11-22
thanks a whole bunch! ^_^

---

