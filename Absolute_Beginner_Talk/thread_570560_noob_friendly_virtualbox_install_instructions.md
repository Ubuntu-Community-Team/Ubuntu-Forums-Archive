---
title: "noob friendly virtualbox install instructions"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-10-08
im a n00b and i want to install virtualbox as there are some windows only apps that i need to be able to use

if someone could give me good instructions that are easy to follow that would be great
thanks in advance

---

### Post by Dr Small on 2007-10-08
```
sudo nano /etc/apt/sources.list
```
Then add the following line to the bottom:
```
#Innotek repos or VirtualBox
deb http://www.virtualbox.org/debian feisty non-free
```
Download the key:
```
wget http://www.virtualbox.org/debian/innotek.asc
```
Install the key:
```
sudo apt-key add innotek.asc
```
Then do a:
```
sudo apt-get update
```

Install VirtualBox:
```
sudo apt-get install virtualbox
```
Add yourself to the vboxusers group:
```
sudo addgroup *username* vboxusers
```
Where "*username*" is your log-in name.

Logout, so adding yourself to vboxusers can take effect.
Log back in.
Start VirtualBox:
```
VirtualBox
```

Dr Small

---

### Post by antisocialist on 2007-10-08
at the step where i type
sudo apt-get install virualbox
i got this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox

any ideas?
i did everything else and it worked. at the sources.list i added the line closed terminal opened again and did the rest of the stuff

---

### Post by funrider on 2007-10-08
this is from the how-to sub forum:

[http://ubuntuforums.org/showthread.php?t=340113&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=340113&highlight=virtualbox)

---

