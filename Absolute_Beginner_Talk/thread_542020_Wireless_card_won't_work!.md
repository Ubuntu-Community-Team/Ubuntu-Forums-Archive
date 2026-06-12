---
title: "Wireless card won't work!"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-09-03
Hi, I added a Dynex wireless card to my computer (Model DX-WGDTC).  I had done some research on it and it was supposed to be supported out of the box.  While Fiesty seems to recognize the card it doesn't seem to be able to use it for some reason.  Does anyone know how I could fix this?

What makes this problem even harder to take care of is that I just moved to a new apartment where I have wireless internet access but no ethernet line available (which is why I got the wireless card) so if I have to access the internet I have to do it from my XP partition, and it's a real pain to keep switching back and forth between the two (to make matters worse, ever since I installed the wireless card XP keeps freezing up randomly, up to five times a day!).

Thanks

---

### Post by Mud.Knee.Havoc on 2007-09-03
Shouldn't somebody with 156 posts (ie. you've been here a long time) know better than posting multiple identical messages in the forum?

---

### Post by Nythain on 2007-09-03
guess we could start with the results of
sudo lspci
sudo ifconfig
sudo iwconfig
the contents of
/etc/network/interfaces
possibly the results of
sudo iwlist <device name, eg eth0, ra0, etc> scan
(i hope thats the right command to scan for wireless ssid's detected by a certain device)

anyone else with anything else thats needed to trouble shoot this one???

Edit: Oh yeah, possibly the Make and Model of the wireless router trying to connect to if known???

---

### Post by mlentink on 2007-09-03
In addition to the above, you might also want to check on the encryption method of the wireless network you want to connect to. WEP? WPA? 
You say Ubuntu recognizes the card. How have you established this? Did you see any wireless networks in nm-applet? (networkmanager)

---

