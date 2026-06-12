---
title: "Wireless network prob"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Petrun on 2007-04-17
Hi. 
I just recently installed Ubuntu to my home computer, dualbooting with my Windows XP. 
It just seems that after I installed it, the wireless network doesn't work in Ubuntu. It just sais that the wireless network I am trying to connect to recuires security capabilities unsupported by my hardware. When I was trying Ubuntu out with an Open CD, it worked perfectly.
What to do?

---

### Post by Kobalt on 2007-04-17
Hello,

What version of Ubuntu have you installed ? 
What is the exact model of your wifi card ?

---

### Post by Petrun on 2007-04-17
I am currently running Ubuntu 7.04 beta. And I don't really know what a wifi card is..

---

### Post by bobplano on 2007-04-17
it is the card or adapter that you are using to recieve the wireless signals. for instance my adapter is WUSB54GS. if you think about it all the things in it makes since because it is a wireless G usb adapter

---

### Post by Petrun on 2007-04-17
Mine is WUSB54G, version 4.

---

### Post by bobplano on 2007-04-17
it says [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") that its supposed to work right out of the box. anyway the drivers you seem to need are rt2570

EDIT: try this link they seem to have the same adapter as you
[http://ubuntuforums.org/showthread.php?t=409259&highlight=WUSB54G+v.4](http://ubuntuforums.org/showthread.php?t=409259&highlight=WUSB54G+v.4)

---

### Post by medley on 2007-04-17
> **bobplano said:**
> it is the card or adapter that you are using to recieve the wireless signals. for instance my adapter is WUSB54GS. if you think about it all the things in it makes since because it is a wireless G usb adapter

Hi bobplano

Out of curiousity, how exactly did you get that wi-fi adapter working. I have the same one, trying it on feisty using ndiswrapper, and never succeded. I'm wondering if it's the pc hardware or someting else. I actually tried a wireless pci adapter as well, with no joy.

You wouldn't mind explaining what you did, would you?

Thanks

---

### Post by bobplano on 2007-04-17
well i have speedbooster but you can try the tutorial by javajake. if it works then you can tell him about it. 
its here [http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GS](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54GS)

my only problem with this was i put it in a directory with a space in the name and make wont accept that although you have v. 4 so i don't know how well it will work; i have version 1

the formatting is a little confusing but you need to do get the headers and compilers, get the attachement or new versions of drivers/ndiswrapper, compile ndiswrapper (the repos version is too old), wrap the drivers, install the system files (i think you can get them from the cd), and for fiesty you need to allow enough power to it. make sure to read the troubleshooting section

---

### Post by Jem00 on 2007-04-17
Hey guys,

I'm a beginner to Ubuntu and I would like to learn to use it.

I am dual booting with Windows and i want to use my Netgear ma111 wireless usb on ubuntu...
how would i do this?

Currently in 'Networking' it shows 2 wired connections when I only have one ethernet port and one wireless USB.

:confused: :confused: :confused:

---

### Post by bobplano on 2007-04-17
well making your own thread might get you more support but try this link
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

---

### Post by Jem00 on 2007-04-17
**Thanks **

---

### Post by fathefner on 2007-04-17
corbin@Fathefner:~$ sudo iwconfig wlan0
Password:
wlan0     IEEE 802.11b+/g+  ESSID:off/any  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality:55/100  Signal level:38/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

corbin@Fathefner:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Resource temporarily unavailable

i am using a NETGEAR WG311v2 802.11g Wireless PCI Adapter 

and i cant get the network to go up my WEP is good but it is really slow

---

### Post by bobplano on 2007-04-17
try taking out your security and then setting up the network then adding WEP back in

---

### Post by fathefner on 2007-04-17
ok if does anyone know if fawn will have wifi support

---

### Post by bobplano on 2007-04-17
i think i've read somewhere that fiesty fawn will have better wifi support because it won't just have open source stuff

---

