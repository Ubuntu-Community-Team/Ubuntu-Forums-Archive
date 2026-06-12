---
title: "Dual Boot xp = :) ubuntu = :("
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by liammc03 on 2007-05-07
I have two partitions on my laptop one with windows xp sp2 which I am getting rid of soon and Ubuntu 6.06 which i plan to keep. I boot in to Windows and it is perfect I boot on to Ubuntu every thing is fine untill 7mins after i have logged in, well what happens is everything works but after 7mins it just restarts its self :S

All Help Apreciated.

---

### Post by liammc03 on 2007-05-07
any help?

---

### Post by John.Michael.Kane on 2007-05-07
> **liammc03 said:**
> any help?

More info may be needed.

From what your describing  ubuntu  randomly rebooting with out warning. would lead one to feel it could be a hardware issue not a software issue. 

If you have your windows data eg: personal files backed up ect. you may want to try installing ubuntu alone. 

Also would help if you listed you full system spec's.

---

### Post by Wiebelhaus on 2007-05-07
> **SD-Plissken said:**
> More info may be needed.

From what your describing  ubuntu  randomly rebooting with out warning. would lead one to feel it could be a hardware issue not a software issue. 

If you have your windows data eg: personal files backed up ect. you may want to try installing ubuntu alone. 

Also would help if you listed you full system spec's.


/agree.

---

### Post by liammc03 on 2007-05-07
Thanks Its fixed now :S Dont know what was causing it :S But there is one more issue I cannot use my wifi card because of drivers but apparently there is somthing i can download that will force it to work? Is this correct?

---

### Post by Outrunner on 2007-05-07
> **liammc03 said:**
> Thanks Its fixed now :S Dont know what was causing it :S But there is one more issue I cannot use my wifi card because of drivers but apparently there is somthing i can download that will force it to work? Is this correct?

Since we don't know what WiFi card you have, we can't tell you how to get your card to work. At least tell us your laptop's model

---

### Post by John.Michael.Kane on 2007-05-07
For wifi we will will need the model card , and chipset eg: broadcom,Ralink

Heres a guide it may help.
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Should you have further issue installing wfi just post.

---

### Post by liammc03 on 2007-05-07
Ok here are a few specs....

My Comp = Compaq Evo N410c

My Wireless Manafactor: Linksys

Wifi Card Model: ireless-G Notebook Adapter WPC54GS V2

---

### Post by Wiebelhaus on 2007-05-07
[http://ubuntuforums.org/showthread.php?t=355247](http://ubuntuforums.org/showthread.php?t=355247)

same issue resolved.

thanks to user "tjtansey"

> Gwen,
dmizer and I have been woorking on a new how to for the wpc54g. I have version 2 if you have a different version reference linksys download site and plug appropriate file name in (I hope).
Also before you try to install at all remove any currently installed version of ndiswrapper.

to remove any previously installed drivers, run the following commands after re-installing ndiswrapper. ndiswrapper -l (will list installed drivers) sudo ndiswrapper -e (driver name **no ext needed**) this will remove old drivers

Here is my how to:
Installation of Linksys WPC54G v2 wireless card
remove card
in terminal:
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.8

mkdir linksys
cd linksys
wget [ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip)
unzip wpc54g_v2_driver_utility_v2.0.zip

At this point you have the software you need to install your driver

Now a little housekeeping to ensure you don't any future problems, we are going to convert the following filename to all CAPS this ensures your driver recognizes the file
mv tnet1130.sys TNET1130.sys

Now we are going to install the drivers
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper

Now we are going to set up your system to initialize on boot-up
sudo nano /etc/modules

add the following line at the end of the file
ndiswrapper
then ctrl-x
y
enter
Now insert your card and enter
ndiswrapper -l

the screen should read:
Installed drivers:
lsbcmnds driver installed
lstinds driver installed, hardware present
Disable your wired network connectio
Now run dmesg and look for the following lines:
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.1 loaded
ndiswrapper: using irq <irq#>
wlan0: vendor: 'TNET1130'
wlan0: ethernet device 00:0f:66:d8:a7:88 using NDIS driver lstinds, 104C:9066:1737:0033.5.conf

Now restart networking with the following command:
sudo /etc/init.d/networking restart
configure your wlan in System>Administration>Networking
Good luck I hope this helps

---

