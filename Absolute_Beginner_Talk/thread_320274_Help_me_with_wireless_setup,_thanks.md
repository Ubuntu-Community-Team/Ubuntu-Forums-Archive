---
title: "Help me with wireless setup, thanks"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by geezas on 2006-12-17
Hey, everybody, it's me again...
I have dapper drake.
I am using the internet through a cable from my router now (eth0)...
Didn't need to configure anything, it worked after installing ubuntu.

However, I also have a wireless option, since my router is wireless, and there's a wireless network card in the computer.
System > Administration > Networking
I activated the wlan0 and entered the WEP key but I can only get internet to work through the cable...

Tell me what to do, check, change...

---

### Post by geezas on 2006-12-17
Where do I find info about for example my wireless card?  name, model of it...?

---

### Post by pebo on 2006-12-17
sudo lspci | grep Network

---

### Post by geezas on 2006-12-17
```
geezas@ANTRAS:~$ sudo lspci | grep Network
Password:
0000:02:01.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

---

### Post by pebo on 2006-12-17
Have you disabled eth0 in Network Tools?

---

### Post by geezas on 2006-12-17
when I disable it, then the internet doesnt work...

activating wlan0 doesnt work :(

---

### Post by pebo on 2006-12-17
Have you added DNS servers?

---

### Post by geezas on 2006-12-17
No I did not....
Can you explain to me what they are and they do... ;]

---

### Post by pebo on 2006-12-17
Don't ask me for a technical explanation :-? , but they translate IP addresses into hostnames / domains. You should be able to read them off your router WAN status data.

---

### Post by geezas on 2006-12-17
Primary DNS Address  	0.0.0.0
Secondary DNS Address 	0.0.0.0     (optional)
MTU                  1500

---

### Post by geezas on 2006-12-17
there is 192.168.0.1 already in DNS tab


....found some more numbers in router settings
* WAN*
MAC Address 	00-0F-3D-3B-43-41
Connection 	DHCP Client Connected  
IP Address 	24.12.145.8
Subnet Mask 	255.255.240.0
Default Gateway 	24.12.144.1
DNS 	68.87.72.130 68.87.77.130

---

### Post by pebo on 2006-12-17
hmm...something doesn't look right there...when you connect with cable what DNS servers do you get?

---

### Post by geezas on 2006-12-17
well....  I am connected with cable now... but I have wlan0 activated too...  if I deactivate cable, internet is gone...   
wait, i will deactive eth0 and see if anything changes with dns numbers...

---

### Post by pebo on 2006-12-17
> **geezas said:**
> there is 192.168.0.1 already in DNS tab


....found some more numbers in router settings
* WAN*
MAC Address 	00-0F-3D-3B-43-41
Connection 	DHCP Client Connected  
IP Address 	24.12.145.8
Subnet Mask 	255.255.240.0
Default Gateway 	24.12.144.1
DNS 	68.87.72.130 68.87.77.130

Sorry didn't read the last bit...try adding the DNS settings to 'DNS servers' in your wireless configuration

---

### Post by geezas on 2006-12-17
I tried adding 2 dns entries: 68.87.72.130 and 68.87.77.130, but same thing,,.,

---

### Post by pebo on 2006-12-17
:confused: Sorry - time to let someone more knowledgeable step in

---

### Post by geezas on 2006-12-17
thanks for trying ;]

---

### Post by mosedavid on 2006-12-17
hi,

i'm very new to linux and ubuntu but have you checked your wireless hub?  My wireless didn't work until i went into the hubs settings - in my case using my Ethernet plugged into the back of the hub.  I checked WEP (apparently WAp is tricky in ubuntu), made sure the WEP key was correct.  The hub was working with a fixed ip address with the modem router sending DHCP through the wireless to the laptop.  The IP and subnet range was the same.

It then still didn't connect so i put in a fixed ip address and subnet mask - same range as the rest.  It showed as connected but still couldn't get on the internet.  Changed it back to DHCP, checked the network key again using : **sudo etc/network/interfaces** and the darn thing started working.

my wireless card was a ralink ra2500 - lots of post here about those!

probably wont be any help but its worth looking outside ubuntu for the problem - router, wireless hub etc.

---

### Post by technomonkey on 2006-12-17
Hi all,
I am having a Wi-Fi problem and would really appreciate some help!
I am using a Belkin USB Wi-Fi dongle and have used "lsusb" and it has been recognised;
"Bus 003 Device 002: ID 050d:705a Belkin Components"

But in Network Settings, only Ethernet and Modem connections are show, I don't get the option of Wireless.......

Any Ideas?

---

### Post by geezas on 2006-12-17
So many problems, so little answers...

---

### Post by technomonkey on 2006-12-17
Hi All,

I have found a solution that solved my problems - the guide below allowed me to set up Wi-Fi in about 15 mins!!!!!!!!!!!

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux) 

Michael

---

