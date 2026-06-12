---
title: "DWL-G122 With Network manager"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by naza on 2007-08-26
I am kinda new to ubuntu and linux so i am sorry if this is a basic question but, i brought a D-Link DWL-G122 so that i could get a better reception for my pc, as it is USB so i can move it around easyily. I plug it in a it works. The Drivers and everything are find. i type in sudo iwconfig wlan0 up, and it goes up. But the problem is that i use the network manager GNOME app and that does not seem to pick it up. I have another wireless in my PC, BT voyager 1040 PCI card which hase the broadcom 4306 chipset and uses the BCM43xx driver. That works fine with it. The only difference is that the BT voyager was in the PC when i installed ubuntu and the D-link was not, and i have just added it. So how do i make the network manager list my D-link as well. The D-link DWL-G122 uses the RT73 chipset. I know that the network manager can do this as when i changed to manual configuration and then back it picked up both of them, but now i try it and it does not.

---

### Post by peebly on 2007-08-26
Hello

If I was you I would stick with The BT voyager adapter.

I have a DLINK DWL-G122 and have had lots of problems with it cutting out when visiting certain websites like youtube or the register causing me to have to unplug the adapter switch off computer and reboot.

Haven't had any problems at all with the BT voyager card.

---

### Post by Austin_KW on 2007-08-26
Which driver are you using with the rt73. The drivers supplied with feisty do not work.

You need to install the legacy drivers from serialmonkey.com. But the legacy drivers are not supported by the network manager and need to be configured manually or through the the /etc/network/interfaces file. See this howto, [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236).

Gutsy (still in alpha test) will support the rt73 using the newer beta drivers with network-manager, but it is a major hack to get these working on feisty; You would need to install the gutsy kernel and drivers. I recommend the legacy drivers, use the above link

---

