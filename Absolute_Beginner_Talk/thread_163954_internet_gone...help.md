---
title: "internet gone...help"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-21
i just replaced my old 'b' router with a netgear 54g router. I set all up in windows first and configured WPA security, and changed the name, (from NETGEAR default to a made up one) and I was online and good in windows. I rebooted into linux and was online sporatically, with a very weak signal. I ran iwconig and got this:

ryan@ubuntu:~$ iwconfig
lo no wireless extensions.

eth1 no wireless extensions.

eth0 IEEE 802.11g ESSID:"BCNETGEAR"
Mode:Managed Frequency:2.462 GHz Access Point: 00:14:6C:01:23:5E
Bit Rate=1 Mb/s Tx-Power=20 dBm
Retry limit:7 RTS thrRed Faceff Fragment thrRed Faceff
Power ManagementRed Faceff
Link Quality=35/100 Signal level=-79 dBm Noise level=-78 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:54 Invalid misc:0 Missed beacon:21

sit0 no wireless extensions.

ryan@ubuntu:~$
Now on eth0, the ssid is bcnetgear, that is NOT mine tha I created, i think its a neighbors, I saw it in the windows 'view all available wireless networks' list. How can i get to a similar list in linux? is there one? So I can set up my network for default and enter my WPA key if I need to, ( I entered my MAC address while setting up the router as the only allowed one) Please help me what to do next, thank you.

---

### Post by x5452 on 2006-04-22
help please, i followed this how to:

[http://doc.gwos.org/index.php/Ipw2200_wpa](http://doc.gwos.org/index.php/Ipw2200_wpa)

and nothing, I have no idea what Im doing anymore, about to say screw it and give up

---

### Post by x5452 on 2006-04-22
ok now, i tried this how to:
[http://www.ubuntuforums.org/showthread.php?t=90450&highlight=keys+configured](http://www.ubuntuforums.org/showthread.php?t=90450&highlight=keys+configured)
I am now online, but signal strength is like 80-90% not 99-100 and im ritght next to the router.  How do I KNOW what wireless I am on? I ran /sbin/iwlist scan and it lists a couple and says a  couple do not support scanning, eth0, (which is what my wireless is called) reports a hidden ESSID, ( I have the router set to not broadcast the ssid) but how do I KNOW what connection I am on??

Edit:  It SAYS I am connected, but I cant access any web sites, F it, i give up

---

