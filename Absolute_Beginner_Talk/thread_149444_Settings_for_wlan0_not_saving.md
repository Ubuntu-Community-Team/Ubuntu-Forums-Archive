---
title: "Settings for wlan0 not saving"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by conbrio on 2006-03-23
Hello all,

Need some help to get over a hump. Everytime I reboot I have to enter the info to connect to my router (ssid and wep key) and I also have a second location in my network settings and for that one too I have to enter the ssid (this is a school network).  I have tried to use the save current setup on logout but it didnt do anything. What am I missing or not doing to get the settings saved so I do not have to enter them again at every login when I want to connect wirelessly to my router or the school network. Thanks

ConBrio

---

### Post by Tobitas on 2006-03-24
Hi, I am new to ubuntu to, so hopefully my answer is of any use. I had similar problem, and solved them by editing /etc/network/interfaces.
so, if you type for example 
```
sudo nano /etc/network/interfaces
```
and then add something similar like this:
```
# The primary network interface
#iface eth0 inet dhcp
iface wlan0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1
wireless-mode managed
wireless-encryption on
wireless-essid 491730xxxx
wireless-key open 4279954745055542xxxxxxxxxxxxx

auto wlan0
```

what exactly you have to put in obviously depends on your router and IP settings.
hope this helps
Tobias

---

### Post by sailor2001 on 2006-03-24
had the same problem..The wikis and ppl always say "save and exit" but never explained how to  do that....After I config ndiswrapper in the treminal, I hit the cn























































I had the same problem.....The wiki's and ppl on the forum always say "save and exit" after setting up a pprogram, but never bothered to explain how to "save"  I hit the ctrl + o key after setting up the wireless and it seems to work......have no idea if that is right or wrong

---

