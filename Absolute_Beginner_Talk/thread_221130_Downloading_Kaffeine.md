---
title: "Downloading Kaffeine"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by mbrang00 on 2006-07-22
Hi All,

I found a post telling me that Kaffeine is the = to Media Player...Well I dont know how to go about downloading and installing programs. Can someone give me a quick walk through on downloading and installing Kaffeine?


Thanks in advance

---

### Post by not_yet on 2006-07-22
from the top toolbar

system / administration / Synaptic Package Manager

search for your program 

click on it and pick apply

---

### Post by Ziox on 2006-07-22
first of you have enable the extra repositories (check my signature), then you have to do 
sudo aptitude update, 
which grabs the most recent versions of everything, and then you should do
sudo aptitude dist-upgrade, but you don't have to.

to install kaffeine or any program that's in the repositories, do:

sudo aptitude install <application name>
ex: sudo aptitude install kaffeine

read my second to last link (in signature) that says: new help in general. its a great guide that will be a great help to you, and anyone new to linux/ubuntu

EDIT: there are many ways to install apps, alot of people tells you to use sudo apt-get, but using sudo aptitude is better, because it resolves dependencies much better, and if you every you uninstall the software, sudo aptitude remove will remove all of the extra programs that came with the original program.  Again check the second to last link.

---

### Post by Jucato on 2006-07-22
Kaffeine is KDE/Kubuntu's media player and is installed by default. No need to download/install

But Ubuntu/GNOME has its own media player called Totem. You might want to try that out first before you install Kaffeine. If it works for you, then you wouldn't have to download something else. Saves you the hassle :D

---

