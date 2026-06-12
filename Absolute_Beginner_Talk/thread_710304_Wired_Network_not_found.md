---
title: "Wired Network not found"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by LargeMike on 2008-02-28
When I first installed Ubuntu, the wired network connection worked just fine. Since editing GRUB to increase the time the menu stays on screen and make windows the default OS, I no longer have any internet connection.  

I am not using any other systems on the network. The network cable connects directly to the Cable Modem without a router.   The system dual boots to Windows and the internet connection works fine in Windows, but in Ubuntu, I can not get any connection.

I am using roaming mode, but have tried using manual connection and setting the IP address, gateway and subnet mask to the same settings that I have in Windows.  No result in either. In some of the earlier posts, it was suggested to try sudo ipconfig eth0 down and then sudo ipconfig eth0 up, then log off and log back on. No Dice. I also tried pppoe config in the terminal.  I received a message that it was not installed, and when I tried to install, it failed because the internet site could not resolve.  I can not ping anything except the loopback address.

results of ifconfig eth0 are attached

I'm really feeling stuck :confused: and would appreciate any suggestions.

---

### Post by stoneybroke on 2008-02-28
Hi Sometimes I find that my network will not work all I do is click on the Wired Network Connector at the top right of your screen, stop the network then start it again and it usually re-boots and starts again so have you tried that?

---

### Post by sayakb on 2008-02-28
@OP

Have you installed any firewall like firestarter?

---

