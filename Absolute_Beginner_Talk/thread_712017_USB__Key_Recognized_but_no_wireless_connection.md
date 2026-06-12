---
title: "USB  Key Recognized but no wireless connection"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by manu769 on 2008-03-01
hello everyone , 
hope you can help . I'm new to Ubuntu. My wireless connection with Ubuntu  is not working.
My USB key is recognized when I digit  *iwconfig* in the terminal but it won't connect .
It ask me for my WEP key which I put in but it won't recognize it . With windows that WEP key was working and connecting me immediately . I even tried to change password in my router configuration but it doesn't work.
What's wrong ?

Is there any code I can digit in the terminal ??
Thanks please reply with any idea you have it may work .

---

### Post by paultag on 2008-03-01
Can we get more info? What make / model and mfg of the USB Dongle?

try:
```

iwlist scan

```

Also, have you tried nm-applet? the GNOME wireless utility on the menu bar? If you have an ASCII WEP password, use that option, and if you have a HEX WEP then use the HEX option.

Cheers,
Tag

---

### Post by Hightide on 2008-03-01
HI,  when you try Tag's code, also have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188")

regards

:)

---

### Post by kracheck on 2008-03-01
I wrote this a while ago for my USB dongle, you might find some information in it that can be usefull in oder to get your stick work


USRobotics wireless USB Adapter (model : USR5422) and Ubuntu 7.10 with WPA/Static IP

Download the latest version of ndiswrapper from [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) (I downloaded version 1.52)

*Install as follows :
tar -zxvf ndiswrapper-1.52.tar.gz (this creates the ndiswrappe1.52 directory)
cd ndiswrapper-1.52
make distclean
make
sudo make install

*look for the original driver for USR5422 802.11g 54 Mbps USB Adapter here : 
[http://www.usr.com/support/5422/5422-files/5422-files.exe](http://www.usr.com/support/5422/5422-files/5422-files.exe)
Unzip the file and look for the folder "Driver".  Copy this folder to a USB key and put the content on the linux pc.
In this folder change all the names of the files into small letters, no capital letters.

*install the driver
sudo ndiswrapper -i filename.inf (for instance sudo ndiswrapper -i /home/"username"/Desktop/Driver/rsc4usb.inf)

*check the installation with
ndiswrapper -l
The outcome of this command is either

rsc4usb driver installed
device (0BAF:0118) present

or

rsc4usb driver installed
device (0BAF:0118) present (alternate driver: p54usb) 

In this last case you will need to do some additional tweaking. The kernel may use p54usb module for the USB Adapter. If that module is loaded, then ndiswrapper will be unable to 

use that device.  First we remove the alternate : 
modprobe -r p54usb
Then we blacklist the module to make sure it doesn't load at start-up
sudo nano /etc/modprobe.d/blacklist
Add :
#blacklist for ndiswrapper
blacklist p54usb

*Now we make sure that ndiswrapper gets loaded at start-up, to do that we type

sudo nano /etc/modules
add the word "ndiswrapper" to the end of this file and save it

*In order to make WPA with a static ip work, make sure the /etc/network/interfaces file looks like this (you need to be root to edit it)

auto lo 
iface lo inet loopback 
address 127.0.0.1 
netmask 255.0.0.0

auto wlan0 
iface wlan0 inet static 
address 192.168.0.10 #this is the ip adress I assign to the USB dongle
gateway 192.168.0.1 #this is the ip adress of  
dns-nameservers 192.168.0.1 
netmask 255.255.255.0  
wpa-ssid MY NETWORK NAME
wpa-ap-scan 2 
wpa-proto WPA 
wpa-pairwise TKIP 
wpa-group TKIP 
wpa-key-mgmt WPA-PSK 
wpa-psk MY SCRET PASSPHRASE  #obtain it by typing wpa_passphrase YOUR SSID YOUR PASSPHRASE at the command prompt


At every reboot my network was down so I had to invoke a start-up script (credits go to wieman01)
*Create script
sudo nano /etc/init.d/wireless-network.sh
Add this line & save file:
/etc/init.d/networking restart

*Change permission (executable) of the file :
sudo chmod +x /etc/init.d/wireless-network.sh

*Create symbolic link:
sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S40wireless-network

*reboot the system by typing
sudo shutdown -r now

---

