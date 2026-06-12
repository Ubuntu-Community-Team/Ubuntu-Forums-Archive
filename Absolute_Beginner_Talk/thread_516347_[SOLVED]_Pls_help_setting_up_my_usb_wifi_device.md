---
title: "[SOLVED] Pls help setting up my usb wifi device"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Funkey Monkey on 2007-08-03
Hi,
I have a usb wireless adapter, but its not working out of the box.
System -> Admin -> Network only has my wiredlan and modem

I have used search function but there is no definitive guide for my device.

Its a Mecer Mini Wireless Lan Usb 2.0 Adapter.
I phoned them and they said the chipset is a Abocom WUG2400.

I googled it and a website said the Chipset is TNET1450
and it also says someting about ACX111
[http://acx100.sourceforge.net/matrix.html](http://acx100.sourceforge.net/matrix.html)

I`m Running the Desktop version of Ubuntu 7.04 Feisty Fawn
My lsusb gives:
xxx@desk:~$ lsusb
Bus 004 Device 004: ID 07b8:b21a D-Link Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c044 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

And lspci gives:
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)


I think that Ndiswrapper is the only option for me but the guide is a bit confusing for a person just stepping into the light.
[https://help.ubuntu.com/community/WifiDocs/Driver/](https://help.ubuntu.com/community/WifiDocs/Driver/) Ndiswrapper
Another website I found regarding ACX111
[https://help.ubuntu.com/community/WifiDocs/Driver/](https://help.ubuntu.com/community/WifiDocs/Driver/) acx111?action=show&redirect=WifiDocs%2FDevice%2FAc x111

Can someone please help me to install the wifi device without breaking feisty???

---

### Post by jombeewoof on 2007-08-03
first download ndiswrapper [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

then cd into the directory you downloaded it too.
then 
```
sudo apt-get update && sudo apt-get install build-essential apt-get install linux-header`uname -r'
make && sudo make install 
```

as long as you don't have any errors it's installed

---

### Post by Funkey Monkey on 2007-08-04
Thanks for the advise but I dont think it worked

This is what I found in the terminal. 


xxx@desk:~$ cd \Desktop
xxx@desk:~/Desktop$ cd \ndis
xxx@desk:~/Desktop/ndis$ sudo apt-get update && sudo apt-get install build-essential apt-get install linux-header`uname -r'
> make && sudo make install
> 
>

---

### Post by Funkey Monkey on 2007-08-06
K this is what I have done: 

first I

lsusb  and found my usb device code  is  07b8:b21a

I the went to 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and Downloaded   
 1.[WWW] [http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
 2.[WWW] [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
 3.[WWW] [http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk)

I then sudo dpkg -i ndiswrapper-common_*.deb
           sudo dpkg -i ndiswrapper-utils*.deb
           sudo dpkg -i --force-depends ndisgtk_*.deb

then  echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

I tried to use System | Administration | Windows wireless drivers but could not get it to load the .INF file 

So I tried sudo ndiswrapper -i ~/drivers/drivername.inf

AND IT WORKED. 
the device is now on roaming mode so i`ll be playing with it a bit more.

(I also disabled network manager don`t know if it did something good)
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

I hope this will help some poor sole in the future. 
We as ubuntu users should ask the manufacturers to give use proper drivers 
(I would sign a petition)

---

### Post by Funkey Monkey on 2007-08-06
well i must be doing something wrong because it does not want to connect to router or internet.
I will try to fix it in the distant future.

---

