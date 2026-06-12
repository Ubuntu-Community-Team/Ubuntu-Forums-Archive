---
title: "firestarter: &quot;The device erth0 is not ready&quot;"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2007-12-02
I have a wired connection configured manually and I can't get firestarter to work. I get the message "the device eth0 is not ready", although I am using eth0 at the time. I think that this problem started after I installed virtualbox and have configured a tap0 device in order for Windows (which run as a virtual machine) to be able to connect to the internet. Maybe something is wrong there, since I also don't have an internet connection at all every once in a while and have to reboot to fix it.

Here's what I get from ifconfig -a 

root@christina-laptop:/home/christina# ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:90:F5:3C:30:59  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe3c:3059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2322913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2344140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1433149550 (1.3 GB)  TX bytes:965740335 (921.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:90:F5:3C:30:59  
          inet6 addr: fe80::290:f5ff:fe3c:3059/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:2323046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2344160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1468003677 (1.3 GB)  TX bytes:969117778 (924.2 MB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tap0      Link encap:Ethernet  HWaddr 00:FF:10:81:32:A0  
          inet addr:192.168.2.64  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:10ff:fe81:32a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:113749 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Thanks in advance for the help!

---

### Post by daimaru on 2007-12-02
> **christina_svats said:**
> 

eth0      Link encap:Ethernet  HWaddr 00:90:F5:3C:30:59  
          inet6 addr: fe80::290:f5ff:fe3c:3059/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:2323046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2344160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1468003677 (1.3 GB)  TX bytes:969117778 (924.2 MB)
          Interrupt:11 Base address:0x4000 


i'm not sure if this will help, but I normally have problems with my wired connection and my router if i use the inet6 address and dont assign a normal static ip adress as you have for your tap0 device.

since your tap0 device is using 192.168.2.64

try this, or replace it with the static ip you wish to use. 
```
sudo ifconfig eth0 192.168.2.63
```63 is just an example use whichever number you like.

or if you want to use dhcp to dynmically assign ip use:

```
**dhcpcd eth0**
```

hope this works.

---

### Post by christina_svats on 2007-12-03
ok, I configured my eth0 using sudo configure eth0 192.168.2.3 and firestarter did start without any error message but... now I completely lost my internet connection! 
Any ideas on how to get back to where I was?

---

### Post by edm1 on 2007-12-03
Your problem could be with a bug in network manager have a look [here]("http://ubuntuforums.org/showthread.php?t=468630") and see if the work around fixes it.

---

### Post by christina_svats on 2007-12-03
thanks, I will try some of this stuff when I go back home, and I hope it works...
The connection on my virtual machine seemed to be ok, though...

---

### Post by christina_svats on 2007-12-03
ok, still no luck, I don't have an internet connection, I unistalled firestarter in case it was getting in the way, but no. ifconfig gives me this:

root@christina-laptop:/home/christina# ifconfig 
br0       Link encap:Ethernet  HWaddr 00:90:F5:3C:30:59  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe3c:3059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125541 (122.5 KB)  TX bytes:2569 (2.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:90:F5:3C:30:59  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe3c:3059/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144633 (141.2 KB)  TX bytes:2415 (2.3 KB)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tap0      Link encap:Ethernet  HWaddr 00:FF:E4:AD:35:F7  
          inet addr:192.168.2.64  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:e4ff:fead:35f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Any ideas on what might be wrong? Help please...(what's this br0 anyway???)

---

### Post by daimaru on 2007-12-03
wow weird problem you have there. check gateway and nameserver. 
to add gateway to your eth0 device assuming you have a router running at 192.168.2.1
do this.
```
**sudo route add default gw 192.168.2.1 eth0**
```
and make sure you have your nameserver in your resolv.conf file.

```
**sudo echo nameserver 192.168.2.1 > /etc/resolv.conf**
```

that should get your internet connection to work again.

---

### Post by christina_svats on 2007-12-04
I get the following when I try to configure the default route:

SIOCADDRT: No such process

Maybe I did something stupid. Anyway, the thing is that I have no problem connecting to the internet when I run a LiveCD, so, is there a way to configure my network like it is by default when running the LiveCD? Maybe this will get me back to where I was...:confused:

---

### Post by bobyy on 2007-12-04
@christina_svats ..hy can you show us the routing table ?
> $sudo netstat -r
maybe here is the problem..

---

### Post by christina_svats on 2007-12-04
root@christina-laptop:/home/christina# $sudo netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
christina-lapto *               255.255.255.255 UH        0 0          0 tap0
192.168.2.0     *               255.255.255.0   U         0 0          0 br0
192.168.2.0     *               255.255.255.0   U         0 0          0 tap0
default         .               0.0.0.0         UG        0 0          0 br0
root@christina-laptop:/home/christina# 


After rebooting again and again and again and after doing sudo /etc/init.d/networking restart   (again and again and again) I got back my internet connection, but I am afraid that I will lose it again (it happened before). Can you get anything out of netstat -r?????

I also know that there is a known bug concerning my Realtek card that is caused by windows (I run windows as a virtual machine), but I don't think that this is the problem, because I followed the respective instructions and it should be fixed by now. Anyway, I haven't used windows for lots of days now so I don't think they are getting in the way...

---

### Post by bobyy on 2007-12-04
maybee ..gateway must be for sure 192.168.2.0 and 
              genmask..........................255.255.255.0 you have 255.255.255.255

i hope it  is right
i work with realtech for years and i have npb.

---

### Post by christina_svats on 2007-12-04
I admit I don't really get it...
What does netstat gives us? I see br0 (which I have no idea what it is) and tap0, but i don't see eth0 (which i am using by manual configuring it). My router is at 192.168.2.1

---

