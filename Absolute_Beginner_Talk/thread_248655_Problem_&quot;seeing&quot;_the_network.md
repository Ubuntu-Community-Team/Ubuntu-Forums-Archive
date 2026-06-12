---
title: "Problem &quot;seeing&quot; the network"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by JonParis on 2006-09-01
I'm an absolute beginner with Linux so please be gentle!

I have installed Ubuntu and I really like it but - although it recognizes the ethernet card in the laptop it just can't see the network.  If I boot Puppy then it works perfectly after running the wizard.  But I'm not wild about the Puppy interface and would prefer Ubuntu.

This is the current situation:

1) The card is enabled and shows up in Network Settings.

2) I can change the network settings and it will enable and disable on request

3) If I give it a hard-coded IP (instead of using DHCP) it can ping its own address - but cannot ping anything else on the network.  Nor can anything on the network see that address.

I've exhausted all the things I know to look at so any thought would be welcomed.

Jon

---

### Post by jorn on 2006-09-01
Are you behind a router?
Try:
> ifconfig
in terminal and paste output, though I am not sure I can help you.

---

### Post by Iowan on 2006-09-01
Wish I had a good "Do this and your problem will go away", but I don't.  I'd wonder about workgroup/domain name... but **ping** shouldn't care.  You mentioned what happens with static IP address - what happens with DHCP address?

---

### Post by galileon on 2006-09-01
open a console, and type ifconfig, post the results here please

edit: sorry, didnt read the thread properly, and i cant figure out how to delete this post...

---

### Post by JonParis on 2006-09-01
> **jorn said:**
> Are you behind a router?
Try:

in terminal and paste output, though I am not sure I can help you.

The whole network is behind a router - other PCs can see each other - and under Puppy this one can too.

I tried the ifconfig - copied the text and then burst out laughing!  I can't get to the internet on that machine so I can't paste the output here!  

I'm going to try a USB key and see how that works.

---

### Post by JonParis on 2006-09-01
> **Iowan said:**
> Wish I had a good "Do this and your problem will go away", but I don't.  I'd wonder about workgroup/domain name... but **ping** shouldn't care.  You mentioned what happens with static IP address - what happens with DHCP address?

With a DHCP setting it just keeps trying for about 5 minutes or so (I can see the attempts on the system activity trace).  It then gives up but with no error message or anything.  There is no rejection message in the log of the D-Link router that acts as the DHCP server.

Jon

---

### Post by JonParis on 2006-09-01
> **JonParis said:**
> The whole network is behind a router - other PCs can see each other - and under Puppy this one can too.

I tried the ifconfig - copied the text and then burst out laughing!  I can't get to the internet on that machine so I can't paste the output here!  

I'm going to try a USB key and see how that works.

OK - Now I'm even more impressed - it immediately recognized the USB key and it worked like a charm.  Is there a specific command one should use before removing the USB key?  I tried "Eject" but it doesn't do it.  Anyway - on to the results of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:50:04:B4:3D:F3
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:feb4:3df3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6211 errors:0 dropped:0 overruns:0 carrier:6205
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:502118 (490.3 KiB)
          Interrupt:3 Base address:0x300

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:66928 (65.3 KiB)  TX bytes:66928 (65.3 KiB)

---

### Post by jorn on 2006-09-01
How does your:
> sudo gedit /etc/network/interfaces
look like?
Are you able to acces you router?

---

### Post by JonParis on 2006-09-01
> **jorn said:**
> How does your:

look like?
Are you able to acces you router?

content is:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

As to the router - no - it cannot ping anything on the network except itself.

Jon

---

### Post by jorn on 2006-09-01
Just a suggestion With a cable to the router. Make the file look like this:> 
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

What is the name of your wireless netadapter?

---

### Post by galileon on 2006-09-01
why's there no 

      auto eth0

just before 

      iface eth0 inet dhcp

?

---

### Post by JonParis on 2006-09-01
> **galileon said:**
> why's there no 

      auto eth0

just before 

      iface eth0 inet dhcp

?

Beats me - "ubuntu did it" - I haven't touched that file.  Is it worth adding it back by hand?

---

### Post by JonParis on 2006-09-01
> **jorn said:**
> Just a suggestion With a cable to the router. Make the file look like this:
What is the name of your wireless netadapter?

I'll give that a try.

Not sure what you mean by "name" - this PC does not have a wireless adaptor.  It has been used with one under Win2K - but that can't affect it surely?

Jon

---

### Post by JonParis on 2006-09-01
I have tried both of the suggestions and restarted the PC.  Neither the "auto eth0" or the commenting out of the wlan0 entries makes any difference.  


Anyone got any other ideas?

---

### Post by jorn on 2006-09-02
Another possibility is trying reconfiguring you connection and see if there are any hints:
> sudo pppoeconf
I thought you had a wireless card because "wlan" in tne file "interfaces" means wireless-lan and I just wanted you to disable it so we only have to concentrate on one thing. That is don by putting "#" in front of it.

---

### Post by JonParis on 2006-09-02
> **jorn said:**
> Another possibility is trying reconfiguring you connection and see if there are any hints:

I thought you had a wireless card because "wlan" in tne file "interfaces" means wireless-lan and I just wanted you to disable it so we only have to concentrate on one thing. That is don by putting "#" in front of it.

I ran pppoeconf as suggested.  It finds the ethernet card but subsequently fails with a message to the effect that the access concentrator of my provider did not respond.  I guess I'm not understanding the terminology becuase I thought my 'provider" was the ISP on the other side of my router?  Isn't pppoe just  used by the router?  I didn't think my ethernet conection needed to know anything about it?

In case the existing definitions were causing the problem I dectivated all of the entries in the etc/network/interfaces by adding the # as suggested previously.  I then re-booted and tried again but it makes no difference.

Since the PCMCIA card works just fine under puppy is there any point in booting that and running some commands to see what is different about the config?

Thanks for the help so far 

Jon

---

