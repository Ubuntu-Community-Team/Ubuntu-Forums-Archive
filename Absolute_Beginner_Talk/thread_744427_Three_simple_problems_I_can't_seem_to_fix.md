---
title: "Three simple problems I can't seem to fix"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by ryan22158 on 2008-04-03
1) I can't seem to figure out how to make my network location my default one. When ever I restart or shut down I have to go into network manager and select my location and then apply the settings. Is there a way I can get this to "stick" so I don't have to go into the network manager every time I start up?

2) Every once and a while when I restart my sound does not work I have tried selecting different settings while in preferences but the only thing that seems to fix it is restarting or logging off a couple of times it works again any thoughts?

3) The touch pad on my laptop has barely any speed compared to my USB mouse I have tired the menu in preferences it seems to on affect my USB mouse and not the touch pad.

---

### Post by esva on 2008-04-03
how about if you set the preferences of sound and then you click on the save this session box when you are going to log off? the box in the wondow that pops up saying if you're sure you want to log off.

---

### Post by pseudo-random on 2008-04-03
I don't bother with the network manager. I've found it to be very buggy.
When I switch between wireless or ethernet with my laptop for example I do it from the command line with ifconfig. I put the commands into scripts on my desktop so If I'm wireless I click wifi.sh etc.
If you'd like examples let me know.

---

### Post by ryan22158 on 2008-04-03
> **pseudo-random said:**
> I don't bother with the network manager. I've found it to be very buggy.
When I switch between wireless or ethernet with my laptop for example I do it from the command line with ifconfig. I put the commands into scripts on my desktop so If I'm wireless I click wifi.sh etc.
If you'd like examples let me know.

Interesting, does this work with WPA enabled? 

And yeah I would need to know how to do that since I have pretty much no idea how.

---

### Post by Crafty Kisses on 2008-04-03
Can you post the following output:
```
lspci
```

---

### Post by ryan22158 on 2008-04-03
> **esva said:**
> how about if you set the preferences of sound and then you click on the save this session box when you are going to log off? the box in the wondow that pops up saying if you're sure you want to log off.

Okay, so this works great for logging in and out but I just restarted to check if it saved my settings but it did not, I had go to network manager and reselect my destination an then wait for it to connect. 

And I made sure ubuntu saved my session every time I logged out so I that cuts down on how many times I have to reconnect. But a big problem is that pretty much the only time I stop using ubuntu is to use vista because I am in the process of trying to repair it.

---

### Post by ryan22158 on 2008-04-03
> **Codename said:**
> Can you post the following output:
```
lspci
```


00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

