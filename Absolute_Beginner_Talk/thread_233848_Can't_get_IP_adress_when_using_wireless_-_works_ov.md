---
title: "Can't get IP adress when using wireless - works over Ethernet only"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Johnjkle on 2006-08-10
Hi All,

I'm new to Ubuntu and Linux in general, but I'm loving Dapper so much already that I've replaced Windows with it on one of my laptops - a Sony VAIO T2XP. The laptop is a Centrino and uses the Intel 2200BG wireless chipset - Dapper detected this out of the box and it worked fine for the last few weeks. However, my Linksys WAG54G all-in-one router/ADSL modem is on the way out and the wireless on it is going kind of flaky (I can tell from the results with my Windows systems). 

I have a second broadband connection at home, using a generic cable mode supplied by the provider and I bought a D-Link DWL-G700AP access point to add wireless capability to this. I have a DELL laptop running Windows XP currently connected to that and it gets its' IP via DHCP. The problem is on my Ubuntu VAIO - I can connect over my wired ethernet just fine (I'm actually typing on it right now) and DHCP works. However, when I use the wireless, I can connect to the D-Link AP and get a strong signal, but I cannot reach anything and the wireless card never gets an IP over DHCP. Assigning a static IP also has no effect.

Problem is, it also doesn't work with my older Linksys router (which it sometimes worked with before) anymore, though that could just be the router so I'd keep it out of the equation for now.

Here's what I see in iwconfig:

eth1      IEEE 802.11g  ESSID:"DLinkJK"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:32:8F:CC
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/100  Signal level=-54 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:12

And in ifconfig for the wireless card:

eth1      Link encap:Ethernet  HWaddr 00:13:CE:1B:E6:1E
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:18 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x2000 Memory:e0206000-e0206fff

So obviously, there's no IP but I don't know why - as I said DHCP works for the wired connection but not for the wireless. Static also does not work for the wireless - I just can't get an IP. If I'm missing any output that I am not yet aware of, please let me know and I'll post that up. Thanks in advance.

---

### Post by nalmeth on 2006-08-10
I wish I knew more 'down and dirty' details about how to configure wireless, but it's been so long since I've had to deal with it.

Click wireless help in my signature, perhaps that guide will help you, if you haven't already seen it.

---

### Post by stricevics on 2006-08-10
> **Johnjkle said:**
> Hi All,

So obviously, there's no IP but I don't know why - as I said DHCP works for the wired connection but not for the wireless. Static also does not work for the wireless - I just can't get an IP. If I'm missing any output that I am not yet aware of, please let me know and I'll post that up. Thanks in advance.

Can you ping anything (including the router)? Can you get into the web-config utility of the router?
Do you have MAC filter enabled on the router? Do you have security (WEP, WPA, WPA2) enabled on the router?

---

### Post by Johnjkle on 2006-08-10
@ nalmeth - I'll take a look at that guide as soon as I get a chance, thanks.

@ stricevics - I can't ping the AP, no. The only thing I can ping is loopback - 127.0.0.1 and nothing else when the wireless is up. The AP is set up with MAC filtering (doublechecked the Sony's card is in the allowed list though) and WEP 64 bit hex, open authentication. I already tried without WEP, to no avail.

---

### Post by tehnad on 2006-08-10
Just a quick question.  Isn't your wireless card ath0 when you do ifconfig or is that only the address for internal wireless cards like mine?  When I do an ifconfig I get ath0 for wireless and eth0 for my hard wire.

edit: I also get this when I do an iwconfig.  What is the difference?

---

### Post by Johnjkle on 2006-08-10
tehnad, I'm afraid I have no idea what the difference is between ath0 and eth0 - my wired ethernet is eth0 and the wireless is eth1 (which as you see in the original post, is built into the system anyway, as this is a Centrino laptop). With a PCMCIA wireless card installed, the listing for it becomes wlan0 instead, I think (haven't used one in awhile).

---

### Post by Papa-san on 2006-08-10
Actually, from what you posted as results from iwconfig and ifconfig shows that both of them are 'eth1' I am really no expert, but from my experience, this isn't going to work... Maybe I'm wrong, but it just seems that I had a similar problem back when I installed breezy...

---

