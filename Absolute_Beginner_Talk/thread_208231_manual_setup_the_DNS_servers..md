---
title: "manual setup the DNS servers."
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by apix on 2006-07-03
My dls modem, although it has dhcp, it doent give the dns servers to my pc. So on each boot i have to manually edit the /etc/resolv.conf file to have access to the www. any ideas on how can i have my ubuntu (6.06) get the dns servers automaticaly in each boot ?

Thanks ! :)

---

### Post by HereInOz on 2006-07-03
Go to System > Administration > Networking and select the Ethernet interface.

You can create a staic IP address for your network in Properties of the Ethernet card, then click on the DNS tab and Add the DNS servers for your ISP.  This removes all the dependence of your Ubuntu box on the DHCP of your router.

Just set the IP as a fixed IP address, in the same subnet as the modem/router, set your gateway as the modem/router address, and set the DNS servers to the correct numbers.

If, for instance, you are running a modem/router with an internal IP address of, say, 192.168.1.1, you would set the static IP of the Ubuntu box at something like 192.168.1.6 and the gateway at 192.168.1.1

This will obviously change depending on the settings of your modem/router.

See how you go.

Alan

---

### Post by MaximB on 2006-07-03
and one more thing that happend to me...
after I setup the manually the dns address after 10 minutes it was reset
so I made that file resolv.conf read only.
and my problems solved

---

### Post by apix on 2006-07-03
@HereInOz : My router has dhcp, so i dont need and want to setup a static ip in my computer. the only thing i want, is to have "static" DNS servers. Cant i do that, if i keep the pc on dhcp ?

---

### Post by lamego on 2006-07-03
Edit /etc/dhcp3/dhclient.conf and remove the "domain-name-servers" from the request directive.
Make sure you restart the dhcp service before setting the dns servers.

---

### Post by apix on 2006-07-03
Thanks lamego, that was what i was looking for :)

---

### Post by zool2005 on 2006-07-13
Thanks HereInOz, that seems to have solved my problem. Sometimes my connection is fine and sometimes I have to manually restart it so I won't know if it's worked until I've done a few more reboots.:)

---

### Post by zool2005 on 2006-07-15
I'm replying to my own post after several reboots to say that setting a static IP to my router has solved my DHCP problems and now I can boot without restarting eth0. Thanks:D

---

### Post by kworx on 2007-11-26
for those still interested, in /etc/dhcp3/dhclient.conf find and configure this line

```
prepend domain-name-servers 127.0.0.1;
```

configure 127.0.0.1 to the DNS your router has.
and don't forget to remove the domain-name-servers from the request section.

I know that fixed my problem for the time being.

---

