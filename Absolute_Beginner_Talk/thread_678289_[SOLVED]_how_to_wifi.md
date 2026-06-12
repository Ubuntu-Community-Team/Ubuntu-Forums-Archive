---
title: "[SOLVED] how to wifi?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-01-25
I recently installed ubuntu on a partitioned section of my hard drive and i cannot connect to wireless networks. I have an internal  realtek RTL8187B wireless usb 2.0 network adapter.
if ii click the network icon i get a choice of wired network or modem 
so i guess my question is what do i need to do to use my home wireless network with ubuntu?

---

### Post by seventhc on 2008-01-25
Do you have either a wireless or network icon showing in the upper right corner?
If so what options to you get if you left click on it.
also open a terminal and run this command.
```
iwconfig
```

---

### Post by tjwoosta on 2008-01-25
I do have a network connection icon but it only says wired or modem

when i tried to run iwconfig this is what happened

tj@tj-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tj@tj-laptop:~$ 

I dont think the os recognized the network adapter, what can i do?

---

### Post by ctswhole on 2008-01-25
More than likely you will have to use the windows driver for you card with ndiswrapper.

---

### Post by NGSG on 2008-01-25
you should see first with lspci whether you see your wireless.
/usr/bin/lspci

grep then for the word wireless.
you should look for something like e.g.:
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection

---

### Post by Presto123 on 2008-01-25
Also, its good to look in System/Restricted Drivers to see if the card is even showing up at all.

For Ndiswrapper, the link is:[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

Click on the "Documents/Wiki" part to read through the info.

---

### Post by seventhc on 2008-01-25
Here are 2 links that might be of some help.

[http://ubuntuforums.org/showthread.php?t=571046](http://ubuntuforums.org/showthread.php?t=571046)

and this one 
[http://ubuntuforums.org/showthread.php?t=630791](http://ubuntuforums.org/showthread.php?t=630791)
The last link contains more links, I wish I could be of more help but never had wireless issues before. Just check out the links in the threads.

---

### Post by tjwoosta on 2008-01-25
yea i tried the lspci thing and i cannot find it this is what i got

tj@tj-laptop:~$ /usr/bin/lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
tj@tj-laptop:~$ 
what should i do?

---

### Post by tjwoosta on 2008-01-25
also i tried the restricted drivers manager but it says my hardware does not require restricted drivers

---

### Post by tjwoosta on 2008-01-25
ok i found the wireless card but it says its usb and it is difinately internal

tj@tj-laptop:~$ lsusb
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
tj@tj-laptop:~$ 

i have read the links that were posted above and it sounds like i am in the same boat as these guys.

---

### Post by tjwoosta on 2008-01-26
also i know my card is an RTL8187b because that it what vista says but when i lsusb it comes up as 8189 what the hell does that mean?

---

