---
title: "Xubuntu won't connect to 2Wire router"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by sang froid on 2008-01-18
I installed Xubuntu recently onto a desktop computer (not a dual boot, though) and it refuses to connect to the internet. I have a 2Wire 2700HG-B router hooked via an ethernet cord that works fine with my laptop running Windows.

So far I have:

Tried accessing the router's IP address (192.168.1.254 and gateway.2wire.net) in firefox to change the settings.

Manually added the DNS server (192.168.1.254) and the Search Domain (gateway.2wire.net) in Network Settings, and changed the eth0 connection setting to DHCP. This made the no connection image disappear in the top left corner of the screen, but I still can't get to the settings page in firefox.

Used PPPoE, both the Roaring Penguin one and the Ubuntu package one. Roaring Penguin failed to configure and pppeoconf reported that "the access concentrator of your provider did not respond"

If anyone could help me out it would be greatly appreciated. ](*,)

---

### Post by mikeyphi on 2008-01-19
Don't quite understand the problem....

If you can get the Router setup correctly there should be no need to make any changes to Firefox - it should connect automatically to your 'always on' Internet connection (unless you have previously made changes in the Firefox Preferences/Advanced/Network settings)

If its the Router you need to setup - the settings to be entered under 'Network/Wired connection' are the same as in Windows.

Enter DHCP - in the Wired connection/Properties tab
Enter the Gateway address (in DNS Server box under Network settings/DNS)
 - but it sounds as though you've got this part done!!

---

### Post by zipperback on 2008-01-19
I have a 2wire router as well.

All you need to do is set your network card (eth0) to do a standard DHCP ip address request.

If you changed the dhcp ip address block allocations in the router portal configuration then you should change it back to the default settings. Reboot your router and your comptuer and you should be back online.

> 
Used PPPoE, both the Roaring Penguin one and the Ubuntu package one. Roaring Penguin failed to configure and pppeoconf reported that "the access concentrator of your provider did not respond"


You do NOT need to add any third party packages. If your network card is working out of the box and you are using the 2wire router with the default dhcp ip block settings then your system should just work.

- zipperback
:popcorn:

---

### Post by sang froid on 2008-01-20
Problem sovled...I just messed with the router until the Ethernet LED turned on... Thanks for your time.

---

