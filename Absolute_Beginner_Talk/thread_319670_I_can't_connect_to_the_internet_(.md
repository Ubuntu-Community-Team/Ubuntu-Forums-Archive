---
title: "I can't connect to the internet :("
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by misfito on 2006-12-16
HI. I'm really unhappy since I had to reinstall ubuntu on my other machine days ago...
I did it because the system started mallfuctioning since I moved to my new house days ago, first it started to freeze and I had to reset it a couple of times, then after a forced restart the system didn't wanted to boot after several tries and it gave only a message that said GRUD GRUD.
 I reseted it again ending with the same GRUD  message. After that I reseted my motherboard, unhooked and pluged back my hard drive. But none of that worked so I decided to go with a reinstallation of the system :( .
The same day this happened I had a visit from the cable company, they came to install my service.
I reinstalled the system :) everything worked just fine. BUT I WASN'T ABLE TO CONNECT TO THE INTERNET.
I didn't say nothing to the cable guy because I didn't tried to connect with that computer when he was here.
He plugged my other computer (the one I'm using right now) thru a ethernet cable.
I had DSL before and I used to have both computers connected all the time. But when I moved here I had to get another internet provider because the old company I had didn't cover this area. Good thing is I have a faster connection now.
But anyways, when I installed Ubuntu for the first time (not to long ago), I remember that I just had to plug the ethernet cable to the system and that was all.  I could connect right away.
Now is different, I plugged the USB cable to the system (the cable modem has two choices ethernet and USB) And I tried to connect with no success :(, then I unplugged the other computer to use the ethernet cable, I plugged this one too, to my system, but with the same results...
I'm not sure if I have to call my internet provider, I wanted to ask for advice here before, to see if there's any work around.

I'm using: UBUNTU 6.06
                Soyo Motherboard  p41875
                2.8 GHz pentium 4  
                512 DDR memory
                
                modem> Ambit U10C018 (picture below)
[IMG]http://www.simplehelp.net/images/cable_modems/ambit_u10c018.gif[/IMG]

---

### Post by padre999 on 2006-12-16
Did you have a look at this? [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html)

---

### Post by hyper_ch on 2006-12-16
Please go to your System Administration --> Network menu and check if ethernet is actually activated.
If it is, then see whether the properties are set to DHCP.

If that is also true, please turn off the modem and your computer and turn both on again.

Once booted up, check if you have an internet connection.

If not, please post the output of

```

ifconfig

```

here.

P.S.: I don't think you can operate the USB and ethnet port at the same time on that modem.

---

### Post by misfito on 2006-12-16
> **sjau said:**
> Please go to your System Administration --> Network menu and check if ethernet is actually activated.
If it is, then see whether the properties are set to DHCP.

If that is also true, please turn off the modem and your computer and turn both on again.

Once booted up, check if you have an internet connection.

If not, please post the output of

```

ifconfig

```

here.

P.S.: I don't think you can operate the USB and ethnet port at the same time on that modem.


ifconfig gave me this:

```
user@My-linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:2C:09:7D:72
          inet6 addr: fe80::250:2cff:fe09:7d72/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:93978 (91.7 KiB)  TX bytes:2914 (2.8 KiB)
          Base address:0x9000 Memory:f8000000-f8020000

eth1      Link encap:Ethernet  HWaddr 00:16:CF:05:38:BF
          inet6 addr: fe80::216:cfff:fe05:38bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1157611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:54065822 (51.5 MiB)  TX bytes:442332 (431.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:360104 (351.6 KiB)  TX bytes:360104 (351.6 KiB)
```

---

### Post by kvonb on 2006-12-16
What country are you in?  I see that you only have an IPv6 number on your ethernet interfaces which is very odd unles you are in Japan!

It looks to me like your computer is not getting an IP address assigned by the modem, you need to ring the ISP and ask them if the modem is supposed to assign an IP address or if you have to set it manually.  If auto, then go into network properties and change the ethx device (whichever is connected to the modem) to "assigned by DHCP", if manual then they should tell you what the number should be.

Alternatively look at the documentation that came the modem, it should tell you that.

You said your computer started acting funny, check the disk drive for errors
, the move might have damaged it.  Also look on the mainboard at the capacitors, if the tops of any are rounded or bulged then they need replacing or you need a new mainboard, it is very common.

Ultimately I suggest you talk to your ISP and ask them how it is supposed to connect.

One last thought, you need a crossover network cable to connect the modem to the ethernet port, they did supply one didn't they?

Rgds, KEv :)

---

