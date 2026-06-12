---
title: "ntfs 3g for kubuntu"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2007-04-16
I want to install ntfs 3g on kubuntu 6.10

the tutorial for that is for ubuntu with commands in(for) gnome.

please help me in installing it for kubuntu.

---

### Post by miggols99 on 2007-04-16
First add the repositories in your sources list:
```
kdesu kate /etc/apt/sources.list
```
Add these at the bottom:
```
deb http://flomertens.free.fr/ubuntu/ edgy main main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
deb http://flomertens.keo.in/ubuntu/ edgy main main-all
```
Add the gpg key:
```
wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -
```
And update your system:
```
sudo apt-get update
sudo apt-get upgrade
```
Now install the packages:
```
sudo apt-get install ntfs-3g ntfs-config
```
Now enter the ntfs config:
```
kdesu ntfs-config
```
Now you can read/write NTFS partitions!

---

### Post by miggols99 on 2007-04-16
Oops double post. Please delete.

---

