---
title: "install wireless netgear"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Tozen on 2006-12-18
I have installed xubuntu on a laptop and everything works fine, but now do I want to add a brand new "Netgear  WG511 wireless PCMIA-card" (I have installation CD).

The problem is that Im a total beginner to Xubuntu so I dont have a clue how I will do it... I have read something about Ndiswrapper!? what is that?
Is there a step-by-step-thread that I've missed?

Please keep it simple since Im a novice :)

Thanks
/T

---

### Post by wireddad on 2006-12-18
Have you try just plugging it in to see if Ubuntu will recognize the card?  I have a D-Link card and it recognized it no problem.

---

### Post by Tozen on 2006-12-18
I have tried to both put it in when xubuntu is running and before boot... but nothing happends...

---

### Post by wireddad on 2006-12-18
I am also a newbie, but try these:
 
[http://toys.lerdorf.com/archives/15-802.11g-Netgear-WG511-and-Linux.html](http://toys.lerdorf.com/archives/15-802.11g-Netgear-WG511-and-Linux.html)
 
[http://www.larsen-b.com/Article/73.html](http://www.larsen-b.com/Article/73.html)

---

### Post by wireddad on 2006-12-18
2 more sites that may help.
 
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
 
[http://grumpymole.blogspot.com/2006/11/xubunt-edgy-getting-wireless-going.html](http://grumpymole.blogspot.com/2006/11/xubunt-edgy-getting-wireless-going.html)

---

### Post by wireddad on 2006-12-18
Found something else that may help.

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG511andNdiswrapper?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG511andNdiswrapper?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Tozen on 2006-12-19
Thanks for all your posts :)
I must admit that Im lost now...
I have tried the "lshw"-command and got:
*-network UNCLAIMED
          description: Ethernet controller
          product: 88w8335 [Libertas] 802.11b/g Wireless
          vendor: Marvell Technology Group Ltd.
          physical id: 0
          bus info: pci@0d:00.0
          version: 03
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          resources: iomemory:f4000000-f400ffff iomemory:f4010000-f401ffff irq:11
-------------------
Does that mean that the card and driver is recognized but not in use?
I cant see the wireless card in the "network-list" (under system)

---

### Post by Tozen on 2006-12-19
Ah... I finally got it working by setting up Ndiswrapper and following the exact intstructions at:
[http://ubuntuforums.org/archive/index.php/t-9454.html](http://ubuntuforums.org/archive/index.php/t-9454.html)
Thanks again! :)

---

### Post by wireddad on 2006-12-20
Awesome.:)

---

### Post by Tozen on 2006-12-20
That was not the end of the problems... 
Setting up my wireless card works just fine, but when I have logged out or restarted, I have to run "modprobe ndiswrapper" and "iwconfig" all over again to connect!? 
Is it supposed to be like this?
Or what could be wrong?

---

### Post by Tozen on 2006-12-23
For the record:
I solved it by opening the terminal window and typing 
```
sudo nano /etc/modules
```
and adding the line 
```
ndiswrapper
```
in the end of the file... then saving it by "ctrl+O"
this makes it loading ndiswrapper at boot, but I've been told that it might have to do it all over if I update the kernel!?

---

