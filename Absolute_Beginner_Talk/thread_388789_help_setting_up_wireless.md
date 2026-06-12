---
title: "help setting up wireless"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by bobplano on 2007-03-19
hello,

i am using 6.06 to try out linux and get away from windows. i have a wireless network and like many other people i'm having trouble getting ubuntu to connect to the internet. i don't have a long enough ethernet cable and the only other computer is a laptop(the computer i'm using ubuntu on is a desktop). Ubuntu won't boot from the laptop(it stops at 'waiting for system root files' or something) but the live CD will. i put ubuntu on an external hard drive so i wouldn't have to mess with the windows drive at all 
i know there is a guide to my wireless adapter, WUSB54GS v.1, but that uses apt-get and doesn't that require an internet connection? 
is there a way to either get the package off the live version and put it on a usb stick and run it?
another way i think i could make this work was to get the drivers i need from the CD and install them, but i don't know how to do that either. 

any help on this would be appreciated and thanks in advance

---

### Post by Hortinstein on 2007-03-20
easy answer.....buy longer cord.....i am not sure about the others but heres a free bump for u :-)

---

### Post by txhellkat138 on 2007-03-20
Hello. I have the same issue wevery time I install Ubuntu On a new system I can't run 250 feet of cable.So here's my suggestion it always works for me. o to the pc you can get on the internet hell borrow a friends if you gotta and download ndiswrapper 1.8 or 1.9 either one works and ndiswrapper-common and install them then find your linksys driver disck and copy it over to your harddrive as well on the new install. you will also need to have build-essential and linux headers installed which I believe you can do through synaptic once you get those 2 packagges installed then install ndiswrapper. then browse into your wireless driver folder from the windows version of the disc you have and find the file WUSB54GS.inf and remember the path to it open up a terminal and type in ```
sudo ndiswrapper -i /path/to/your/driver/WUSB54GS.inf
``` and hit enter
not type ```
sudo ndiswrapper -l
```and you should get a line like ```
WUSB54GS      hardware present
``` after that type in ```
sudo ndiswrapper -m
``` which will write the alias info in your modprobe file now do ```
sudo depmod -a
```(not real sure why but it was on the walkthrough i learned all this form about a year go) and then ```
sudo modprobe ndiswrapper
``` which should load the module into the kernel. to check it type in lsusb and check for ndiswrapper in the output. you should see your card light up at this point. if it is try typing ifconfig and if a wlan0 entry is there then you asre set depending on if you use kde or gnome you can make  it connect pretty easy. I never could do it with gnome but im sure there's an easy way. Im still a newb but I hope this helps a little

---

### Post by bobplano on 2007-03-22
unfortunately synaptic connects to the servers which again requires internet. if the internet crashed tomorrow there would be mass panic.well ill try an 'alternate' way to install the packages, or in other words getting the links and going to the sites on windows then transferring them to ubuntu. thanks for responding though and ill try this out once i get the packages.

---

