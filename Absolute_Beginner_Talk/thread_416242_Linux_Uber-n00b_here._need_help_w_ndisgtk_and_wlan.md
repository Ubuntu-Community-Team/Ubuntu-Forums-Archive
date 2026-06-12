---
title: "Linux Uber-n00b here. need help w/ ndisgtk and wlan"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by ArmyofKirb on 2007-04-20
First of All,

Thanks for even reading this  post. I just installed ubuntu 7.04 on my old laptop. I love the idea of open source and independence from Microsoft.

I am having trouble getting my wlan to work. My Wireless card, a BCM4306, is detected by the network manager, and I'm able to enter the ESSID and hex key of my network. I attempt to activate it, and I  get the activating window, but thats the extent of it. No connectivity. I can't even connect directly with the router.

So I have to ask these questions: How can I tell if my driver for the wireless card is present and installed? If its not installed, I know that ubuntu comes w/ ndisgtk but I don't know how to access it. (Spoon-fed by Windows for 20+ years) How do I access ndisgtk?

Lastly, is there a progra m I can use to show available wireless networks in a gui? 

As a n00b to Linux, I promise that I will make every effort to read up on it and become more familiar with it so that I can A) become independent of help from others, and B) start to help people myself.

Thanks in advance,

Kirb

---

### Post by al1b1 on 2007-04-20
About the wireless problem i reccomend you disconnect and then recconect your adapter. Network manager use roiaming mode which allows you to see all the networks detected

---

### Post by jiminycricket on 2007-04-20
*sigh* Broadcom...these are reverse engineered drivers and the only ones available for Linux, official or not...long story.  They don't work with all cards yet.  They also need firmware for the actual card, AFAIK.

Anyhow, try installing (sudo aptitude install bcm43xx-fwcutter) and then reboot and see what happens.

---

### Post by ArmyofKirb on 2007-04-21
Here's what I get when I do that:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "bcm4306-fwcutter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
kirb@kirb-laptop:~$

---

### Post by ArmyofKirb on 2007-04-21
> **al1b1 said:**
> About the wireless problem i reccomend you disconnect and then recconect your adapter. Network manager use roiaming mode which allows you to see all the networks detected

I'm sorry, but I can't seem to figure out how to enter "roaming mode" I open up network settings, and it has my three devices: my wireless card, my ethernet card (which works beautifully), and my modem. I know that my home has about 5 or 6 wlans around it, so if I can figure out how to see them, maybe I don't have a driver issue.

Thats my problem, I am too nooobish to figure out if I even have a driver problem. According to broadcom, they include some linux drivers in the latest kernel.

I have to ask, what do you mean by disconnecting and reconnecting my adapter? Do you mean through device manager?

Thanks,

Kirb

---

### Post by Pobega on 2007-04-21
Post the output of these commands:

```
sudo ifconfig
sudo iwconfig
sudo lspci | grep Network
```

---

### Post by ArmyofKirb on 2007-04-21
> **Pobega said:**
> Post the output of these commands:

```
sudo ifconfig
sudo iwconfig
sudo lspci | grep Network
```


here's sufo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0B:CD:8A:24:9F  
          inet addr:192.168.1.46  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe8a:249f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5781016 (5.5 MiB)  TX bytes:406422 (396.8 KiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

kirb@kirb-laptop:~$ 

kirb@kirb-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"R"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:364B-5653-38   Security mode:open
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kirb@kirb-laptop:~$ sudo lspci | grep Network
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireles

Thanks,

Kirb

---

### Post by Pobega on 2007-04-22
It looks like your wireless card is working then.

Try a quick "iwlist eth1 scan" and see what comes out. Post back here and then I'll show you how to connect to your wireless network.

You also might want to tell me which network is yours, and if you have a WEP pass or not.

---

### Post by ArmyofKirb on 2007-04-22
> **Pobega said:**
> It looks like your wireless card is working then.

Try a quick "iwlist eth1 scan" and see what comes out. Post back here and then I'll show you how to connect to your wireless network
You also might want to tell me which network is yours, and if you have a WEP pass or not.


Here's the results:

kirb@kirb-laptop:~$ iwlist eth1 scan
eth1      No scan results
kirb@kirb-laptop:~$ 

I guess that means no available wireless networks, right? That's strange because I have 5+ networks available right in my townhouse. I have my own , which my desktop uses (w/ windows XP) and bunch of wlan's the belong to my neighbors. Might my problems be because of my drivers after all?

---

### Post by jiminycricket on 2007-04-22
> **ArmyofKirb said:**
> Here's what I get when I do that:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "bcm4306-fwcutter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
kirb@kirb-laptop:~$

You need the universe repository enabled in Synaptic, under Tools->Repositories

---

### Post by ArmyofKirb on 2007-04-22
> **jiminycricket said:**
> You need the universe repository enabled in Synaptic, under Tools->Repositories

Ok, I went to **System>Synaptic Package Manager>Settings>Repositories**. I then enabled the universal repositories, like you said. I entered:  iwlist eth1 scan again, and got the same result.e

I went back to Network Manager, and this may have been here b4, but I found the roaming check box and checked it. I ran the iwlist eth1 scan one more time, but still no luck.

P.S. Thanks again for all your help guys. I'm looking for a good linux tutorial/manual for beginners, any suggestions?

Kirb

---

