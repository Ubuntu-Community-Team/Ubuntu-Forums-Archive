---
title: "trouble with wireless network"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by gauche on 2007-12-11
i'm sorry if this is a stupid question but i have a dell laptop with ubuntu and ndiswrapper installed and i can see my wireless network but when i try to connect it asks me for a password. i don't use a password when i connect in windows i have a fixed ip address. but in wireless network properties when i enter my  ip address, default gateway and  dns server nothing happens. i don't understand what i'm doing wrong.

---

### Post by stchman on 2007-12-11
> **gauche said:**
> i'm sorry if this is a stupid question but i have a dell laptop with ubuntu and ndiswrapper installed and i can see my wireless network but when i try to connect it asks me for a password. i don't use a password when i connect in windows i have a fixed ip address. but in wireless network properties when i enter my  ip address, default gateway and  dns server nothing happens. i don't understand what i'm doing wrong.

What kind of wireless card does your laptop have?

---

### Post by gauche on 2007-12-11
it's a 1370 wlan mini-PCI card.

---

### Post by Ansible on 2007-12-11
Are there any other networks around?  My laptop defaults to someone else's network in my building and I have to keep changing it back to mine.  It may be that you are connecting to a network that has WEP security on it... or not.  Worth checking though.

---

### Post by gauche on 2007-12-11
in properties i selected my network from the drop down list then i entered my ip address, default gateway and dns server and nothing happens.

---

### Post by Papa-san on 2007-12-11
There is a really good program called wicd.
A quick google will get you there. It kinda takes the guesswork out of wireless. the other suggestion I have is to look in my signature line under wireless. That how-to did help...

---

### Post by gauche on 2007-12-11
when i get to step 3.3 i see this

lo        no wireless extensions.

eth0      no wireless extensions.



eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

then i couldn't figure out what to do.

---

### Post by wirah on 2007-12-11
Sounds like your wireless network is encrypted but windows saved the key. You'll need to rememebr what your network key is!

---

### Post by PhoenixP3K on 2007-12-11
No, when you are not in roaming mode, the Network Manager will still ask to put a pass-key (WEP or WPA) even if it is an un-secured network. I solved that problem by putting my laptop in roaming mode.

---

### Post by gauche on 2007-12-11
> **wirah said:**
> Sounds like your wireless network is encrypted but windows saved the key. You'll need to rememebr what your network key is!
i don't remember anyone giving me a password. i gave the network administrator my mac address and then he assigned me an ip address.

---

### Post by bobyy on 2007-12-11
Hy...
in terminal tipe this:
> $sudo dhclient eth1

maybee this is the problem..
ignore this post ....i am to tired after night shift so i dont observe you have asighned a staic ...IP
anyway try in command line with:
> $sudo ifconfig eth1 192.xxx.xxx your IP..

---

### Post by Papa-san on 2007-12-12
He will have to give you the key. 
Did you ever look into the 'WICD' GUI? That won't solve this particular problem, but will help at other places you can use wireless. 

The only way I managed to get past the "Access Point: Not Associated" (Even though I had entered the proper WEP ID &key) thing was to disable encryption on my wireless router. Once it made the connection, I was able to turn WEP back on and it has worked smoothly ever since. 

Most routers are not going to be able to recognize an Ubuntu wireless box, and won't let it through for some reason. 
My router sees this:
    * Name: 00:90:4B:2C:52:6B
    * Type: Unknown
    * Status: Online
    * Connection: Wireless
    * IP Address Source: Static IP (though my laptop IS set to DHCP... this is what the _router_ sees.
    * IP Address: 192.168.1.147
    *  
    * UPnP Enabled: No
    * MAC Address: 00:90:4b:2c:52:6b

A windows box looks like this:
# Name: Ashley's
# Type: Computer
# Status: Online
# Connection: Wireless
# IP Address Source: DHCP
# IP Address: 192.168.1.148
#  
# UPnP Enabled: No
# MAC Address: 00:17:3f:4f:ba:2

You will have to talk to the administrator, because, to the best of my knowledge, this is something that cannot be rectified on your system (at least past getting the WEP key entered)... It's a router problem because the router doesn't want to see anything other than windows systems...

---

