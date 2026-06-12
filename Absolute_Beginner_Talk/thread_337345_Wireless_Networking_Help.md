---
title: "Wireless Networking Help"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by kungfuscout on 2007-01-12
Hello,

I am a complete n00b to Linux, and I have a dual boot with Ubuntu 6.10 and Windows XP Home installed on my laptop. My system is a Dell Inspiron 2200 with an internal wireless networking card. I am extremely happy with Ubuntu, except that I can not get my wireless connection to work.  I have spent the last few days trying to get this to work, and I am now completely out of ideas. Here are the steps I took:



I browsed my Windows partition and recovered the two drivers I needed.

I installed 'ndiswrapper' and 'ndisgtk'.

I used 'ndisgtk' to configure ndiswrapper for my drivers.

I used the terminal to run 'ndiswrapper -l' and it told me that my driver was installed and the hardware was present.

I installed 'Network Manager' and 'Wifi-radar'

I disconnected my wired internet and tried to connect to my wireless network (unencrypted, name: linksys).



Neither of the fore mentioned programs did anything to help whatsoever. I tried experimenting with different settings and everything I could think of; nothing worked. Could anybody please help? Thanks in advance.

---

### Post by Modernity on 2007-01-12
Do you have a button or switch you can turn off the WLAN? or is it machine controlled?

---

### Post by jas0 on 2007-01-12
The Intel 3945 chipset (which I believe you have) is getting mixed results in Ubuntu. Have you tried network-manager-gnome?

---

### Post by kungfuscout on 2007-01-12
Okay, First:

My keyboard has a function key which allows me to access certain functions, network connectivity among them. Most, like Stand By, Volume, Eject CD Tray, and Power work on both XP and Ubuntu. However, the button controlling my wireless card seems to have no effect. I just tried using it and it makes no difference.



Second:

Yes, I have tried Network Manager, and am using it right now.  It works well with my wired connection, but doesn't get me any closer to wireless, unfortunately...

---

### Post by misha680 on 2007-01-13
One thing you might try is editing your network interfaces file if you have not already done that so that network manager is able to handle your wireless interface properly. To do this press Alt-F2 to run a command, and then type in the following command:

```
gksu gedit /etc/network/interfaces
```

Then, make sure that the only thing there is:

```
auto lo
iface lo inet loopback

```

This way, network manager will control everything else. If you do not feel comfortable deleting other lines, you can make them into comments by prefacing them with # (the pound character). I hope this helps. 

Also, I think if you are really using Intel Pro/Wireless 34xx wireless card I am pretty sure the kernel has a generic driver for it as I just installed Ubuntu on a friends Inspiron XPS something or other and network manager seemed to work with ipw394x driver (sorry if I keep confusing the digits here), so if you have that card I am not sure you need ndiswrapper. But either way it should work.

---

### Post by kungfuscout on 2007-01-13
Thanks for the tip, but it still is not helping. ](*,) 

You know, I am starting to get a crazy idea that Dell doesn't like Ubuntu.

---

