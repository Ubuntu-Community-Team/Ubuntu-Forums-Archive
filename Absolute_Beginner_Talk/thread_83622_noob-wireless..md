---
title: "noob-wireless."
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by TimAy on 2005-10-29
Well, i'm a noob to ubuntu and linix, but would love to get the damn interent working so that i could learn a bit. 

So i install Ubuntu (dual boot with XP). All lovely. Problem is, I can't seem to ping my router, so obviously i can't look anything up. I'm using a WG311 netgear WNic which it seems is compatible straight off the install. Why isn't it working. When i go iwconfig, my card is there so its picking it up ok. Also, DHCP is turned on on the router so it should be picking up automatically. Is there something im completey missing? 

Any help appreciated.

Also, another semi query. I see all these nice programs that are on the ubuntu iso with the extension .deb. Why wont the ubuntu archiever read these? Im i doing something stupid/using the wrong program?

---

### Post by Manny C on 2005-10-29
Try the following command at a Terminal:
```
 sudo ifup eth1 
```
if your wireless is allocated to eth1 type in the superuser password and see what happens.

What wireless security feature you using on your router?

---

### Post by TimAy on 2005-10-29
the card is under "wlan0" so i typed that in. It says "already configured"

I have WEP enabled. The key for my wep is in hex and afaik only 10 digits, so when i was installing and it asked if i wanted to set up wirless, it seemed strange that it was telling me my key should be 15 or so numbers. Should i try converting the key from hex or something?

edit/ just tried iwlist wlan0 encryption and it says 3 key sizes availible 40, 104, 232 bits but than says error reading wireless key (SIOCGIWENCODE) operation not permitted. ???

now, if i use iwconfig to try change anything, i just get a Operation not permitted

---

### Post by Manny C on 2005-10-29
Try putting sudo before these commands:
```
sudo iwlist wlan0 encryption
``` 
What are you using: Gnome or KDE?

---

### Post by TimAy on 2005-10-29
gnome afaik.i take it putting sudo infront is a type of admin thing? Now the encryption works, its telling me there are 4 keys availible. 

On my router settings (192.168.0.1 from this laptop) my wep key is selected as 64 bits hex. Its something like DC186V5EfF or along those lines. So i went to network and but in that code, but under ascii. When i try sudo iwlist wlan0 encryption it tells me there are 4 availible with number one being the ascii translation of my code. Its 104 bits long. is this right?

---

### Post by TimAy on 2005-10-29
argh. still no luck

right, seems i've narrowed down the problem

i've been trying sudo iwlist wlan0 scanning and it doesnt see anything. So basically, no wireless network is being picked up, even though im typing on one right now!

---

### Post by Manny C on 2005-10-29
Hmm...you should try to install a wireless manager life [wifi-radar]("http://www.bitbuilder.com/wifi_radar/") or [NetworkManager]("http://people.redhat.com/dcbw/NetworkManager/"). Both are in the repositories. I think NetworkManager is better. But then again, I don't use Gnome. So have a look at their websites and decide what suites your setup best. 
Then to install them, simply issue the following command:
```
 sudo apt-get install network-manager
``` if you want NetworkManager
OR
```
sudo apt-get install wifi-radar
``` if you want Wifi-Radar. [Make sure you have the Universe repositories enabled in your sources.list file.]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse")

Incidentally, if you are a noob, it may be worthwhile spending some time reading through the unofficial (and now slightly outdated...but only slightly) [UbuntuGuide]("http://ubuntuguide.org/"). The guy who put this together, has had a health problem which is slowing down/stopping (?) him from updating the Guide to Breezy.

---

