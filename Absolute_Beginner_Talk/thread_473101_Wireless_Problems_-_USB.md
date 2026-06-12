---
title: "Wireless Problems - USB"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by xMave on 2007-06-13
Alright, I ran into a new problem now so I'll try to give you a lot of information first.

Ubuntu won't detect that my linksys wireless network adapter (WUSB54G V.4) is plugged in. When I first plug it in, the 'power' light on the adapter turns on for about 2 seconds and then goes off, but the 'activity' light never goes on. I also have a USB mouse that's plugged in and working fine.

Now I THINK I have AMD64, mainly because when I tried to install something with the intel i38 or whatever, it said "wrong architecture" and AMD64 worked. So I presume thats all that works. 

I'm running Ubuntu Feiry Fawn (7.04 amd64), with no internet connection ON the PC with ubuntu, but I DO have internet access on another computer.

I'm running an Intel Core 2 Duo 6300 processor with a gigabyte motherboard, the computer is all home made.

In the internet connections, there is no wireless option, just "Wired connection: Roaming mode enabled" and "Modem connection: this network interface is not configured".

With the adapter plugged in, these are the results of the tests in the terminal:

**Lsusb** *didn't include the Buses with 0000:0000, only the ones with something on them:
> Bus 007 Device 002: ID 045d:c041 Logitech, Inc.

**ifconfig:**
> eth0[INDENT]Link encap:Ethernet  HWaddr 00:16:E6:D2:30:2F
UP BROUDCASTMULTICAST MTU:1500 Metric:1
RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16[/INDENT]

lo[INDENT]Link encap: Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:772 errors:0 dropped:0 overruns:0 frame:0
TX Packets:772 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:61832 (60.3 KiB) TX bytes:61832 (60.3 KiB)[/INDENT]

**iwconfig:**
> lo[INDENT]no wireless extensions[/INDENT]

eth0[INDENT]no wireless extensions[/INDENT]

I REALLY appreciate any help, thanks!

---

### Post by wreti on 2007-06-13
Are you using a wired connection on that computer with Ubuntu, or are you on another machine?

---

### Post by xMave on 2007-06-13
No, the computer with Ubuntu has no internet access whatsoever (just the wireless which isn't working obviously), I'm using a laptop that has wireless internet to get help.

---

### Post by wreti on 2007-06-13
If you uncheck "Enable roaming" for your wired connection, you may be able to use the wired connection. As far as the WUSB54G adapter goes, the version 4's are bit tricky to get going. You should be able to get it working with ndiswrapper and the proper windows driver for your device. Maybe this thread will help you. [http://ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g+v4](http://ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g+v4)
If you can't get your wired connection going, you'll have to download on another comp and transfer over to your Ubuntu comp.

---

### Post by xMave on 2007-06-13
I'll give that a read and a try, but I don't think I'd be able to get on the wired connection by unchecking the roaming, because I'm not wired? The  router/modem is 70-100ft away so I can't wire it.

Thanks for the help so far!

---

### Post by NfF on 2007-06-13
xmave. i too exactly have the same problem with my dekstop pentium 4 pc. i also am using a laptop to connect to the internet..
if u found the solution..do contact me..im down.

---

### Post by xMave on 2007-06-13
I sure will.

Ok, when I followed that guide I got so far as to getting the driver (rt2500usb.inf) off of the Linksys cd, but when I try to put it on ndiswrapper using the terminal's:

```
$sudo ndiswrapper -i rt2500usb.inf
```

, it doesn't work and says it's an invalid driver. Does the driver (rt2500usb.inf) have to be in the same folder (/usr/sbin) as ndiswrapper? Because when I tried to move it, it said I didn't have permision to write in that folder.

Still lost :(

---

### Post by xMave on 2007-06-14
Ok, so I figured out how to move the file (a simple "$sudo mv rt2500usb.inf/sys /usr/sbin/" did the trick).

I ran an lsusb and it FINALLY showed up as the linksys being connected. But no wireless in the connections, I restarted now and if it works, I'll be sure to tell as to what I did for any future strugglers (hopefully not me!).

---

