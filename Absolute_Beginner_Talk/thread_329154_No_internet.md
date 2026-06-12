---
title: "No internet"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by yelserpdog on 2007-01-01
Hi there,
Well, I got Ubuntu Edgy installed on my Inspiron 1501 and it's dual booting ok with XP. My problem is that I cannot get the internet working. I'm using a broadcom wifi that's built in o the laptop and I've noticed on other threads that there are ways to get it working. I figured if i  can just get internet working using the ethernet cable direct into the router I can then get wireLESS working after that but I can't even get the the wirFUll way working. In the top right of the screen it keeps saying that it's not detected or something. I've gone to system > networking and tried to configure it in there as per my ISP settings but no joy. Can anyone help?? Cheers

---

### Post by taco_truck on 2007-01-01
I have the same exact problem as you and i need some real help from a professional...

---

### Post by jonathan.lees on 2007-01-01
First make sure you have the activity led lit on your ethernet card and on the port it is plugged into on the router.

---

### Post by geo_bio on 2007-01-01
Please go to Network Manager. It should be a icon of two monitors on teh top right of your screen (by the Power/Logout icon). There, you have to Configure it and choose the network. Then go back the the previous screen, and change your network. By default, it may say "lo", but you should change it to "eth1" (or whatever is the wireless).

If you're having a problem getting the WiFi card to work due to driver problems, then let me know and I'll explain about that.

---

### Post by solon magrizos on 2007-01-01
I have to be, by far, the worst handyman in the world. It&#8217;s not like I can&#8217;t use a screwdriver or a hammer, it&#8217;s just that no matter what I touch, something goes wrong. Thank god I always have Solon magrizos to help me out. The guy in a genius when it comes to anything hands on. Whether it&#8217;s building a deck, installing a garage door, or even putting together a chair, he makes it into an art. Heck, he even turns replacing a light bulb into an art. I can rest a lot easier knowing Jacob helped me build something. For some reason, my things just don&#8217;t end up quite as safe.

---

### Post by jonathan.lees on 2007-01-01
Could Solon Magrizos help me fix my network?

---

### Post by yelserpdog on 2007-01-01
> **geo_bio said:**
> Please go to Network Manager. It should be a icon of two monitors on teh top right of your screen (by the Power/Logout icon). There, you have to Configure it and choose the network. Then go back the the previous screen, and change your network. By default, it may say "lo", but you should change it to "eth1" (or whatever is the wireless).

If you're having a problem getting the WiFi card to work due to driver problems, then let me know and I'll explain about that.

When I go here it brings up an error message saying:
Please contact your system administrator to resolve the following problem SIOCGIFFLAGS error:No such device

Ta
Des

---

### Post by jonathan.lees on 2007-01-01
Could you open Terminal, found in Applications > Accessories and type the following 3 commands individually, and then post the output here:

```

lspci
cat /etc/iftab
ifconfig

```

---

### Post by yelserpdog on 2007-01-01
> **jonathan.lees said:**
> Could you open Terminal, found in Applications > Accessories and type the following 3 commands individually, and then post the output here:

```

lspci
cat /etc/iftab
ifconfig

```

Here it is:

des@des-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc Unknown device 4380
00:13.0 USB Controller: ATI Technologies Inc Unknown device 4387
00:13.1 USB Controller: ATI Technologies Inc Unknown device 4388
00:13.2 USB Controller: ATI Technologies Inc Unknown device 4389
00:13.3 USB Controller: ATI Technologies Inc Unknown device 438a
00:13.4 USB Controller: ATI Technologies Inc Unknown device 438b
00:13.5 USB Controller: ATI Technologies Inc Unknown device 4386
00:14.0 SMBus: ATI Technologies Inc Unknown device 4385 (rev 13)
00:14.1 IDE interface: ATI Technologies Inc Unknown device 438c
00:14.2 Audio device: ATI Technologies Inc Unknown device 4383
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 438d
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4384
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
des@des-laptop:~$ cat/etc/iftab
bash: cat/etc/iftab: No such file or directory
des@des-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:C0:2B:1C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

des@des-laptop:~$ 

THanks
Des

---

### Post by yelserpdog on 2007-01-02
Can anyone help??

---

