---
title: "slow speed in Internet"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Trosky on 2006-05-14
Hello people, I am new with linux... I have a slow speed of Internet with linux, it's aproximately 1/3 of the speed with windows. My machine is an acer laptop with an external wireless card (Belkin Wireless G Notebook card), I configured it using the ndiswrapper because no drivers for linux, and I used the driver of "Belkin Wireless G Notebook adaptor" from the wiki page of ndiswrapper.
The load of firefox is slow, it's about 30/40 second to start and get the google webpage, 30 seconds for access yahoo.com and so on.
What can I do for fixing?

Thanks
Trosky

---

### Post by andrewlubinus89 on 2006-05-14
Try turning off ipv6. I think I had a similar problem when I first installed ubuntu. Type "about:config" into your address bar in firefox and search for "ipv6" or something like that and it should bring up network.dns.disableipv6 and change it to false and see if that helps. Search for "ubuntu" and "ipv6" on google for more information.

---

### Post by Trosky on 2006-05-15
thank you very much, you are a genious!!!!!, it was exactly that althought the defect value was false, just change to true and it&#347; now flying :D

---

