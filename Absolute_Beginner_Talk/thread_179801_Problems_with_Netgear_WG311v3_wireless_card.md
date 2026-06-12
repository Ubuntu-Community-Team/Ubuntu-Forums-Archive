---
title: "Problems with Netgear WG311v3 wireless card"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Kilgore_Trout on 2006-05-20
Hi all, 

New to Ubuntu (and linux overall) and after a successful install of Breezy, I've come to my first speedbump...

I have been reading over the wiki regarding wifi, networks, ndiswrapper, etc. but with no luck.

I have a Netgear WG311v3 PCI card installed in the computer, but it does not display in Network Settings or ndisgtk.

The output from sudo lshw -businfo reads:

pci@00:0f.0            network        Marvell Technology Group Ltd.

sudo lshw -C network shows:

 *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: f
       bus info: pci@00:0f.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       resources: iomemory:f4010000-f401ffff iomemory:f4000000-f400ffff irq:3

But from iwconfig I get:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

(eth0 is my wired NIC, not sure what sit0 is)

Anyways, I am somewhat confused as to whether the system can see my wireless card or not.

Any help would be appreciated, if you have come across something similar or if I am just not grasping the concept at work here (very possible).  TIA

---

### Post by macdo on 2006-05-20
Can you post the output of ```
ifconfig -a
```

---

### Post by Kilgore_Trout on 2006-05-21
This is what I get from ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:50:DA:10:96:1C
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe10:961c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14140 errors:5 dropped:0 overruns:0 frame:5
          TX packets:11627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14606429 (13.9 MiB)  TX bytes:1563313 (1.4 MiB)
          Interrupt:11 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:668466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53020332 (50.5 MiB)  TX bytes:53020332 (50.5 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by Koech on 2006-05-21
Hello, I'm a newbie in this but I also had the same problem with a RaLink card I have, but when I used Dapper Drake(Ubuntu 6.06 Beta2) I could see my wireless recognised. Therefore if you don't mind, just install Dapper.
Good Luck!

---

### Post by macdo on 2006-05-21
Here's a quick howto:

1) Remove any prior ndiswrapper on your PC```
sudo apt-get remove --purge ndiswrapper
```
2) Get the drivers for WinXP for your card: download [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip) and extract WG311v3.INF and WG311v3XP.sys (if it doesn't work, you might need to try WG311v3.sys, but don't extract it yet) from the Windows 2000 folder. Put them in a folder in your home directory called wg311v3
3) Install Ndiswrapper: ```
sudo apt-get install ndiswrapper-utils
```
4) Install the drivers: ```
cd wg311v3
sudo ndiswrapper -i WG311v3.INF
```
5) Load ndiswrapper into the kernel: ```
sudo modprobe ndiswrapper
```
6) Run ifconfig -a to see what your wireless card is called: probably wlan0, but it might be eth1 or even ath0. We'll call it wlan0 for the moment: if it's something else, you'll need to replace wlan0 with the something else for the rest of this howto.
7) Turn off your Wired Ethernet card: ```
sudo ifdown eth0
```
8 ) Scan for wireless networks: ```
sudo iwlist wlan0 scan 
```
9) Configure your card: ```
sudo iwconfig wlan0 channel X essid ESSID mode Managed 
``` The X and the ESSID are to be replaced by the values you found at step 8. Make sure you've turned off any encryption, for the moment at least. 
10) Start up your wireless card: ```
sudo ifup wlan0
``` If that tells you that the card is already running, do ```
sudo ifdown wlan0
sudo ifup wlan0
```
11) Ping Google to see if it works (the -c 1 just makes it ping once - we're not trying to flood them): ```
ping -c 1 www.google.com
``` The screen should print something like this: ```
PING www.l.google.com (66.102.7.147) 56(84) bytes of data.
64 bytes from 66.102.7.147: icmp_seq=1 ttl=241 time=178 ms

--- www.l.google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 178.060/178.060/178.060/0.000 ms
```

Hopefully, that should be it.

---

### Post by Kilgore_Trout on 2006-05-21
Thanks to you both for your help.

Unfortunately, I can't seem to get past step 5 in your post.

I removed ndiswrapper-utils, added the WG311v3.INF and Wg311v3XP.SYS files to a directory named wg311v3 in my home directory, and reinstalled ndiswrapper-utils.

When I go to install the drivers, I get the message:

```
mfracassini@ubuntu:~$ cd wg311v3
mfracassini@ubuntu:~/wg311v3$ sudo ndiswrapper -i WG311v3.INF
wg311v3 is already installed. Use -e to remove it

```

Tried to use ndiswrapper -e to remove and reinstall, but no luck.

Then when I tried to load ndiswrapper into the kernel I got:

```
mfracassini@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

Any hints as to what could be going on?

---

### Post by Kilgore_Trout on 2006-05-22
Nevermind the post above...

I had been trying to use ndiswrapper with the drivers from the install CD that came the wireless card.

Using the drivers from the website worked fine, and the rest of the steps were basically a cakewalk.

Thanks again.

---

### Post by Chris Val Kef on 2006-09-12
got the same problems... can't install my wg311v3 wireless card...

at step 5 for 
modprobe ndiswrapper 
i get the message : FATAL: Could not open '/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': no such file or directory

but i get nothing for modprobe usbcore (according to some other directions saying to try it too)

can someone help me? 

for ndiswrapper -l everything is ok (wg311v3 driver present, hardware present)

in device manager the card is shown as '88w8335[Libertas]802.11b/g Wireless'
and in networking there's nothing...

---

### Post by :::mL::: on 2006-11-14
try with new ndiswrapper drivers -> version 1.28

it's worked for me  :)

(but first you should download and install "linux-headers" (you need those for compilling new drivers)

---

### Post by galligator on 2006-11-21
hey guys i cant get past the second step i need help!!! i dont understand when to extract it and how to put it into a home folder?!! 

thanks,
brad

---

### Post by lavaramano on 2006-12-23
@macdo: 
thanks a lot for your help. 
now i have mi wifi card working just perfect. :KS

lucks

---

### Post by David Colton on 2007-02-05
Thanks for the great support and insightful and informative posts here. Thanks to this thread I managed to go from XP to Ubuntu in 2 sitting [the 2nd sitting was after picking up this thread in work today].

This is another complete nubie question. I've got my Netgear WG311v3 up and running [I'm writing this on the aforementioned machine at home] but the setting are not permanent. Everytime I reboot I loose my wlan0 setting.

I know I'll feel dumb when I see the answer. Maybe it's late but at the moment this is totally eluding me.

David.

---

### Post by shmatt on 2008-04-03
I'm having the exact problem that David is having. It's driving my crazy. Anyone have any suggestions?

---

### Post by acirilo on 2008-07-09
> **David Colton said:**
> Thanks for the great support and insightful and informative posts here. Thanks to this thread I managed to go from XP to Ubuntu in 2 sitting [the 2nd sitting was after picking up this thread in work today].

This is another complete nubie question. I've got my Netgear WG311v3 up and running [I'm writing this on the aforementioned machine at home] but the setting are not permanent. Everytime I reboot I loose my wlan0 setting.

