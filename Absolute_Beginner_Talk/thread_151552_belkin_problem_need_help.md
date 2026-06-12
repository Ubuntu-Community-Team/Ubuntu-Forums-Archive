---
title: "belkin problem need help"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by ampteed on 2006-03-28
HI I cant find my belkin wirless card!
Have looked around in div threads, coud not find any help!
My ubentu cant find the card! poste somthing about bordcom!
alsow I dident have the card in under install, do I have to reinstall?

realy need help here

---

### Post by markr on 2006-03-28
What model number is it?

---

### Post by ampteed on 2006-03-28
its a F5D7011 Belkin card but ubuntu cant find it!
however when I type "lspci"
I get "0000:06:00.0 Network controller: Broadcom Corportion BCM4306 802.11b/g Wireless LAN controller (rev 03)
:confused:

---

### Post by jethro10 on 2006-03-28
I messed around with this problem for 3 days, to no avail.

Eventually I bought a £20 Wireless bridge and attached it to my wired network card.
Same result, lot less worries

---

### Post by ampteed on 2006-03-28
ok here is the "lspci" 

```
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:09.0 CardBus bridge: Texas Instruments: Unknown device 8031
_[U]0000:06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)_[/U]

```
and here are the and "pci -n"
```
root@ampted:/home/ampted # lspci -n
0000:00:00.0 0600: 1002:5950 (rev 01)
0000:00:01.0 0604: 1002:5a3f
0000:00:13.0 0c03: 1002:4374
0000:00:13.1 0c03: 1002:4375
0000:00:13.2 0c03: 1002:4373
0000:00:14.0 0c05: 1002:4372 (rev 11)
0000:00:14.1 0101: 1002:4376
0000:00:14.3 0601: 1002:4377
0000:00:14.4 0604: 1002:4371
0000:00:14.5 0401: 1002:4370 (rev 02)
0000:00:14.6 0703: 1002:4378 (rev 02)
0000:00:18.0 0600: 1022:1100
0000:00:18.1 0600: 1022:1101
0000:00:18.2 0600: 1022:1102
0000:00:18.3 0600: 1022:1103
0000:01:05.0 0300: 1002:5955
0000:05:00.0 0200: 10ec:8139 (rev 10)
0000:05:09.0 0607: 104c:8031
_[U]0000:06:00.0 0280: 14e4:4320 (rev 03)_[/U]

```

hope someone can help me!!!!

---

### Post by mdmarmer on 2006-03-28
In Dapper this card can be made to work natively

The native driver is quite new so it's probably better to use ndiswrapper
Try this thread

If it doesn't explain it well enuf search on ndiswrapper broadcom wireress for some others ...

[http://ubuntuforums.org/showthread.php?t=147648&highlight=wireless+broadcom+ndiswrapper](http://ubuntuforums.org/showthread.php?t=147648&highlight=wireless+broadcom+ndiswrapper)

In Dapper you may need to remove the native driver or blacklist it ...

Mike

---

### Post by ampteed on 2006-03-28
tnx!

but it dint work!
beginning to think that ubuntu dont like my pcmci slot/card! cant find it or install! I have tryed every thing I have found in the forum!
by the way can u show me the code for usage of dabber?

---

### Post by trent dillman on 2006-03-28
Does 

```
lsmod | grep bcm
```

show anything?

---

### Post by ampteed on 2006-03-28
hmm no!?!
```
root@ampted:~ # lsmod | grep bcm
root@ampted:~ #

```

---

### Post by trent dillman on 2006-03-28
Ok, so try installing ndiswrapper-utils and ndisgtk

```

sudo apt-get install ndiswrapper-utils ndisgtk

```

Then run the gui program

```

sudo ndisgtk

```

Install your windows drivers from your driver disk (should be bcmwl5.inf).

---

### Post by ampteed on 2006-03-28
Ok the drivers are installed but cant find the hardware

---

