---
title: "TCP/IP Stack"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Linux_n00b on 2007-05-05
I was currently working in ubuntu (Feisty Fawn) and I tried to install a CISCO VPN program.  During the installation it said it may not work properly if I do not install the TCP/IP Stack for Microsoft.  I don't know why, but I selected "YES" to install it.  I tried opening the VPN software and it would not open properly.  Since VPN would not work, I just used the WINE UNINSTALLER to uninstall it.  Also, now my NetGear WG511T wireless network card will not connect to any wireless networks in UBUNTU.  How would I go about fixing this?  Help would be greatly appreciated..

---

### Post by tophatandy on 2007-05-05
dont use the cisco vpn.. 
try something like hamachi..

your not going to be able to install the program onto wine as it does not create a virtual machine to run specific protocols or anything like that. It is merely an emulator that makes refrences to linux's tcp/ip protocol stack..

try hamachi.. its always worked fine with me..

next.. do you have the network manager show up?

go to the network settings panel in the administration menu,
then try enabling the wirless card (or disabling then enabling it if it is already enabled)

try loging out and loging back in.

---

### Post by rbalfour on 2007-05-05
If you need to connect to a Cisco VPN system, You have to install the Linux Version, you can get it from Cisco.
Hamachi is okay. But OpenVPN is better. There is a Windows client too.

---

### Post by Linux_n00b on 2007-05-06
I tried logging out and logging back in and that did not fix anything.  I think it messed me up completely because I installed that TCP/IP stack for microsoft in linux and that is why my wireless card is not working.  Rebooting, logging out and logging back in, disabling and re-enabling the wireless card did not fix it.  Any other ideas of which I can try to get this thing working? Would I have to reinstall UBUNTU?

---

