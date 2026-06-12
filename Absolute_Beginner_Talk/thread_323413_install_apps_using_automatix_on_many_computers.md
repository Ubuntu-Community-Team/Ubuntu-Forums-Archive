---
title: "install apps using automatix on many computers"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by hudanet2005 on 2006-12-22
does any one here know how to install apps using automatix on many computers to save bandwith?

for example: i want to install google earth and google picasa, using automatix on many computers. the bandwith is limited, is it possible after install on one computer, i copy the google earth and google picasa installer to another computer and then using automatix, they will be installed without downloading the google earth and google picasa anymore? 

thank you in advance

---

### Post by aysiu on 2006-12-22
Are these many computers all the same hardware? If so, you can just clone the entire installation using PartImage or *dd*.

---

### Post by hudanet2005 on 2006-12-22
many computers with different hardwares. for your info, i prefer to use I386 installer. thank you in advance. right now everytime i want to install apps using automatix, i have to connect to internet. very time consuming!!! ](*,) ](*,) ](*,)

---

### Post by aysiu on 2006-12-22
Well, things like Google Earth and Picasa may be a different story, but everything Automatix installs using the package manager should be stored in /var/cache/apt/archives

Copy those to a CD and then *cd* (change directories) to that CD and ```
sudo dpkg -i *.deb
``` and that should install all those applications without using the internet.

---

