---
title: "i cant get internet on"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by katarot on 2006-03-13
im using a belkin g router today was the first time iv ever saw linux on my laptop iv only ever used win xp and i got on the internet fine 
can some help me and explain how i can get the internet on ubuntu

---

### Post by Brunellus on 2006-03-13
[QUOTE=katarot]im using a belkin g router today was the first time iv ever saw linux on my laptop iv only ever used win xp and i got on the internet fine 
can some help me and explain how i can get the internet on ubuntu[/QUOTE]
what laptop/wireless card?

---

### Post by katarot on 2006-03-13
iv got a dell inspiron and dell wireless 1370 wlan mini-pci card

---

### Post by Brunellus on 2006-03-13
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29)

Your card isn't listed, but I strongly suspect that you will need to use ndiswrapper and the windows driver (an .inf file).  

am at work now, can't give more exhaustive help, but will look in later.

---

### Post by katarot on 2006-03-13
im using the live disk at the moment i dont want to install ubuntu and get rid of windows unless i definetly get the internet on i cant live without the internet

---

### Post by Iowan on 2006-03-13
[QUOTE=katarot]im using the live disk at the moment i dont want to install ubuntu and get rid of windows unless i definetly get the internet on i cant live without the internet[/QUOTE]
Consider a dual-boot system?

---

### Post by Brunellus on 2006-03-13
[QUOTE=Iowan]Consider a dual-boot system?[/QUOTE]
seconded.  Also, there are certain issues that apply to liveCDs and not necessarily to fully-installed systems--drivers for wireless cards being one, for instance.  likewise (closed-source) graphics cards drivers, multimedia codecs, and the like.

---

### Post by kwjaxon on 2006-03-13
I am new and am having the same problem.  Have the dual boot installed and cannot get online.  Modem in Win. is Lucent Winmodem.  Have tried thru email as well as networking.  Can you help, please?

---

### Post by Brunellus on 2006-03-13
[QUOTE=kwjaxon]I am new and am having the same problem.  Have the dual boot installed and cannot get online.  Modem in Win. is Lucent Winmodem.  Have tried thru email as well as networking.  Can you help, please?[/QUOTE]
this is a separate issue.  consult the WinmodemLucent wikipage:

[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemLucent](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=WinModemLucent)

---

### Post by katarot on 2006-03-13
ok im now dual booting win xp and ubuntu but still no internet so i been looking ndiswrapper but what one will i choose there to many and i dont want to download them all just to see what one works

---

### Post by ebutton on 2006-03-13
Happy Now to everyone!

If anyone is working a laptop wifi problem, start here:

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

One has to identify the type of hardware chip being used, for instance.

I found that my built-in wireless was automatically detected by Ubuntu 5.10 on a Sony Vaio VGN-S380P, but that a Cardbus wireless card (needed for the external antenna connector) was not.  I got the wireless card to work using ndiswrappers.

I found the WiFiHowTo to be EXTREMELY helpful.

Regards,
EdButton

---

### Post by katarot on 2006-03-14
ok well i got the ndiswrapper of ubuntu install disk and then i downloaded the ngistk burned it to disk then boot up ubuntu and i try to use syanptic to install it 
but it did not pick it up so then i thought i might have to move it to were the ndiswrapper was stored so i tryied this but i get a message saying i dont have the authorizastion to do this i just wanted to know what iam doing wrong and how to correct this
thanks

---

### Post by maxx_730 on 2006-03-14
What do you mean too much different versions? Just do this in a terminal:
sudo apt-get install ndiswrapper-utils
cd (location of windows drivers)
sudo ndiswrapper -i (name of windows driver).inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper 
sudo ifup wlan0
I think that should do the trick.
Ps: try considering dots & alineas for your next posts, it makes things a bit more readable

---

