---
title: "Wireless Issues"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-02-12
Hi,

I'm trying to get my wireless card to work, but to no avail as yet.  I've tried several tutorials and solutions, but the light on my usb wireless card isn't even coming on.

I'm using Gutsy, and a US Robotics wireless usb.

I installed ndiswrapper and my specific driver (RSC4USB.inf) as per [This Thread]("http://ubuntuforums.org/showthread.php?t=606311&highlight=ndiswrapper+Gutsy").

I have checked all the steps stated there, and everything appears to be correct.

The last step is to go to Admin> Network and configure your wireless network, but the only options I have there are for ethernet and dial up.  There's no wireless option at all.

If I run the command "ndiswrapper -l" I get:

```

rsc4usb : driver installed
device (0BAF:0118) present (alternate driver: p54usb)

```

"iwconfig" gives me

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

"ifconfig" gives me

```

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:AA:19:79  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:feaa:1979/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:774017 (755.8 KB)  TX bytes:153179 (149.5 KB)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

So I can see that I'm missing wlan0 for some reason, but I have no idea what to do now!

Can anyone help please?

---

### Post by kwacka on 2008-02-12
if you use "lsmod" do you see ndiswrapper drivers?

---

### Post by Squizz on 2008-02-12
> **kwacka said:**
> if you use "lsmod" do you see ndiswrapper drivers?

Yeah, here's the line

```

usbcore               138632  4 ndiswrapper,p54usb,uhci_hcd

```

---

### Post by dca on 2008-02-12
At CLI type:
 
lsmod | grep ndiswrapper
 
(or)
 
modprobe -l | grep ndiswrapper
 
 
...if nothing shows up, type
 
 modprobe -i ndiswrapper
 
...then restart system...
 
 
*nevermind, I was too late...* :D

---

### Post by Squizz on 2008-02-12
Yeah, I checked ndiswrapper -l before I posted, and posted the output.

I don't really know, but I'm guessing I need to make wlan0 work as that's usually in the network menu if a wireless card is attached.

---

### Post by dca on 2008-02-12
Don't quote me but I guess that P4usb or whatever listed as 'alternate driver' is loading at start-up along w/ ndiswrapper causing this issue?

---

### Post by Squizz on 2008-02-12
so should I blacklist it?  It's broken already so it doesn't really matter what I try....

---

### Post by dca on 2008-02-12
...hmmm, good point...
 
I'm always hesitant....  I haven't really had that much experience w/ the USB or PCMCIA Wifi cards...  Now the PCI, mini-PCI, & mini-PCIe I like to think of myself as a pro...  but I'm not...:(
 
I can't imagine there being any differences.
 
Let us know then if blacklisting the other does any good...

---

### Post by kwacka on 2008-02-12
Possibly Inaccurate reply removed.

---

### Post by sharkly17shogun on 2008-02-12
I don't know about your computer, but it might be a hardware issue. Check if the wireless card is properly installed.

---

### Post by Squizz on 2008-02-12
I think I may have just messed up a bit...

```

admin1@server:~$ ndiswrapper -r rsc4usb
couldn't delete /etc/ndiswrapper/rsc4usb: Inappropriate ioctl for device
admin1@server:~$ sudo ndiswrapper -r rsc4usb
admin1@server:~$ modprobe p54usb
WARNING: /etc/modprobe.d/blacklist line 27: ignoring bad line starting with 'b'
WARNING: Error inserting cfg80211 (/lib/modules/2.6.22-14-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted
WARNING: Error inserting mac80211 (/lib/modules/2.6.22-14-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
WARNING: Error inserting p54common (/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54common.ko): Operation not permitted
FATAL: Error inserting p54usb (/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54usb.ko): Operation not permitted

admin1@server:~/Desktop/Driver$ ndiswrapper -i rsc4usb.inf
couldn't create /etc/ndiswrapper/rsc4usb: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
admin1@server:~/Desktop/Driver$ sudo ndiswrapper -i rsc4usb.inf
installing rsc4usb ...
couldn't open rsc4usb.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
admin1@server:~/Desktop/Driver$ sudo ndiswrapper -i RSC4USB.inf
driver rsc4usb is already installed
admin1@server:~/Desktop/Driver$ ndiswrapper -l
rsc4usb : invalid driver!
admin1@server:~/Desktop/Driver$ 

```


And blacklisting the other driver had no effect by the way dca.

sharkly17shogun - this thread is a request to help me install it properly....

Also, I should probably point out again that the green light isn't coming on, on the card like it was in dapper either.

---

### Post by kwacka on 2008-02-12
sorry, try 'sudo modprobe' & 'sudo ndiswrapper'

---

### Post by Squizz on 2008-02-12
> **kwacka said:**
> sorry, try 'sudo modprobe' & 'sudo ndiswrapper'

Those errors were my fault sorry - I left a "b" in the blacklist file.

I just did

```

admin1@server:~$ sudo ndiswrapper -r rsc4usb
admin1@server:~$ sudo modprobe p54usb

```

but got no output, and still nothing new in iwconfig :(

---

### Post by Squizz on 2008-02-13
Can anyone help today?

Basically I need to make wlan0 appear - didn't want to start a new thread though.

Thanks!

---

