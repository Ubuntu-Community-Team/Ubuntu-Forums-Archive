---
title: "Network card installation/static IP problems"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by remainder on 2007-07-29
Hi,

   I've got two questions, one very simple and one more along the lines of what you are probably used to. 1) How do I know whether my network card is working properly in Ubuntu? I followed all the directions [here]("https://help.ubuntu.com/community/ADSLPPPoE"), and I can certainly surf the internet without problems when I've configured my connection to DHCP. It's just that, sometimes when I've set it to statc IP, I can't connect to anything on the internet. I had it working with a static IP this morning, then changed the IP to something else and then back to what it was originally and can't get static IP to work again. So, 2) Is there an explanation for this? I'm trying to get a router set up here at home, and the manufacurer says  Linux users should use a static IP.

Thanks,
Danny

---

### Post by moffa on 2007-07-29
If you have it setup with a static ip address you probably forgot to add DNS hosts. If you go to System > Administation > Network and add the DNS servers to you DNS tab you should be okay.

I have many computers running off of a wide variety of routers and I have never _had_ to use a static ip address.

---

### Post by remainder on 2007-07-30
Thanks for your reply. How do I know the IP address of my DNS server? Right now, the DNS tab has two entries, and both are 192.168.0.1. That seems a little odd to me, but my computer does seem to be able to contact a DNS server when I go online (again mainly with "DHCP" and not "static IP").

And, Moffa, have you ever used a D-link router without static IP? That's the brand of router I'm trying to get set up right now.

---

### Post by moffa on 2007-08-07
sorry for the late reply,

the ip address of your dns server will probably be your router (ie 192.168.0.1).  I've used a Dlink router without a static ip and it worked fine.  To get it working with a static ip, I had to setup the dns server in the /etc/network/interfaces I think.

---

