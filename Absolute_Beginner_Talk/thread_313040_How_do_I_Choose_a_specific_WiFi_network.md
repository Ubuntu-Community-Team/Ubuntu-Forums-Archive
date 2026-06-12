---
title: "How do I Choose a specific WiFi network?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by lkvee on 2006-12-05
I installed Ubuntu 6.06 and fully updated Synaptic, so I'm running the newer kernel now.  I did so after installing Windows XP on my Sony Vaio VGN-FS645P/H.   Ubuntu not only detected the wired and wireless Ethernet, it also configured and activated both.

At one university, there are two wireless networks - one for students/faculty/staff, and the other for guests.  In Windows, I can choose which wireless network to use.   Ubuntu as it is, seems to be choosing the students/faculty/staff network by default.  I want to choose the guest network instead.

I'd love to hear any thoughts/input/feedback.   Thanks for reading.

---

### Post by zvezdogled on 2006-12-05
Hi,

I am no expert, but i think it goes something like this;
write in terminal:
sudo iwconfig device essid "guest"

wher device is your wireless device name and you shoul change it with something like that: eth2, eth1, eth0;)
and guest is the essid name you want to log on to.
if you want to know which networks you can log on to then use these command:
iwlist scan

and something like this should come out

lo         Interface doesn't support scanning.

eth2       Scan completed :
           Cell 01 - Address: 00:14:A5:0F:06:F6
                     ESSID:"simon"
                     Protocol:IEEE 802.11bg
                     Mode:Master
                     Channel:11
                     Encryption key:off
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                                11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                48 Mb/s; 54 Mb/s
                     Quality=59/100  Signal level=-65 dBm  
                     Extra: Last beacon: 1264ms ago

eth0      Interface doesn't support scanning.


i hope i wrote it clear enough.

---

### Post by mikewhatever on 2007-01-15
Have you installed Gnome Network Manager. You can find it in Synaptic if you want to, it is called 'network-manager-gnome'. If you like the terminal then
```
 sudo apt-get install network-manager-gnome
```
 After installation and reboot, you will have another icon on the panel near the clock. Click on it and see what networks are available.

---

### Post by shanepardue on 2007-01-15
Gnome network manager like mikewhatever said or wifi-radar. both are nice and easy.

---

