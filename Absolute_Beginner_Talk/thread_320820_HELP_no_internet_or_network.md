---
title: "HELP no internet or network"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by superoo on 2006-12-18
Hi, I've just installed Ubuntu Edgy Eft and Windows XP Professional SP2.  Both boot fine using GRUB.  I have an ethernet DSL modem hooked to a router hooked to 3 computers.
In Windows everything including file/printer sharing works fine.  I didn't even have to configure anything but in Ubuntu nothing works!!! I'm writing this from Windows...

When i use Ubuntu, the light on the router doesn't even turn on... I have gone through all steps in the Ubuntu help including 
sudo pppoeconf
and installing/configuring samba
I also tried some stuff from forums but to no avail.

In administration>network eth0 is enabeled and i can ping 127.0.0.1 and 127.0.1.1

plz help me, i've been working on it all weekend and am now totally lost...
also i'm an extreme newby](*,)

---

### Post by macogw on 2006-12-18
```
ifconfig
```
What comes up?

can you ping 192.168.1.1?

---

### Post by superoo on 2006-12-18
I cannot ping 192.168.1.1

```
shiney@shiney:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:F8:05:0B:8C
            inet6 addr: fe80::200:f8ff:fe05:b8c/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
            Interrupt:11 Base address:0x8000

lo         Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:114 errors:0 dropped:0 overruns:0 frame:0
           TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:7620 (7.4 Kib)  TX bytes:7620 (7.4 Kib)
shiney@shiney:~$
```

Sorry for the late reply, i had to take a picture and manually write this...

---

### Post by macogw on 2006-12-18
Well no wonder you couldn't ping the router.  The router's not giving you an IP address.  For the sake of fun, can you
```

ifconfig eth0 down
ifconfig eth0 up

```
and see if anything happens?

---

### Post by superoo on 2006-12-18
```
shiney@shiney:~$ ifconfig eth0 down
SIOCSIFFLAGS: Permission denied
shiney@shiney:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied
shiney@shiney:~$
```

The same error mesages came up when i tried to use the internet sharing HOWTO from this forum... The router works fine with Windows with no setup.  I have had the router for like 10 years and lost the documentation on how to set it up.  It is a Micronet SP243A 10BASE-T EtherHub.  The other components are all newish.  AsusA7V266, Athlon XP 2000, 512 Mb DDR400, Geforce 2 64Mb, CDRW if this helps

---

### Post by atnishry on 2006-12-18
Hi I had smiler problem, it might be that you don't get an ip address from your router.
it seems that some routers doesn't work out of the box with Ubuntu dhcp client because it doesn't send a the computer name the the dhcp server.
if that is the case you need to edit your  /etc/dhcp3/dhclient.conf - 
> sodo nano /etc/dhcp3/dhclient.conf
and make sure that it's sends your computer name as a hostname:
> send host-name "[COLOR="Lime"]Computer Name[/COLOR]";
you might just need to remove the "#" and place your computer name.
one more problem that I had was that my router didn't send back domain name servers so I need to config those as well, it isn't big deal all you need to do it to get you'r ISP DNS (you can get it from your router or your windows and then make sure you have this line in /etc/dhcp3/dhclient.conf with your ISP DNS.
> prepend domain-name-servers 203.161.127.1, 203.153.224.42, [COLOR="Lime"]xxx.xxx.xxx.xxx[/COLOR];

totally forgot to restart the network, so what you need to do is:
> 
sudo ifconfig eth0 down
sudo ifconfig eth0 up


or 

> 
sudo /etc/init.d/networking restart

 
and then look at the ifconfig result...
have fun !

---

### Post by atnishry on 2006-12-18
add [COLOR="Lime"]"sudo"[/COLOR] before [COLOR="Lime"]ifconfig eth0 down[/COLOR]
you need root access 


> **superoo said:**
> ```
shiney@shiney:~$ ifconfig eth0 down
SIOCSIFFLAGS: Permission denied
shiney@shiney:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied
shiney@shiney:~$
```

The same error mesages came up when i tried to use the internet sharing HOWTO from this forum... The router works fine with Windows with no setup.  I have had the router for like 10 years and lost the documentation on how to set it up.  It is a Micronet SP243A 10BASE-T EtherHub.  The other components are all newish.  AsusA7V266, Athlon XP 2000, 512 Mb DDR400, Geforce 2 64Mb, CDRW if this helps

---

### Post by superoo on 2006-12-18
ok,  i changed
```
send host-name "shiney"; 
```
also
```
prepend domain-name-servers 10.0.0.138,60.229.157.25; 
```
then ran
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
with no output
then ran
```
shiney@shiney:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:F8:05:0B:8C
            inet addr:10.0.0.138 Bcast:10.255.255.255 Mask:255.0.0.0
            inet6 addr: fe80::200:f8ff:fe05:b8c/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:115 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
            Interrupt:11 Base address:0x8000

lo         Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:458 errors:0 dropped:0 overruns:0 frame:0
           TX packets:458 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:33376 (32.5 Kib)  TX bytes:33376 (32.5 Kib)
shiney@shiney:~$
```

I can now ping 10.0.0.138 (modem)
but not 60.229.157.25 (router)

If there are any further ideas i would be so gratefull thanks for all input so far...

---

### Post by atnishry on 2006-12-18
what is a bit wired cause you don't soups to get  your router ip as your ip...
try 
> sudo /etc/init.d/networking restart

and then ifconfig

---

### Post by superoo on 2006-12-18
Hmm,
i restarted ubuntu then ran
```
sudo /etc/init.d/networking restart 
```
it had a lot of output (i cant cut and paste)
then i got this again
```
shiney@shiney:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:F8:05:0B:8C
            inet6 addr: fe80::200:f8ff:fe05:b8c/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:24 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
            Interrupt:11 Base address:0x8000

lo         Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:146 errors:0 dropped:0 overruns:0 frame:0
           TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:9988 (9.7 Kib)  TX bytes:9988 (9.7 Kib)
shiney@shiney:~$
```

