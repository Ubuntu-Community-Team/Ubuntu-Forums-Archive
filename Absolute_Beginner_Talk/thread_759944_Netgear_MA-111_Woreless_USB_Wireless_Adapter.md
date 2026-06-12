---
title: "Netgear MA-111 Woreless USB Wireless Adapter"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by BeeSharp on 2008-04-19
Hello All, 
Nice forum and lots of information - thank you!

I'm an absolute newbie to Linux. I'm tired Window endless updates and glitches, so I'm experimenting with an old PC where Windows was was so junked up it wouldn't even run. I'm using that old PC now, formated the hard drive Ubuntu in installed and functioning. Nothing else on the drive except Ubuntu. The Internet and Firefox works fine using a direct cable from the network card. Actually a pretty ez and intuitive installation.

I would like to use a Netgear MA-111 wireless adapter. I was able to load the ndis wrapper package and have the Netgear router driver installed. Ubunto doesn't seem to recognize the  wireless adapter. 

How can you get Ubunto to find the USB wireless hardware?

Thanks in advance!
Jim

---

### Post by alan34 on 2008-04-20
Hi Jim

Go (on top bar) Applications - Accessories - Terminal then type or copy and paste this

ndiswrapper -l

should have some output like this only with the name of your usb wireless

net8185 : driver installed
	device (10EC:8185) present

If not the windows driver are not installed properly - post back.

then copy and paste 

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

gksudo gedit /etc/modules

at the end of the file add ndiswrapper on a line on its own - should look like this

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

Restart the computer and look in Network Manager - the two computer icon on the top toolbar on the right, should see a wireless option.

Good luck alan

---

### Post by BeeSharp on 2008-04-22
When I input this: ndiswrapper -l
I get:
netma111 : driver installed

That's the driver for my Netgear MA111 wireless usb adapter. I don't think Ubuntu is seeing the hardware?

I tried this command if that might be helpful?

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:5A:43:4C:9E  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe43:4c9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1537271 (1.4 MB)  TX bytes:260648 (254.5 KB)
          Interrupt:16 Base address:0xdc00 

eth1      Link encap:Ethernet  HWaddr 00:40:F4:6B:17:7A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I'm using the Ubuntu PC on a wired connection now.
Thanks
Jim

---

### Post by gali98 on 2008-04-22
Okay I have this exact card!
So Do this if you haven't already:

```
sudo apt-get install linux-wlan-ng
```
Now I see you have used ndiswrapper.
So do these commands:
```
ndiswrapper -m
ndiswrapper -ma
ndiswrapper -mi

```
now open up /etc/network/interfaces
```
sudo gedit /etc/network/interfaces
```
and add this to it:
```
iface wlan0 inet dhcp
     wireless_mode managed
     wireless_essid your_essid
```
you may need to change wlan0 to wlan1 or something.
Now do 
```
iwconfig
```
and you should see wlan0 or wlan1 on there somewhere.
now do :
```
sudo /etc/init.d/networking restart
```
try your internet now. If it still doesn't work then restart your computer.
I haven't had to configure my card in a while, but since hardy comes out in two days I will learn again. Hopefully these instructions will work perfect though!
Kory

---

### Post by gali98 on 2008-04-22
And when following the instructions above, it would probably be best to disconnect from your eth0 connection (your wired connection). So you might copy and paste instuctions and print out or something.:)
Kory

---

