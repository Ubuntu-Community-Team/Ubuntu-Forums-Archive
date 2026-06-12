---
title: "blacklist driver"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by unisol on 2007-06-09
im told with the wireless card i have, i have to blacklist the driver. can someone explain to me how to go about this? its an rt61 chip, from linksys pci wireless card version 4.01.

---

### Post by supersonicdarky on 2007-06-09
a quick search tuned this up
[quote=http://www.zachberry.net/?p=4]First check to see if you have a wireless card based on the rt61 chipset. Open up a terminal window and type &#8220;lspci | grep &#8220;rt61&#8243;&#8221;, or just type &#8220;lspci&#8221; and check to see if you spot rt61 anywhere in there. If so, type &#8220;**sudo gedit /etc/modprobe.d/blacklist**&#8221; (to edit the blacklist file - A list of kernel modules that will not be included upon boot), and add &#8220;**blacklist rt61**&#8243; somewhere in the file. Now close gedit then (again in the terminal window) type &#8220;**modprobe -r rt61**&#8243; to remove the module from the kernel.[/quote]

---

