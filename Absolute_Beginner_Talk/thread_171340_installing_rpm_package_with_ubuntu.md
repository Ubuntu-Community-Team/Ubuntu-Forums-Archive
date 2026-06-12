---
title: "installing rpm package with ubuntu"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by patanjali on 2006-05-06
Please can anyone tell me how to install rpm pfiles in ubuntu?

Thanks in advance

Patanjali  :confused:

---

### Post by jazzmuzik on 2006-05-06
Rpm files are for Redhat/Fedora based systems. Ubuntu is a Debian based distro and uses the deb package format. You can convert an rpm file to a deb with the 'alien' program. But your best bet is to look for a package compiled on a Debian based system (Ubuntu ideally) in the deb format already.

---

### Post by patanjali on 2006-05-06
How do I get this "alien" programme?

---

### Post by Sandlst on 2006-05-06
```
sudo apt-get install alien
```Then to use it (no gui) ```
sudo alien /path/to/rpm/file.rpm
```Cant remember if sudo is necessary......
Lastly ```
sudo dpkg -i /path/to/new/debfile.deb
```

---

### Post by patrick295767 on 2006-05-06
```
alien -i  myrpm.rpm
```
to install the rpm
  
```
alien -d  myrpm.rpm
```
to make the deb file 
(for dpkg -i )
  
I would recommand you to use sources, with 
```
./configure ; make ; make install
```
  
Greetings

---

### Post by aysiu on 2006-05-06
You an .rpm only if you can't find a .deb.

---