I cannot ping anything again... I really dont know what to do

---

### Post by superoo on 2006-12-18
could the router be the problem? its very old... is there anything else i can try?

---

### Post by superoo on 2006-12-18
i tried mooving my ethernet card around to different slots and it had no effect.  Do i need to get drivers or something? I also tried plugging the modem directly into the LAN card and all results were exactly the same again...

---

### Post by RudolfMDLT on 2006-12-18
Hi, you said that not even the router light comes on? Um, are you talking about the ehternet green and/or orange light next to the port number that you plugged in your network cable? If the router light doesn't come on then you won't be getting and IP will you?

If i've got it wrong ang the router is on try this:

edit the networking config file manually and assign yourself a fixed IP. I'll reboot into Ubuntu now and show you how.

---

### Post by superoo on 2006-12-18
yes, the green/amber light on the router next to port 2 doesn't light up when i load ubuntu. all other ports stay lit as usual.

I downloaded some drivers but have no idea how to install them
this is the readme

```
This readme file describes how to configure the Digital Fast EtherWORKS PCI
10/100 (DE500-XA, -AA, -BA) and Digital EtherWORKS Turbo PCI 10 (DE450-CA, -TA) Unixware 2.1 drivers into the system kernel using the "id" tools, i.e., idinstall and idbuild.  The "System" file for either driver should not be changed. The driver will autodetect the hardware and read its configuration for the system device database. The driver will issue a warning if the adapter was not configured properly.

Fast EtherWORKS PCI 10/100 Installation
---------------------------------------
Install the adapter into the Unixware System and boot. Copy the files from the de500.cf directory to a temporary subdirectory. From the temporary directory type the following two commands:

/etc/conf/bin/idinstall -R /etc/conf -M -k de500
/etc/conf/bin/idbuild -M de500

Now rebuild system's hardware option database by typing:

	dcu -S

There are two system files you'll need to edit prior to configuring
TCP/IP.

Edit /etc/confnet.d/netdrivers and add the following first line:

	de500_0 inet

Edit /etc/confnet.d/inet/interface and add the following as the last line:

	de500:0::/dev/de500_0:-trailers::

Once this has been done you can configure TCP/IP by running:

	/etc/confnet.d/configure -i

These two files are documented in the "TCP/IP Administration" book. Now reboot
and the driver should load and TCP/IP should be operational.

EtherWORKS Turbo PCI 10 Installation
---------------------------------------
Install the adapter into the Unixware System and boot. Copy the files from the de450.cf directory to a temporary subdirectory. From the temporary directory type the following two commands:

/etc/conf/bin/idinstall -R /etc/conf -M -k de450
/etc/conf/bin/idbuild -M de450

Now rebuild system's hardware option database by typing:

	dcu -S

There are two system files you'll need to edit prior to configuring
TCP/IP.

Edit /etc/confnet.d/netdrivers and add the following first line:

	de450_0 inet

Edit /etc/confnet.d/inet/interface and add the following as the last line:

	de450:0::/dev/de450_0:-trailers::

Once this has been done you can configure TCP/IP by running:

	/etc/confnet.d/configure -i

These two files are documented in the "TCP/IP Administration" book. Now reboot
and the driver should load and TCP/IP should be operational.
```

The card says FCC ID: A09-DE450 
and the chip is digital 21041-AA DC1017BA
I have read that there are problems with this card...
thanks

---

### Post by RudolfMDLT on 2006-12-18
If you could tell me where you downloaded the driver it would help but try this.

open up the terminal and type this:

> cd /home/YOURNAME

mkdir temp


now copy the directory the readme tells you to this directly using your mouse and keaybord(not in the terminal).

after that:

> 
cd /home/YOURNAME/temp



Now copy and paste everything form the readme that they tell you to type, into the terminal and press enter.

Post back how that works.

---

### Post by superoo on 2006-12-18
I got the driver from [http://www.network-drivers.com/companies/316.htm](http://www.network-drivers.com/companies/316.htm)
The driver i got is 45uxw101.tar
They also have
45lli245.dd 
45mdi102.dd

I followed your instructions untill an error occured at

```
shiney@shiney:~/temp$ /etc/conf/bin/idinstall -R etc/conf -M -k de450
bash: /etc/conf/bin/idinstall: No such file or directory
shiney@shiney:~/temp$
```

The files in /home/shiney/temp/de450.cf are
Driver.o
Drvmap
Master
Node
Space.c
System

I think these drivers are for some other version of Linux/Unix since i do not have a directory etc/conf

---

### Post by RudolfMDLT on 2006-12-18
Okay,

I tried the commands, obviously they don't work. I checked out the drivers page - It's for a Unix system.

[http://www.sco.com/products/unixware714/](http://www.sco.com/products/unixware714/)

This OS Specifically.

I've been busy looking for an alternative - Didn't find one. How old is this card? You might try finding an equivalent driver here:

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

but first post the exact card model and age please.

---

### Post by superoo on 2006-12-18
Thanks heaps for your help, the only things i know about this card are that the card says FCC ID: A09-DE450 and the chip is digital 21041-AA DC1017BA.  

I've been reading around and the de4x5 series appear to have a problem with linux so i'm going to make life easy and get a different card.  

Thanks again guys.  I'm going to bed now coz its getting to 3 am in sydney cya:)

---

### Post by RudolfMDLT on 2006-12-18
I was gonna sugest that! - But it's rude telling a guy to chuck his card and buy a new one! :)  

Good call! 

Cheers and Goodluck,

Rudolf

---

