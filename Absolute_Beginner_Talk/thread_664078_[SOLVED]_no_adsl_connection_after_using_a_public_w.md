---
title: "[SOLVED] no adsl connection after using a public wifi connection"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2008-01-10
hello, i was wondering what would be causing my adsl connection to not work after using my local librarys public wifi hotspot. this wifi connection was a managed connection where i had to input my name, internet address, and a password to register on their system. the wifi worked awesome, but when i got home and reconnected the cable coming from my adsl modem back to my machine, the connection was dead. oddly enough, my windows vista os i dual boot with works with the adsl connection fine. i was using ubuntu to log onto the wireless connection. any ideas anyone?

---

### Post by kyphi on 2008-01-10
Recheck your connection configuration.

System, Administration, Network Settings.

Default gateway device should read: eth0

Click on Ethernet connection and then Properties.  Enable this Connection should be ticked and Configuration set to DHCP.  Click OK

Back in the Network Settings screen go to DNS Server and make sure that your ISP's numerical address is there.  Under Search Domains enter the name of your ISP (the part after the @ in your email address).  Click OK and you should be back on line.

---

### Post by thebestofall007 on 2008-01-11
you know what, i just tried checking the dns server addresses against the vista i have installed and it turns out that the wifi hotspot replaced the primary and secondary server addresses (that my adsl service uses)  with 10.10.10.1.  i changed it back to  the 2 addresses and presto, it worked. thanks, now i will know what to do if i use that hotspot again. 

one last thing: why would such a hotspot  change the dns settings to begin with?

---

