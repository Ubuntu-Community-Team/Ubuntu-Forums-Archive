---
title: "wireless not picked up on start up"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-01-10
Hi all, I have finally managed to install (using ndiswrapper) the driver for my wireless card ( thanks to the help that I have had on this forum). The problem I am having at the moment is that I am not able to get the driver to be picked up on start up. 
any ideas on what i need to do to get it picked up on start up.
I used the following commands thus far

ndiswrapper -i
ndiswrapper -m
modprobe ndiswrapper 


thanks...

---

### Post by Dr. Nick on 2006-01-11
If running modprobe ndiswrapper fixes it, then edit the file /etc/modules by running  **sudo gedit /etc/modules **just add the word ndiswrapper to the top of the list, that should load it on boot. Also if you have a wired card you may use the networking gui to disable it if you dont use it often, sometimes wired/woreless conflict

---

