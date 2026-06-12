---
title: "No wireless connection with WEP"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Frenske on 2008-02-20
The story so far! After our wireless network was violated we decided to protect it with a password. I set up the WPA encryption with password (catchphrase) on the Belkin G Plus Nimo Router. Everything was working fine.
Unfortunately one of my flatmates has a 8 year computer which does not do WPA encrypting and therefore he changed the encryption to WEP and obtained an 46 digit Hexadecimal code and gave it to everybody. Everybody is happy except me!
When I want to connect to the router with my Belkin FD7050 v3, I am not being asked for the new network key!!!! After a couple of seconds it starts to connect with a different network (with bad connection).
I tried the manual configuration: selecting the network, WEP hexadecimal encryption, typed the in password, tried the IP4all, DHCP setting, but nothing works.

This problem is not restricted to Ubuntu 7.10 but I can't connect to our own network in Windows XP.

---

### Post by anewguy on 2008-02-20
I assume you do realize that wep (or wpa for that matter) can be cracked - in the matter of wep it can be cracked quickly.

Does your router support MAC filtering?  If so, perhaps you want to setup the valid addresses for the machines that are allowed to connect, then remove wep/wpa all together.  Be sure you use something other than the default maintenance password on your router.

---

### Post by Frenske on 2008-02-20
I know it is not the safest way, but it is better than what we had before. I live in a place where there are a lot of people are living - a bit like a large student house but then with working peeps. It is more convenient to have a password everybody knows in the house.

Anyway the odd thing is that the Belkin F5D7050 adapter worked fine with WPA with ascii network key, but after changing it WEP with hexadecimal key it does not work any more? 
Perhaps the key can not be overwritten?

---

### Post by Frenske on 2008-02-20
Problem solved! I just needed to make a new network with the same name as the old one and select the appropiate encryption. Not nice that changes are not transposed in the network connections utility. Oh well, the same problems existed with Windows Zero Connection utility.

---

### Post by dca on 2008-02-20
...don't quote me but it sounds like if that roaming mode is enabled dealie in the network settings forces you to have to do this...

---

