---
title: "vm ware doesn' work"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by kalamara on 2008-03-08
when i install vm ware on Ubuntu 7 it start installation very well then write on screen that will search about the sutibale module then write on screen that it can't find the sutibale and it need the source code for Linux then it fail what can i do ?

---

### Post by freelinuxhelp on 2008-03-08
You can install the Linux source with this command:
sudo apt-get install linux-source

---

### Post by anaconda on 2008-03-08
no, no, no, noo

vmware requires you to have 2 packages
and here is how to install them (from terminal):
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

I suggest you copy-paste this command to your terminal, because the ` needs to be the correct one. so no ' and no ' but ` otherwice it wont work..

then try it again..

---

