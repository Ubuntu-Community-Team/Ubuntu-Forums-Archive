---
title: "Manual Connect to an Open Wireless Network"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by infection0 on 2007-10-28
Hi, I am using Gutsy's Network Manager to connect to wireless networks.

I am trying to use manual mode only - roaming mode isn't an option right now because it keeps undoing monitor mode back to managed mode when I "sudo iwconfig eth1 mode Monitor" on an Intel 3945. This works fine for secured networks. However, on open networks, the "password type" box only allows for WEP or WPA security. There is no "open" option in manual mode. How do I fix this?

By the way, I am using the default Intel 3945 drivers included in Ubuntu and am assuming that they allow monitor mode. If there's something else I need to do to enable Monitor mode without resorting to disabling roaming, I would be glad to hear that too. Thanks for all your help!

--(Total Linux Noob) infection0

---

### Post by infection0 on 2007-10-29
I guess I'll bump it once before I give up? :popcorn:

---

### Post by NoPoChris on 2008-04-09
I have the same question. I'd like to be able to connect to a network at a coffee shop or the airport, but I can't connect to any network without encryption.

---

### Post by swoll1980 on 2008-04-09
I believe you can leave security type empty that is the same as open dont quote me on that though I broke my card a few months ago so I don't remember exactly

---

### Post by NoPoChris on 2008-04-10
I tried leaving the password field blank but that didn't work. I don't have the option to leave the password type blank. I have to choose between WEP (Hex), WEP (ascii), WPA, and WPA2.

---

### Post by Red-Shield on 2008-04-10
sudo iwconfig eth0 essid "any" enc S:what ever the password is 


i think 

and then run sudo dhclient eth0

---

