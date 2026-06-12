---
title: "Changing the computer name &amp; name broadcasting"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by DonQuixote on 2006-01-27
Hey all,  I was wondering

1) how you would go about changing the computer name, should you want to and
2) I have noticed that I can not just type in my computer name from another machine to connect to it over a network.  When I look at my router's IP assignment table I see all the Windows machines' names and IP's, but my Ubuntu box only has the IP address with no name.  I am wondering how I can get the router to recognize my Ubuntu machine's name and to be able to connect to it through the network by entering it's name, and not being required to enter the IP address.

Thanks!

John

---

### Post by BenTyreman on 2006-01-27
```
sudo hostname <new hostname>
```
should change your hostname. You will need to restart immediately after changing it.

I had the same problem with hostnames not being broadcasted. I removed dhcp3-client and replaced it with pump. Works perfectly now.

---

### Post by DonQuixote on 2006-01-28
Ben,

Much thanks!  Works fine now.

John

---

