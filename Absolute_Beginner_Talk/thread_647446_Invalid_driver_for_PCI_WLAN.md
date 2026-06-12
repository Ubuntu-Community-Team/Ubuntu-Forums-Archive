---
title: "Invalid driver for PCI WLAN"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Killy1 on 2007-12-22
I'm having problems installing the driver for my PCI wlan, I have a marvell 88W8335 - Libertas 802.11b/g. After searching, found it should work (ndiswrapper listings)  with the win-Xp driver .inf file. 

After installing ndiswrapper, I am unable to get the driver to work (following instructions in Beginning Ubuntu - Keir Thomas). When I use the:

sudo ndiswrapper -i......inf

I get a message saying no such file or directory. Then after:

sudo ndiswrapper -l

I get the inf file name and invalid files.

Does anyone have any suggestions?

---

### Post by Abu_Dayya on 2007-12-22
Why do't you use the graphical interface of ndiswrapper? Copy the .inf file from the CD you got with the adapter and paste it on your home folder or desktop. Then Load them with ndiswrapper

---

### Post by Killy1 on 2007-12-22
May sound stupid, but how do I access the graphical interface of ndiswrapper?

---

### Post by Abu_Dayya on 2007-12-22
System &#8594; Administration &#8594; Windows Wireless Drivers
Then select 'Install new driver'
Then Choose the location of your .inf file, and click install

---

