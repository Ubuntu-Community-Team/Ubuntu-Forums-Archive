---
title: "Windows Wireless Drivers"
date: 2005-04-01
forum: Apple PPC Users
---

### Post by carlossousa on 2005-04-01
Hello,

I've read somewhere that it is possible to use the windows drivers for wireless usb/pcmcia card on linux. Has this been tried yet? I think that it's harder to try and reverse-engineer the broadcom wifi adapter so why not use the windows drivers for a external usb wifi adaptor, for example the dlink 120+.

Any opinions?

Thanks

---

### Post by bobmitch on 2005-04-01
Google, or search these here forums for **ndiswrapper** .

Good luck.

---

### Post by carlossousa on 2005-04-01
Hello,

Thanks for the reply, but when I asked, I was wondering if anyone had tried doing it on k/ubuntu ...

Thanks

---

### Post by underworld on 2005-04-01
[QUOTE=carlossousa]Hello,

Thanks for the reply, but when I asked, I was wondering if anyone had tried doing it on k/ubuntu ...

Thanks[/QUOTE]

Yes, I do. This would be the ndiswrapper-utils from hoary with the original windows drivers from the cd. The wireless device is a USB Asus WL-167g.
But I have a problem, sometimes when I switch on the laptop it doesn't work, so I have to reboot the laptop 1-3 times. Have tried to reload the ndiswrapper module but that didn't help.
Nonetheless I am waiting for the opensource drivers for this device. They are being developped ([http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) ).

Greetings,
Daniel

---

### Post by bobmitch on 2005-04-01
[QUOTE=carlossousa]Hello,

Thanks for the reply, but when I asked, I was wondering if anyone had tried doing it on k/ubuntu ...

Thanks[/QUOTE]

Then why didn`t you post it in an ubuntu forum?  [/sarcasm]

There have been plenty of ndiswrapper guides/questions on these forums - if you at least give it a shot, then if you have a problem, come back with the details.  I`m just trying to point you in the right direction, see if you can get it working - if not, we`ll try and help.

You are 10 times more likely to receive help if you do some groundwork first. :)
Good luck.

---

### Post by fabiang on 2005-06-07
[QUOTE=underworld]Yes, I do. This would be the ndiswrapper-utils from hoary with the original windows drivers from the cd. The wireless device is a USB Asus WL-167g.
But I have a problem, sometimes when I switch on the laptop it doesn't work, so I have to reboot the laptop 1-3 times. Have tried to reload the ndiswrapper module but that didn't help.[/QUOTE]
Yesterday, in asus support site you can found the drivers source code, you can get it from here [http://www.asus.com.tw/pub/ASUS/wireless/WL-167g/SourceCode-V2030.zip](http://www.asus.com.tw/pub/ASUS/wireless/WL-167g/SourceCode-V2030.zip) (note it's says .zip but really is a .tar.gz)

i was:
sudo apt-get install linux-headers
mv Source....zip Source.tar.gz
tar xvfz Source.tar.gz
see the readme :)

---

### Post by ok2ar on 2006-10-09
Hi folks,

After doing ndiswrapper and all the other required things,  I went from NO wireless to having all my wireless devices working using NDISGTK.   
NDISGTK allows you to use your windows/98/eXPee/   .inf files with unbuntu.
The three wireless USB devices it fixed are the Netgear MA111, Zyxel AG200, and the built-in prism3 based wireless on my Mal Mart A535 laptop.
The terminal command DMESG told me things were working.  Here is my present 
/etc/network/"interfaces"
-------------start----------------
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp



iface wlan0 inet dhcp
wireless-essid YOURSSID
wireless-mode managed
 
auto wlan0

iface wlan1 inet dhcp
wireless-essid YOURSSID
wireless-mode managed
wireless-key YOURSECRETCODE

auto wlan1

iface wlan2 inet dhcp
wireless-essid YOURSSID
wireless-mode managed

auto wlan2
-----------------------END--------------------
this forum is great.  hope this helps.  
regards, 
jd

---