### Post by Johnjkle on 2006-08-11
Both of what? If I understand correctly, ifconfig and iwconfig can show different information about the same adapter. I posted the ifconfig output for eth1, not eth0 (which is the wired adapter) and the same for iwconfig (though in that case, since eth0 is wired, there is no info for it in the iwconfig output to begin with). And it did work like this before: eth1 will be seen in both if/iwconfig, though iwconfig gives all the specific wireless info like type of connection, signal, access point, etc.

BTW, sudo dhclient eth1 results in a "NO DHCP OFFERS" error message...

---

### Post by stricevics on 2006-08-11
> **Johnjkle said:**
> Both of what? If I understand correctly, ifconfig and iwconfig can show different information about the same adapter. I posted the ifconfig output for eth1, not eth0 (which is the wired adapter) and the same for iwconfig (though in that case, since eth0 is wired, there is no info for it in the iwconfig output to begin with). And it did work like this before: eth1 will be seen in both if/iwconfig, though iwconfig gives all the specific wireless info like type of connection, signal, access point, etc.

BTW, sudo dhclient eth1 results in a "NO DHCP OFFERS" error message...

Can you try this:

1. Turn off WEP

2.

```
# sudo ifconfig eth1 down
# sudo iwconfig eth1 essid "DLinkJK" rate auto mode managed key off
# sudo dhclient eth1
```

If that doesn't work, post the output and will try some other methods.

Hope it helps,

St.

---

### Post by Johnjkle on 2006-08-12
Thanks - I already tried WEP off and it didn't work.

However, as is usually the case, I think this my own stupidity here and nothing to do with Ubuntu...

Like I said in the first post, I'm using my cable modem connected to an access point and the AP is set to DHCP. The Windows XP laptop permanently connected to the AP has worked without a problem... I took a closer look at its' settings and noticed the IP (even though assigned by DHCP) was in the format 89.xxx.xxx.xxx - as some of you can probably tell, that's an external WAN address and not an internal IP handed by the AP (which should be in the format 192.168.1.xxx according to how I've set the DHCP on the AP). 

I checked out some FAQ pages for the cable modem and the provider lists something about it handing out only a single IP address to one PC - which I guess makes some sense: the modem is as basic as you can get - only one LAN connection on it and the cable input, nothing else.

Since then, I've managed to connect my Ubuntu VAIO to the original Linksys router (which as I said works whenever it feels like it...) so this assures me that there is nothing screwed up on the Ubuntu side...

I'm no expert in network settings even in Windows, but I think the issue is with the cable modem only handing out a single IP address and the DHCP on the AP can't do anything about it - hence, only a single system can be connected at a time.

Seems like I'm still stuck given what I set out to do (replace the failing Linksys but on my cable connection instead of the ADSL) but again, seems I have been unfair to blame Ubuntu for this, as the problem is simply not with the OS. I guess this is pretty common: for us Linux newbies to blame the system we don't fully understand yet for everything that goes wrong... ;) 

So, thanks to everyone for the help and suggestions - it's very encouraging as an Ubuntu newbie to see that the community support is indeed there and not just hype.

---

### Post by stricevics on 2006-08-14
> **Johnjkle said:**
> 

I'm no expert in network settings even in Windows, but I think the issue is with the cable modem only handing out a single IP address and the DHCP on the AP can't do anything about it - hence, only a single system can be connected at a time.



You are given only one IP address by your ISP.

This is the order of connections:

Cable Modem -> AP -> Computer

AP is the critical element in this layout as it is capable of sharing that one connection (address) over several computers. There are two basic things that AP needs to be set up regarding IP addresses. First part is your ISP. Basically, you are telling your AP how are you connectiing to the internet. Use the IP supplied by your ISP in this section.

Second part is your local (house) network. It is separate from your cable modem in the IP address sense. For your convenience, you can set up DHCP Server on the AP itself. The benefit of such a thing is that you don't have to go around and setup each and every computer with its own IP address. Just set everyone to "Obtain IP address automatically" and you are set.

From now on, your AP should be connected through the cable modem on internet, and you will be able to connect to internet through your AP.

So, to wrap it up:

1. Put WAN address in AP's internet connection section
2. Put LAN addresses (DHCP) for local network

Hope this all makes some sense. :)

---

