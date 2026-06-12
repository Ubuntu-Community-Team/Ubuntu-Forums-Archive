---
title: "[SOLVED] how to share my pppoe (ADSL)?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by tobeme2 on 2007-10-02
I surf on net  by pppoe adsl .
Now I have 2 computers. 
How could I make both pc connected to the internet ?
I make through under Window, but how could I do this under Ubuntu ?
Thanks!

PS:
PC1 (Host)  has 2 Network-Cards, with 2 OS (Windows XP pro sp2  and ubuntu feisty 7.04)
PC2 (Guest)  has one Network-Card with OS Windows XP pro sp2.

---

### Post by skymera on 2007-10-02
you can get firestarter from repos
and in settings is a litle tab that allows you to share connection.

although thats all i know. im not sureabout the DHCP or anything, hope i helped a bit

---

### Post by tobeme2 on 2007-10-02
> **skymera said:**
> you can get firestarter from repos
and in settings is a litle tab that allows you to share connection.

although thats all i know. im not sureabout the DHCP or anything, hope i helped a bit
Thanks !
I'll try.

---

### Post by djchandler on 2007-10-02
> **tobeme2 said:**
> I surf on net  by pppoe adsl .
Now I have 2 computers. 
How could I make both pc connected to the internet ?
I make through under Window, but how could I do this under Ubuntu ?
Thanks!

PS:
PC1 (Host)  has 2 Network-Cards, with 2 OS (Windows XP pro sp2  and ubuntu feisty 7.04)
PC2 (Guest)  has one Network-Card with OS Windows XP pro sp2.

Make it easy on yourself and get a router. You will need a hub or switch built in to it, usually giving you 4 ports. The router can handle the DHCP, besides providing greater security with its NAT firewall built-in, plus other security features.

If you go with the previous answer where you must  configure your Ubuntu firewall with Firestarter, you will also need to configure a DHCP server in your Ubuntu OS.

Why did you put a second NIC in the host box? No hub or switch is my guess. Is the guest a laptop? For a few dollars more you could have saved yourself a lot of trouble IMO.
:confused:
DJ

---

### Post by tobeme2 on 2007-10-04
Thank you for your kindness ,skymera  & djchandler  .
Now I get through by  firestarter!
steps:
sudo apt-get install  firestarter
sudo  firestarter

then a graphic interface appears and set network  by instruction.

---

