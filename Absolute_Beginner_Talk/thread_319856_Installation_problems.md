---
title: "Installation problems"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by bxlinux on 2006-12-16
Hello all, I am new to the linux world and have been having some trouble with my ethernet card. I downloaded the drivers from intel for linux kernel and wish to install. As I am new I donot see dont laugh now an install file. So i checked out this link i found on installing [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) but as I am a noob I am very lost. I tried the commands but I am not sure if I am pointing to the correct file for installation. The driver I am trying to install is for a e100 ethernet card. After extracting as in the read me for the driver it has a section on compiling which is where I am lost. any help as to which file I need to compile would be appreciated. Here is the list of files after extracting the download. e100.7 e100.spec ldistrib.txt, sums with no file extension. In the source folder of the extraction e100.c ethtool.c kcompat.h, makefile. Thats all the files that were extracted. Now what do I from here? Thanks

---

### Post by wpshooter on 2006-12-16
What is the problem that you are having with your ethernet card ?

Is it not being detected and configured by the installation of Ubuntu ?

---

### Post by bxlinux on 2006-12-16
It is being detected but will not no matter what I try it will not pull an IP address. So I figured I would try to get a linux driver and see if that works hence why I am trying to install the ethernet card driver. You can check out that connectivity thread here [http://www.ubuntuforums.org/showthread.php?t=309262](http://www.ubuntuforums.org/showthread.php?t=309262). Be forwarned it is long.

---

### Post by bxlinux on 2006-12-16
Ok I think I found out how to 'make' an install file but now I get the message that it cannot write to /var/cache/man/cat7/e100.7.gz in catman mode e100. What does this mean? I did put in the appropriate password when prompted.

---

### Post by Scorpuk on 2006-12-16
Are you saying your linux box is conencted to a router for internet and that you cannot get an IP address from the router?


Couple of questions, if that is the case:


1. Is your router set upto be a DHCP server?

2. In the network configuration section have you set your ethernet adaptor to obtain an IP from a DHCP server?

---

### Post by wpshooter on 2006-12-16
> **Scorpuk said:**
> Are you saying your linux box is conencted to a router for internet and that you cannot get an IP address from the router?


Couple of questions, if that is the case:


1. Is your router set upto be a DHCP server?

2. In the network configuration section have you set your ethernet adaptor to obtain an IP from a DHCP server?

I think you are probably correct that the problem here lays in the configuration of the router.  If it is correct, I believe his card would work immediately after installing Ubuntu.

---

### Post by bxlinux on 2006-12-16
No I am not using a router I am connected directly through my cable modem. I have a windows pc which is what I am using to connect right now. I tried putting in static ip's as well to no avail.

---

### Post by Scorpuk on 2006-12-16
Ahhh then it sounds as though you have a problem with linux not recognising your cable modem.


If you post what make and model it is, maybe someone can give you some help with this as I have no experience of cable modems as my box is connected to a router.


Good luck.

---

### Post by bxlinux on 2006-12-16
Well the make of the modem is Arris model tm402G/110.

---

### Post by Scorpuk on 2006-12-16
Had a look at the Arissi web site for the manual to your modem: [http://www.arrisi.com/consumer_products/_docs/TM402_User_Guide.pdf]("http://www.arrisi.com/consumer_products/_docs/TM402_User_Guide.pdf")



Couple of things to try, I am not at my linux box so cannot be certain as to dialogue boxes etc. If anyone else can confirm etc.



1. On your windows computer open a dos box: click START -> Run... ->  Type ipconfig at the dos prompt.

2. Note down the IP address and Subnet mask and the Default Gateway numbers (format 999.999.999.999)


Now on your linux box:


Goto the network configuration for IP addresses etc and locate entries for the above information. Since your windows computer is not connected it shoudl be ok to use the same IP address as its. :)


May or may not work, but worth a shot. :D

---

### Post by bxlinux on 2006-12-16
Tried entering that info on the linux box but still unable to connect or ping. ](*,)

---

