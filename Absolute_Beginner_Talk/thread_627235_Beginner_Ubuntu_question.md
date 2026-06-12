---
title: "Beginner Ubuntu question"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by HappyEisentrout on 2007-11-29
Hey there.  I am kind of a beginner when it comes to this Ubuntu stuff but I gave it a try.  I am using a Fujitsu Lifebook E362 and I can use the PCI port for hardwiring the interent but I can get my PCI wireless card to even be read as connected.  I have installed the drivers using Ndiswrapper but it still wont detect it.  Does anyone have any ideas on what I can do?  Oh and my sound doesn't work but I don't care so much about that.

Any help would be appreciated.

---

### Post by jimrz on 2007-11-29
please post the make/model/chipset of your wifi card. this will allow others with the same card to assist you in getting it working

---

### Post by HappyEisentrout on 2007-11-29
sorry, I have a belkin wireless g plus F5D7011 ver1212.  The windows wirelss drivers installer shows that the card is connected it's just the computer won't recognize that it is even hooked up.  The card doesn't light up or anything.

---

### Post by HappyEisentrout on 2007-11-29
Does anyone know how to fix this?

---

### Post by bobyy on 2007-11-29
ok ..lets start
#ifconfig -a
#lshw -c network
#lspci
please post here this outputs.... :) now we have a start point..

---

### Post by HappyEisentrout on 2007-11-30
> **bobyy said:**
> ok ..lets start
#ifconfig -a
#lshw -c network
#lspci
please post here this outputs.... :) now we have a start point..

ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:11:50:95:2D:43  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 

eth1      Link encap:Ethernet  HWaddr 00:50:04:B3:58:2E  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:feb3:582e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2274 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2296353 (2.1 MB)  TX bytes:133423 (130.2 KB)
          Interrupt:3 Base address:0x300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8592 (8.3 KB)  TX bytes:8592 (8.3 KB)



lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status


lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:13.0 CardBus bridge: Texas Instruments PCI1221
00:13.1 CardBus bridge: Texas Instruments PCI1221
00:14.0 VGA compatible controller: Trident Microsystems Cyber 9388 (rev d3)
05:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


is this what you wanted?

---

### Post by bobyy on 2007-11-30
hy ...
try this for your Broadcom BCM4318  [http://ubuntuforums.org/showthread.php?t=346083](http://ubuntuforums.org/showthread.php?t=346083)

---

### Post by HappyEisentrout on 2007-11-30
outstanding, thank you so much.

---

### Post by bobyy on 2007-11-30
let us know if it is working or not ,please.. :)

---

### Post by katch22 on 2007-11-30
He said "outstanding" I would take that to mean it worked. :)

---

### Post by HappyEisentrout on 2007-11-30
yeah it worked great.  Thanks bobyy for finding that post for me.

---

### Post by bobyy on 2007-11-30
Great.. :) 
in my previous post it was a mistake and y apologise for that 
one of command was:
> #lshw -c network
the command shoul be like :
> #lshw -C network

thx see you :)

---

