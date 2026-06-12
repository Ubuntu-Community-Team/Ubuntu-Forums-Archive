---
title: "Beginners Question"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by roxja on 2006-08-30
Hey guys,
Just after installing ubuntu and after getting through my first struggles with wifi I am now getting a 95% signal but can't get online, firefox is insisting that any web site I want to go to does not exist. Any ideas?

---

### Post by John.Michael.Kane on 2006-08-30
It might help if those who read this wanting to help you knew what your wifi hardware is.

---

### Post by roxja on 2006-08-30
Ubunto 5.10 and the wifi card is an Intel PRO/Wireless 2200 BG. Everything seems to be working fine, its connecting to the router no problem and I can't do anything.

---

### Post by IYY on 2006-08-30
Try,

system > preferences > networking

and select your wireless card as the default gateway.

---

### Post by roxja on 2006-08-30
Thanks I think your on the right track there, but I can't see an option to make my card the default gateway.

---

### Post by John.Michael.Kane on 2006-08-30
There should be an option to enter your gateway address under connection settings.

---

### Post by roxja on 2006-08-30
There is but I can't select it if I have DHCP turned on.

---

### Post by roxja on 2006-08-30
Ok spotted the place to select eth1 as my default gateway, eth1 is my wireless card, no difference.

---

### Post by doogy2004 on 2006-08-30
Under system > preferences > networking

select your wireless card, it should be eth1
eth0 is typically your Wired LAN connection

once you have the right adaptor selected it should allow you to connect to the internet

---

### Post by doogy2004 on 2006-08-30
Try deactivating and reactivating eth1

---

### Post by roxja on 2006-08-30
No joy, I am now confused. iwconfig reveals that eth1 is sure to be sure my wireless card.

---

### Post by furiousV on 2006-08-30
Is it just firefox that won't connect to any websites?

Can you ping google.com from the command line?

---

