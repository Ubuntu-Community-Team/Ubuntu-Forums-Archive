---
title: "How to set up a print server?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-04-30
I installed the CUPS print server as directed in the Ubuntu 6.06 server documentation, but nothing else was explained.


I wan't to be able to print from various windows XP computers and OSX computers through the network to a usb printer connected to the Ubuntu server.

How do I do this?


How do you set up a printer on Ubuntu server?


Thank you so much if you can help!!

---

### Post by Seisen on 2007-04-30
To print from Windows your going to have to setup samba and you need to have the drivers for your printer installed on Linux, Windows, and Mac. Also you can remotely access CUPS remotely by putting the IP address of your cups server and adding this ":631" after that. For example to access mine from Windows I put in 192.168.1.11:631 in the browser.

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")

If you have any other questions, feel free to PM.

---

