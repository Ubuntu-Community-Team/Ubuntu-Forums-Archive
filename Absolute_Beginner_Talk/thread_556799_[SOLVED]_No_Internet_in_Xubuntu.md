---
title: "[SOLVED] No Internet in Xubuntu"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by mj0lnir on 2007-09-21
Hello, thanks in advance for any help...

I am rapidly approaching the point where I throw this laptop against a wall. It is an HP Omnibook 6100 running Xubuntu 7.04. I have searched on this site and can't seem to find an answer. 

I have everything installed and working fine, except Firefox. It won't get any sites. It pulls up the system intro page fine, but nothing else. I have tried connecting through a PCMCIA wireless card, a USB wireless adapter, and through an ethernet cable plugged right into the thing. Still can't get any pages.

Any ideas what on earth is going on?

Thanks again.

---

### Post by Pumalite on 2007-09-21
Have you verified your connection otherwise?. Have you tried a different browser?. Konqueror?.

---

### Post by mj0lnir on 2007-09-21
I'm pretty sure there's traffic because the light on the router for the correct port is lit. I'm not sure how I would go about getting or installing a new browser, I'm a little new to Linux.

---

### Post by Pumalite on 2007-09-21
I don't use Xubuntu, but I think you should be able to get Konqueror through Synaptic. If not, try IceWeasel.
System>Administration>Synaptic Package Manager

---

### Post by mj0lnir on 2007-09-21
I looked but I don't have either of those. Thanks for the help though. Any other ideas?

Also, sorry to be so noobish, but I didn't change anything on my network settings. Do I need to add my router as a DNS or as a server or anything like that?

---

### Post by HokeyFry on 2007-09-21
in a terminal type
```
ifconfig
```
and post the output

---

### Post by mocoloco on 2007-09-21
You probably have the version of Xubuntu that doesn't include the internet.  You'll have to purchase the upgrade to the Home Ultimate Premium version, and then ... oh wait sorry, I'm confusing it with a different OS I've had problems with :).

You need to first off verify you have a connection at all.  If you've been able to install updates that's a clear sign.  Open a terminal window (Applications -> Accessories -> Terminal), and type in ```
ping -c 4 www.ubuntu.com
```  It will tell you how many of 4 packets were received.

A) If you do get a response and you're connection's good, install another browser to test with.  On Xubuntu I would recommend Galeon, you can get it doing a search in Applications -> System -> Synaptic.  Or a faster way is copy and past this into a terminal ```
sudo apt-get install galeon
```.

B) If from the ping you see you're connection's not working, do "lspci" in a terminal and paste what Ethernet controller you have.

---

### Post by mj0lnir on 2007-09-21
Here it is:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4232 (4.1 KiB)  TX bytes:4232 (4.1 KiB)

Thanks

---

### Post by HokeyFry on 2007-09-21
thats all that shows up?

are you sure theres nothing else?



what are you using for internet on it right now?

---

### Post by mj0lnir on 2007-09-21
> **mocoloco said:**
> ping -c 4 [www.ubuntu.com](www.ubuntu.com)

"unknown host www.ubuntu.com"

> **mocoloco said:**
> B) If from the ping you see you're connection's not working, do "lspci" in a terminal and paste what Ethernet controller you have.

Here's that:

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:05.0 CardBus bridge: Texas Instruments PCI1420
02:05.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 41)

---

### Post by mj0lnir on 2007-09-21
> **HokeyFry said:**
> thats all that shows up?

are you sure theres nothing else?



what are you using for internet on it right now?

That's all that show up for ifconfig, yes.

I am on another computer for internet right now.

---

### Post by HokeyFry on 2007-09-21
that is really strange, because there should be at least one more entry there


maybe if you tried a reinstall? and when u reinstall have it hooked up into a LAN directly. that may solve your problem. otherwise i dont know what to say because i dont really know how to install an ethernet card, only wireless. that is something i probably should learn how to do though. ill look into it.

---

### Post by mj0lnir on 2007-09-21
Alright, well thanks everyone for the help. In the meantime, I will try a reinstall with the ethernet plugged in.

---

### Post by HokeyFry on 2007-09-21
wait try this

ifconfig -a

and post the output

---

### Post by mj0lnir on 2007-09-21
Too late :)

I'll post results in 30 min or so I guess.

---

### Post by HokeyFry on 2007-09-21
well good luck i guess

any other troubles dont hesitata to PM me, i can help you with wireless also if you want that

---

### Post by mocoloco on 2007-09-21
> 02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 41)
Yeah, that NIC should definitely be detected and set up on install.

---

### Post by mj0lnir on 2007-09-21
Awesome! Reinstalling with the ethernet cable solved the problem. Thanks everyone. HokeyFry, I'm going to PM you about wireless if you don't mind.

---

