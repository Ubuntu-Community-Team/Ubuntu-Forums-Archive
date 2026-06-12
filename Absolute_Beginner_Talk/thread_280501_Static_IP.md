---
title: "Static IP"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-19
How do I set up a static IP address on my ubuntu box. Ive just started using VNC between my macbook and linux box.

---

### Post by bigken on 2006-10-19
system/administration networking click on your lan card ;)

---

### Post by bulldog on 2006-10-19
Go to administration-->network and choose your adapter.

Properties-->static IP and fill in the blanks.

That should do it.

---

### Post by sdubois92 on 2006-10-19
a little problem, I go to [www.whatismyip.com](www.whatismyip.com) and i copy the address down, set up a static ip connection and put down the IP address. It automatially puts in the subnet address and the gateway is blank. I click okay and now I cant get on the internet. any help?

---

### Post by CatKiller on 2006-10-19
If you need to go to a place on the Internet to find out your IP address, then you're unlikely to want to set a static IP address in Ubuntu. Either you get assigned an IP address by your ISP when you connect, in which case you want to keep it on DHCP, or you've paid extra for a fixed IP address or two, in which case you'd know what it was from the people that you bought it off.

There is such a thing as Dynamic DNS if you want to be able to find your computer across the Internet, but I don't know much about it or how it works.

---