I know I'll feel dumb when I see the answer. Maybe it's late but at the moment this is totally eluding me.

David.

echo ndiswrapper >> /etc/modules

---

### Post by Gorromog on 2008-07-16
I have followed the instruction up to point 6. Even though I reinstalled ndiswrapper, and tried using the Windows 98 and Windows XP drivers, it still says network unclaimed. I am completely lost as to what to do next, and it is somewhat ruining my linux experience.

---

### Post by FoxJT on 2008-07-24
Hi,

I am a newbie here and have just loaded an Ubuntu distro (2.04?)which looks really good.
I have a Netgear WG311v3 and after struggling through the above set up, and other threads, I can now communicate with the outside world; always a good thing!

The problem I have is that when I shut down Linux and then reboot, the comms has failed.  However, once I issue the command "sudo modprobe ndiswrapper" it all springs into life again.

What step could I have I missed in the installation?

I am currently at work and the Linux is on my home PC so I am relying on memory, not such a good thing :(.

I did note that the "ifup" and "ifdown" commands gave an error along the lines of "no such device?".

If more info needed let me know.

Thanks,

JT

---

### Post by jniblick on 2008-07-24
Whenever I try to install anything it gives me an error message saying,"Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/il8n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/il8n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'. Can you please help I was trying the steps listed above and when I tried to install anything it gave me the error message.

---

