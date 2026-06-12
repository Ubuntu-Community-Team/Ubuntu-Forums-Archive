---
title: "Upgraded to Edgy - WiFi card out"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by pisapiag on 2006-11-27
I just upgraded to Edgy from Dapper. The "Gestionnaire de périphériques" (peripheral manager?) recognizes the Netgear WG311T wireless NIC and sees it as an AR5212 802.11 abg NIC but the network manager does not and I can't configure it. Everything was working fine under Dapper. What should I do? I'm a total newb with Linux and I don't want to miss Windows. Please help. Thanks.

---

### Post by pisapiag on 2006-11-27
I'm a total newb. I don't know what the hell I did but it now works. Go figure.

---

### Post by kelbizzle on 2006-11-27
I had the same problem you did after upgrading to Edgy. I have the broadcom 43xx after getting the driver installed the network manager didn't work for me either. Instead you can goto System > Administration > Networking.
Disable all the Internet ports except for your wireless card. (I read somewhere they conflict.) Just make separate locations. Once you disable the port except for the wireless card. Goto the properties and specify the ESID that you want to connect to. Type in a password if you have one (mines doesn't) After that you should be able to connect when you click OK and it connects. 

Today I was fooling around with the Network manager and fixed my problem by mistake. I was trying to connect to a network using the wlassistant. In console I seen that it was still using my 192.168.1.100 address from when I was connected at home. So I browsed around and found that in my or /var/lib/dhcp3/dhcpd.leases file everything from home was still connected. 
So I released the lease by 
```
/etc/init.d/networking stop
dhclient -r eth0
/etc/init.d/networking start
```

after removing everything from the Network > Administration > Networking for my wireless lan at home.  I restarted the computer and the Network Manger worked fine like it did before. for the first time ever since edgy was released.

---

### Post by kelbizzle on 2006-11-27
disregard the last post then. Might work for someone else.

---

### Post by pisapiag on 2006-11-28
The Networking section did not even list the wireless card.

---

### Post by kelbizzle on 2006-11-28
Ooo man then you were in much worst shape than I. Anyway you can recall how you fixed it? I find it good to make notes of problems along the way. and the steps you took to fix them. Even troubleshooting steps.

---

