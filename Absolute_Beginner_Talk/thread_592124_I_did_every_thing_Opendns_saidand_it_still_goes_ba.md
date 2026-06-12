---
title: "I did every thing Opendns saidand it still goes back"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by nu2this on 2007-10-26
I'm using Gutsy I went through  the opendns  instuctions & I got this:
```
 robbie@robbie-EMMA:~$ sudo network-admin
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
sudo gedit /etc/dhcp3/dhclient.conf
robbie@robbie-EMMA:~$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
robbie@robbie-EMMA:~$ sudo gedit /etc/dhcp3/dhclient.conf
robbie@robbie-EMMA:~$ sudo ifdown eth0 && sudo ifup eth0
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
 
```
Then at the next reboot the network goes to the ISPs IP instead of Opendns.
Does anybody here Know what is wrong here:confused:
I have disabled IPv6.

---

### Post by stimpack on 2007-10-26
I think network-manager handles these things now and will overwrite manually changed settings. If you enter the DNS servers from the network applet in the systray it should work. (did for me in kubuntu)

edit: from your text above it seems like eth0 is not your interface either. Try 'ifconfig' to see which interface you are using.

---

### Post by stfury on 2007-10-26
i have exactly the same problem man and i got no idea how to get it working.

please help us guys

---

### Post by stfury on 2007-10-26
hi there, i had same problem (this will only work if u are accessing the internet through a router?

go to ur routers ip and it will open up the settings interface.
go to advanced then Dynamic DNS Client,

add in the OpenDNS dns's then click on the userconfigured option.

it wil now work :D gutsy constantly updates from the default dns on the router.

cheers,
stfury

---

### Post by nu2this on 2007-10-26
I did the systray icon reboot right back.
I did ifconfig & got this:

robbie@robbie-EMMA:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:24:C3:64  
          inet addr:74.136.25.52  Bcast:74.136.31.255  Mask:255.255.224.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1481790 (1.4 MB)  TX bytes:76865 (75.0 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Does anyone know what I need to do now?

---

### Post by nu2this on 2007-10-27
Personal bump

---

