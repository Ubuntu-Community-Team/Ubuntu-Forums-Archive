---
title: "Cannot connect to the internet"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Rittered on 2007-04-10
I have just downloaded Ubuntu, installed dual boot with windows xp, but I cannot get connected to the internet, apart from one moment when it nearly finished loading a page. 

I have done "ifonfig", "iwconfig" & "lspci". Please help. 


**ifonfig**
Link encap:Ethernet HWaddr 00:1A:4D:20:9F:72
inet addr:58.108.19.135   Bcast:58.108.19.255   Mask:255.255.255.0
inet6 addr: fe80::21a:4dff:fe20:9f72/64  Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:1 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:590 (590.0 b) TX bytes:3389 (3.3 KiB)
Interrupt:177 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.01  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING   MTU:16436   Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:100 (100.0 b)   TX bytes:100 (100.0 b)

**iwconfig**
lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

**lspci**
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Momory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intela Corporation 82801GB/BR (ICH7 Family) LPC Interface Bridge  (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01df (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)

There maybe some typos as I have had to type this out manually, fun o fun. Thanks in advance for the help.

---

### Post by AtrejuT on 2007-04-10
how do you connect to the internet? (e.g. DSL/modem/etc).
If you use some kind of modem is it connected to your computer via USB? or via ethernet? I assume that is the case since you seem to have a working ethernet connection up there.

btw: if you want to copy things from the terminal just select them with you mouse, right click and chose copy. that way you don't have to type it out.

---

### Post by caffienefree on 2007-04-10
Give this guide a try. Your realtek card isn't configured out of the box.

[http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

---

### Post by Rittered on 2007-04-10
I'm trying to connect via ethernet.

---

### Post by Rittered on 2007-04-10
The link to download the realtek driver comes up with "425 failed to establish connection". Which I assume is becuase I'm trying to download it in XP.

---

### Post by eljalill on 2007-04-10
Without being an expert.. it doesn't look like you need a driver to me. After all it is recognised and all..... if I am not mistaken you even have an IP and all.

Do you use a router? can you ping it?

---

### Post by Rittered on 2007-04-10
No I don't use a router.

---

### Post by eljalill on 2007-04-10
Than try pinging google:
```
ping www.google.com
```

---

### Post by Rittered on 2007-04-10
I pinged google and it couldn't find it.

---

### Post by HereInOz on 2007-04-10
If your ping of [www.google.com](www.google.com) doesn't work, then try:

ping 64.233.161.99

If that works, and ping [www.google.com](www.google.com) doesn't, then it is a DNS problem, and you can fix that by setting the DNS servers of your ISP in the DNS section of your Network configuration (System > Administration > Networking.

If neither ping works, then you have no TCP/IP connectivity at all.

---

### Post by caffienefree on 2007-04-10
It's recognized, but not configured. That's what the Realtek Unknown device line tells us.

No, the download site shouldn't have a problem because it's XP.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Then click on the first GO on the line:

Linux driver for kernel 2.4.x and 2.6.x (Support x86 and x64)   1.05	2006/11/27	17k

If that doesn't work, click on the second GO. Failing that, try the third.

---

### Post by jingo811 on 2007-04-10
I dunno the troubleshooting methods the others are talking about but try copy & paste these commands individually into your terminal

```
sudo dhclient eth0
```
```
sudo route add default gw 192.168.0.1
```

Your problem resembles mine, wired NIC works perfectly in Windows XP but gets confused all the time in Ubuntu. 
Try it!  Sadly the fix won't be permanent if it works for you, the best I could do was to make a BASH script for it.  To make typing shorter and easier.

---

### Post by HereInOz on 2007-04-10
I think you are right, caffeinefree.  Note that the ifconfig output shows only TX & RX errors - no actual successful packets.  Thus it is probable that the card has been recognised but has not been configured because the drivers are absent.

If you are wary about installing the drivers, are you able to put another network card in the thing - one that Ubuntu will recognise - like a Realtek 8139 or similar, and get it working that way.

---

### Post by Rittered on 2007-04-10
> **jingo811 said:**
> I dunno the troubleshooting methods the others are talking about but try copy & paste these commands individually into your terminal

```
sudo dhclient eth0
```
```
sudo route add default gw 192.168.0.1
```

Your problem resembles mine, wired NIC works perfectly in Windows XP but gets confused all the time in Ubuntu. 
Try it!  Sadly the fix won't be permanent if it works for you, the best I could do was to make a BASH script for it.  To make typing shorter and easier.

I tried the above and I got SIOCADDART: Network is unreachable...It diddn't work :(

I think that I need to configure follow caffienefree's advice:
> 
[http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)


However the instructions on the linked site aren't very straightforward. I managed after a few tries to sucessfully download the Realtek driver from the Realtek website. 

The first step according to the linked website is:

> Copy the driver folder r1000 and its contents onto the hard disk. Enter into the driver folder and type the following commands.

make clean modules
make install
depmod -a

I'm new to ubuntu, but I assume that means littearlly go into the folder and type "make clean modules" and press enter, then "make install" and press enter, then "depmod -a[/QUOTE]" and press enter. I did this and nothing seemed to happen, I think maybe I did it wrong.

It then directed to:

> Now you need to edit /etc/modules.autoload.d/kernel-<your kernel version> and add the line below to insert the kernel module on boot.

r1000
 

However I don't have that directory. I have /ect/module. I open this file but it read-only. I am very confused.

---

### Post by Rui Pais on 2007-04-10
> **Rittered said:**
> I tried the above and I got SIOCADDART: Network is unreachable...It diddn't work :(

I think that I need to configure follow caffienefree's advice:


However the instructions on the linked site aren't very straightforward. I managed after a few tries to sucessfully download the Realtek driver from the Realtek website. 

The first step according to the linked website is:



I'm new to ubuntu, but I assume that means littearlly go into the folder and type "make clean modules" and press enter, then "make install" and press enter, then "depmod -a" and press enter. I did this and nothing seemed to happen, I think maybe I did it wrong.

I don't get it why you need to build a driver. Your net card should work with the r8169 module (Linux driver)... 
you may check if it's been loaded using the lsmod command:
```
lsmod |grep r81*
``` 
note that if you compile another driver and if r18169 it's loaded it may conflict among them and you may need to blacklist one of them. 

From your 1st post:
> ifonfig
Link encap:Ethernet HWaddr 00:1A:4D:20:9F:72
inet addr:58.XXX.XX.XX Bcast:58.108.19.255 Mask:255.255.255.0
inet6 addr: fe80::21a:4dff:fe20:9f72/64 Scope:Link
it seems to me that you have network, since you got inet addresses.
58.XXX.XXX.XX it's a strange ip... are you sure it's an internal one? do you have static ip or dhcp?
> It then directed to:

 

However I don't have that directory. I have /etc/module. I open this file but it read-only. I am very confused.

Thas because those instructions are for Gentoo, that have a different file tree. Ubuntu one is /etc/modules.

I would first check if it's not a ipv6 or a dns server problem, before build or load extra modules.

---

### Post by Rittered on 2007-04-10
I tried lsmod |grep r81* and nothing happened. I have set the wired network to dhcp.

---

### Post by lamalex on 2007-04-10
58.108.19.135 is an external IP, he said he's directly on a modem. a) buy a router, being directly connected to your modem is very dangerous, you're just asking to get hacked. Specially when you post your ip on a forum! Luckily your IP is dynamic and will be changed in a day or two, but that's plenty of time to get screwed. Sorry this doesn't help your realtek problem, but I don't want you to get hacked!

---

### Post by Rittered on 2007-04-10
Thanks for the concern. I think i need to install the driver, which I have downloaded. The readme file includes the following:

<Quick install with proper kernel settings>

  Unpack the tarball :
	tar vzxf r1000_vX.YZ.tgz

  Change to the directory:
	cd r1000_vX.YZ

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a

Can I make these instructions Ubuntu compatible by adding sudo infront of each line? If not then how do I install the driver?

---

### Post by lamalex on 2007-04-10
that is right just do each with sudo

---

### Post by Rittered on 2007-04-11
I tried to do that but is says that it cannot find the directory. I assume that is becuase it isn't actually on the root of the file system but rather /home/mark. I was unable to save the file on the root of the file system as it said that I did not have permission.

---

### Post by lamalex on 2007-04-11
it doesn't really matter where it is, if it's in your home directory, just cd into it there. cd /home/mark/r1000_vX.YZ and then run make commands

---

### Post by Rittered on 2007-04-11
I tired that. It seemed to install the new driver although I don't know. Anyway, I restarted and it didn't help the connection problem. I turned off my computer and unplugged everything thinking that there may be some settings in the modem or the ethernet card that needed to be refreshed. 

I opened firefox and then turned the modem on and low and behold a page started to load, very slowly. However, by the time the modem had finiished "booting up" the connection had gone again. 

How do I know if the new driver has installed? And are there any other possible problems?

---

### Post by Rui Pais on 2007-04-11
to load the driver (manually) you need to enter on a terminal:
```
sudo modprobe r8169
```
or 
```
sudo modprobe r1000
```

if one of them work and you want to start them automatically just add a line with the one you want to /etc/modules file.

---

### Post by Rittered on 2007-04-11
Niether sudo modprobe r8169 or sudo modprobe r1000 appeared to do anything. Thanks for all your help.

---

### Post by Rui Pais on 2007-04-11
> **Rittered said:**
> Niether sudo modprobe r8169 or sudo modprobe r1000 appeared to do anything. Thanks for all your help.

modprobe should have loaded the modules. If there was no output thats because it was ok.
You can verify/confirm it's loaded with lsmod command, like:
```
lsmod |grep r1000
``` 

After check they are loaded, check whats the output of lspci

And what the output of:
```
cat /etc/network/interfaces
```
(if it contains an ip adress started by anything else other then 10.x.x.x or 192.x.x.x don't post it here for your security, just replace the numbers for xxs characters)

---

### Post by lamalex on 2007-04-11
they don't give any output. lsmod i believe should tell you if they worked.

---

### Post by fanny on 2007-04-11
ask me a private messgae i will try to guide to you today

---

### Post by heimo on 2007-04-11
Please, if possible, try to keep discussions public, so that the next person who has the same problem, can find answer using search.

---

