---
title: "Installed Ubuntu...can't get internet"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by bob_gates on 2007-01-21
So I'm new to linux conpletely and heard Ubuntu is a good place to start. First I'll list my computer specs if it helps.

EVGA 680i mobo (dual ethernet)
e6300
EVGA 7900GTO
250gb SATA- Windows
160gb IDE- Ubuntu

I installed linux everything went pretty smooth, excpet I couldn't boot up without taking my processor to stock speeds(from 3ghz abck to 1.8ghz). Now everything boots ok and seems to run fine but I can't get the internet to work. In the network tools it shows both of my network adapters, and that they are connected (I think?). I have Bellsouth DSL and a D-Link WBR-2310 router.

Thanks for the help in advance and hopefully I can get this working Im excited to get away from windows.

---

### Post by riven0 on 2007-01-21
Hey, can you tell us what wireless card you've got? You may need ndisswrapper and the official drivers.

---

### Post by Shatrat on 2007-01-21
I have no problems with my overclocked PC in linux, perhaps your o/c wasn't stable?

In the Network Settings app in the System menu are your adapters set to use DHCP to get their address?
Could you post the results of running ```
ifconfig
``` in a terminal for me?
{edit}
> Hey, can you tell us what wireless card you've got? You may need ndisswrapper and the official drivers.
I don't see anything about wireless, I assume he is just using ethernet. Probably the onboard provided by his motherboard since he specified that it has dual ethernet.

---

### Post by bob_gates on 2007-01-21
> **Shatrat said:**
> I have no problems with my overclocked PC in linux, perhaps your o/c wasn't stable?

In the Network Settings app in the System menu are your adapters set to use DHCP to get their address?
Could you post the results of running ```
ifconfig
``` in a terminal for me?
{edit}

I don't see anything about wireless, I assume he is just using ethernet. Probably the onboard provided by his motherboard since he specified that it has dual ethernet.

The O/C was stable in windows for weeks. You are correct, using onboard ethernet. It is set to DHCP. I will try the ifconfig.

---

### Post by Shatrat on 2007-01-21
Just because it didnt crash doesnt mean it's stable.  A few bits off here or there in a jpeg wont produce any noticeable difference, most errors go undetected.  
Unless you run prime95 or something similar for hours (or days) then you can't really say it is stable.  I can get another 200 mhz out of my processor and still boot, but get an error after testing for 2-3 hours.

---

### Post by bob_gates on 2007-01-21
> **Shatrat said:**
> Just because it didnt crash doesnt mean it's stable.  A few bits off here or there in a jpeg wont produce any noticeable difference, most errors go undetected.  
Unless you run prime95 or something similar for hours (or days) then you can't really say it is stable.  I can get another 200 mhz out of my processor and still boot, but get an error after testing for 2-3 hours.

I know the processor is stable. I have used, prime95, memtest, superpi, and gamed on it for 3 weeks now. It's stable.

Here are the results.
ryan@ryan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:4B:01:01:21  
          inet6 addr: fe80::204:4bff:fe01:121/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:04:4B:01:02:72  
          inet6 addr: fe80::204:4bff:fe01:272/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39020 (38.1 KiB)  TX bytes:39020 (38.1 KiB)

ryan@ryan-desktop:~$

---

### Post by crane on 2007-01-21
if you have 2 ethernet connections be sure to try both.
When you swap the cable try bringing them down and back up.
Use the command
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
or eth1 depending on which you have it hooked in.
Then just type ```
ifconfig eth0 (or 1)
```
this should show your IP if it aquired one.
example below, I highlighted IP in red:
```
jason@edgy:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:D8:EE:63:06  
          [COLOR="Red"]inet addr:10.104.1.106[/COLOR]  Bcast:10.104.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feee:6306/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2629306 (2.5 MiB)  TX bytes:732851 (715.6 KiB)
          Interrupt:201 

```

---

### Post by bob_gates on 2007-01-21
> **crane said:**
> if you have 2 ethernet connections be sure to try both.
When you swap the cable try bringing them down and back up.
Use the command
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
or eth1 depending on which you have it hooked in.
Then just type ```
ifconfig eth0 (or 1)
```
this should show your IP if it aquired one.
example below, I highlighted IP in red:
```
jason@edgy:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:D8:EE:63:06  
          [COLOR="Red"]inet addr:10.104.1.106[/COLOR]  Bcast:10.104.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feee:6306/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2629306 (2.5 MiB)  TX bytes:732851 (715.6 KiB)
          Interrupt:201 

```

I have both ethernet ports connected to my router. I have tried each one alone and also tried wiring straight to the modem. Still no luck.

---

### Post by Shatrat on 2007-01-21
Well, neither one has an inet address.
The chipset is obviously pretty new and I've been poking around and haven't found much info so far.
I poked around and found these threads on the nvidia forums which seem to match your problem.
[http://www.nvnews.net/vbulletin/showthread.php?t=82151](http://www.nvnews.net/vbulletin/showthread.php?t=82151)
[http://www.nvnews.net/vbulletin/showthread.php?t=79917](http://www.nvnews.net/vbulletin/showthread.php?t=79917)

Long story short, it's the bios reporting capabilities the hardware doesn't actually have.
Apparently a bios fix is in the works but try adding

```
options forcedeth msi=0 msix=0
```

to /etc/modprobe.conf

---

### Post by moshuptrail on 2007-01-21
might be a good time to disable ipv6

---

### Post by rnodal on 2007-02-03
this may help:
[http://ubuntuforums.org/showthread.php?t=352716]("http://ubuntuforums.org/showthread.php?t=352716")

-r

---