### Post by katarot on 2006-03-14
ok i still cant get the internet to work im going to tell you what iam doing from scratch.
i install ubuntu.
i download r115321.exe from dell and then i extract it to a folder then i get the 
bcmwl5.inf and put it onto a usb flash drive and the same with bcmwl5.sys
then i boot up ubuntu move the DRIVER folder to the desktop and press ctrl alt f1. then i login in again 
and type sudo ndiswrapper apt-get install ndiswrapper-utils . then i get a message saying cannot connect to some address.
the current version is the newest version. i assume it already been installed.
so now i type cd /home/user/desktop/DRIVER so now im in  DRIVER so i type 
sudo  ndiswrapper -i bcmwl5.inf and now i get a message saying
installing bcmwl5.inf and a error message with it 
so i decide i try and finish this to see if it woks so i type this
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
sudo ifup wlan0
it seems to work but then i go to system administration >networks 
my device is not listed here 

i think im on the right path but i dont know were i have went wrong 

im sorry if this is hard to read

---

### Post by Brunellus on 2006-03-14
we need to see those error messages.

---

### Post by katarot on 2006-03-14
ok it will take me a minute or 5 lol i have to shutdown windows and then boot up ubuntu.
btw thanks for all the help on this

---

### Post by katarot on 2006-03-14
it installed but still no internet
i did the exact same thing i did the last time only this time it said 
something then installed 
so i went to system> administration > networks 
nothing change still only ehtheral and the other one 
i went on to ethteral and added my ip masked ip and default gateway again
i came out of it and went and changed from lo to ethol 
i did notice something different the lo had over 1000 packacts and the very first time i turned ubuntu on it was only 20 
im confused to why this didnt work 
i even installed the .sys and the other file i got bcm43xx

---

### Post by katarot on 2006-03-14
i notice something as i boot up ubuntu i get a fail somewere
i think this is because i havent got the internet but im not sure 
well ubuntu still not picking up my card after i installed it have i got to configure it or something

EDIT i think my card is the bcm43xx but on windows it says it is my card is a dell 
i might not have installed it correctly

---

### Post by katarot on 2006-03-15
yes that is the card dell use it in there laptops still cant get internet though here is what iam trying now 

to remove failed attemps 

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

to get the card working 

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

then i go to system > administration > network 
but the only default gateway is the eth0

so i did this 

sudo ndiswrapper l and i detects the hardware 

so why is this not working

---

### Post by Brunellus on 2006-03-15
if the hardware is detected and the driver is valid, you should be OK.  now all you have to do is bring the interface up:

```
sudo ifup wlan0
```

see what that does.

---

### Post by katarot on 2006-03-15
i didnt work arrgghhh 
this is what happend
sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0

---

### Post by katarot on 2006-03-15
well i did this 
martin@martin:~$ iwconfig -a
-a        No such device

martin@martin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

martin@martin:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:22:8E:B7:91
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe8e:b791/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:156677 (153.0 KiB)  TX bytes:156677 (153.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

martin@martin:~$

what do i do from here
is the sit0 mean i have done it or is that ment to be there
im really confused

---

### Post by CookieOrc on 2006-03-15
untill you can install a diver for your wirless card try just using an ethernet cable to connect directly to the router...

---

### Post by katarot on 2006-03-15
arghhh im dying to ubuntu online here is what im doing its copyied exactly from the terminal


martin@ubuntu:~$ sudo apt-get install ndiswrapper-utils
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.7kB of archives.
After unpacking 131kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 56661 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.1-4ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.1-4ubuntu2) ...

martin@ubuntu:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
martin@ubuntu:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
martin@ubuntu:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
>
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
>
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4311:1028:0007.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4311:1028:0008.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:1028:0007.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:1028:0008.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied

---

### Post by katarot on 2006-03-16
ok i think it has been detected i was messing about and i went on to devices 
and there it was broadcom 44 something 
what do i do now if the device is listed in  devices but not on the networrks

---

### Post by katarot on 2006-03-16
ok i disconnected my router and connected directly to my modem just the laptop no other pc connected 
i go on to networks and i see it eth1 so i go to configure enter my ip address and that 
and then change my default gateway to eth1 also 
but still no internet 
what iam i doing wrong 
is it even me or is it my laptop
help please

---

