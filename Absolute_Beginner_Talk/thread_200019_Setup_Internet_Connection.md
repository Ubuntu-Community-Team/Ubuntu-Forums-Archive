---
title: "Setup Internet Connection"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by rogfam06 on 2006-06-19
I use a linksys router to connect via cable modem and was wondering how I exactly can enter my network connection settings in UBUNTU? IP addr...subnet..default..exc...:D

---

### Post by medw1974 on 2006-06-19
Ok, this is my first attempt at answering a question here, so please treat my advice with care as it may be totally wrong.

If the router had previously been setup in windows/another distro ubuntu should pick up the settings.

If it is a new router the instructions in the manual for windows should pretty much work, ie just start up firefox and type in the address of the routers interface and enter details there, hope that helps.

---

### Post by cidica on 2006-06-20
sudo network-admin
if its not installed do a sudo apt-get install network-admin
also gnome-nettool is good for pinging/port scanning/normal network testing. 

Hope this helps!

---

