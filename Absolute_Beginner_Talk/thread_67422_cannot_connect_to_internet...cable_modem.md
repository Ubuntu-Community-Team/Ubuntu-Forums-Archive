---
title: "cannot connect to internet...cable modem"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by listen on 2005-09-20
Hi!

Need help in setting internet connection:-
 
I have downloaded and installed Ubuntu 5.10 and am trying to connect the cable modem (motorola surfboard SB51001) thru the PCI ethernet card.

I have tried to read many forums for solutions but i dont seem to get it...

ok, the results of "ifconfig" is as follows:-

eth0      Link encap:Ethernet  HWaddr 00:C0:26:8D:D7:52
          inet6 addr: fe80::2c0:26ff:fe8d:d752/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:522612 (510.3 KiB)  TX bytes:2772 (2.7 KiB)
          Interrupt:10 Base address:0x9400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16712 (16.3 KiB)  TX bytes:16712 (16.3 KiB)

I have also checked thru the "Systems->administration->networking" and under the "connections" tab, there are 2 entries:-
Ethernet connection - the interface eth0 is active
Modem connection - the interface ppp0 is not configured

my com specs are:-
Motherboard: Aopen AX6BC Pro Pentium II 100 Mhz BIOS ver 1.6
Processor: Intel Celeron 400 Mhz
Ram             : PC100 SDRAM 256MB
Graphics card: 16 MB Riva TNT2 Creative
Sound card: Vibra128  Creative
Harddisk: 8.5Gb Quantum
Casing : 230 W ATX 
CD Drives: 1 X TDK CD-RW 40/12/48 and 1 X CD-ROM
Floppy Drive: 1
Ethernet card: 1 X PCI

thanks in advance

---

### Post by tomcogley on 2005-09-22
Here's something that may help.   Click, in gnome, on the top bar, applications, and then system tools, then click on network tools and network tools will open. And then on top of this app there will be a scroll down device menu, click on it and click on eth0,  the other boxes will activate so you can click on activate this module or activate eth0.  Click on activate it and the close the network tools.  Then you will want to reboot.  Log into gnome and start firefox.  You should have a connection.      tc  ps:  I did this a few times when upgrading a good deal of base system stuff from a breezy preview cd, and find that I lost my connection...actually I rebooted a few times, and did not get a connection until I found the system tools > network tools >activate eth0, and activated it and then restarted yet again...then I had internet.

---

### Post by listen on 2005-09-22
Hi TomCogley,

Thanks for your help...appreciate it..

I had the problem solved thru another posting(after trying out more things and added more results) later...my problem was actually not initializing the cable modem. I was actually switching the ethernet cable between my notebook(XP) and the linux desktop...by unplugging from the notebook, we need to initialize the modem by reppowering it up again...before rebooting linux...
i thoughtt since the signals coming from the cable is the same, all i had to do is reboot the desktop....well it took an advice from another user who questioned me b4 i found out my problem...all thanks to kind folks like yourself and him, SilentCacophony that i am staying on to Linux....it is my second time converting actually..

Thanks once again and happy posting..

regards
listen

---

### Post by jmax on 2005-09-24
[QUOTE=listen]Hi TomCogley,

Thanks for your help...appreciate it..

I had the problem solved thru another posting(after trying out more things and added more results) later...my problem was actually not initializing the cable modem. I was actually switching the ethernet cable between my notebook(XP) and the linux desktop...by unplugging from the notebook, we need to initialize the modem by reppowering it up again...before rebooting linux...
i thoughtt since the signals coming from the cable is the same, all i had to do is reboot the desktop....well it took an advice from another user who questioned me b4 i found out my problem...all thanks to kind folks like yourself and him, SilentCacophony that i am staying on to Linux....it is my second time converting actually..

listen[/QUOTE]

I can attest to this simple and elegant solution. Having been a windows user since the days of Windows V1 ... whatever the hell it was called ... Linux is somewhat a strange beast indeed. I could never get Linux to connect to the net ... this solution is rather pleasing and straightforward. 

I turned the motorola surfboard modem off, booted Ubuntu and then while the boot up sequence for the o/s was doing its thing, turned on the cable modem. It just worked. Wonderful!

Much better than messing about with code. 

John

---

### Post by jmax on 2005-09-24
Alas, I have found that the connection drops out after about 15 mins. 

It does seem to be a problem with initiatlizing the modem tho. Ubuntu recognizes that there is an ethernet connection but the transaction rate ... if that is a way to describe it ... is very slow. The thing, is that this sort of thing happens in windows if you don't load the drivers for the modem {motorola surfboard}. 

I have two hd's, one has Linspire on it ... which works beaut and ubuntu on the other. Ubuntu is faster when loading things like Open Office, or the Internet suites it has. Linspire is very functional ... but i really would love to get Ubuntu connected to the net instead of changing hd's all the time. 

Perhaps one has to resort to some very clever code after all. 

Thanx in anticipation for any help. 

John


John

---

### Post by listen on 2005-09-24
Hi John,

Glad u did the crossover..

for my case, i have had no probems with connections thru the Moto Surfboard since i managed to get it going....for a few days already... i even downloaded updates for Breezy the whole night, as i was worried that my ISP do an auto-reset...
 
no idea what is the prob....as i am a newbie too... but just to let u know that i have no such prob...

hope this helps..

---

