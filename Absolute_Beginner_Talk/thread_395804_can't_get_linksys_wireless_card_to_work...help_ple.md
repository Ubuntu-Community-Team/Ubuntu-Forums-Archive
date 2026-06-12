---
title: "can't get linksys wireless card to work...help please!!"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Sigitas on 2007-03-28
I am a complete Ubuntu beginner (I've had Ubuntu Edgy for about a week now).  I've been having some trouble getting my Linksys WMP55AG wireless card to connect to the internet.  Is there anyway to make this card play nicely with the rest of my computer?  Any help would be greatly appreciated.

PS: I'm pretty sure the OS recognizes the card because when I type in "lspci" in the terminal, a bunch of text pops up, and at the end it reads "Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)....come to think of it, this may be a firmware issue...anyways, I would appreciate it if someone helped me out ASAP because I cant live without my internet :)

---

### Post by chili555 on 2007-03-28
Please install linux-restricted-modules and then your card should be recognized. If you can get the computer to an ethernet connection, you can:```
sudo apt-get install linux-restricted-modules
``` Apt-get will sort out the details and dependencies. If no way to get an internet connection, you can download to the computer you posted from, copy the file to a CD or USB drive and move back to Ubuntu. Match the file you download to your running kernel:```
uname -r
```Here is where you can search: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) If in doubt, download and transfer all the items that are dependecies (red dot).

---

