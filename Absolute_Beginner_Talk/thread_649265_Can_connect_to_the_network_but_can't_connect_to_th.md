---
title: "Can connect to the network but can't connect to the internet"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Casual_Mohammed on 2007-12-24
Hello.

First of all I am an absolute newbie with Linux (installed it an hour ago). I'm using a Sony Vaio G model and I just installed the latest version of Ubuntu.

My problem is that I can connect to my network fine and I put in my proxy setting but when I use firefox it keeps saying that it cannot connect to "website" server.

---

### Post by Casual_Mohammed on 2007-12-24
bump

---

### Post by jan quark on 2007-12-24
Pleas post the result of the following commands which you can type into the terminal. They will show us some pieces of information about your network status.

lspci

lshw -C network

iwconfig

ifconfig

sudo iwlist scan

---

### Post by Casual_Mohammed on 2007-12-24
LPSCI

> homer@Arbiter:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:05.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:05.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:08.0 Ethernet controller: Intel Corporation 82562EM/EX/GX - PRO/100 VM (LOM) Ethernet Controller Mobile (rev 03)
06:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


**lshw -C network**

> homer@Arbiter:~$  lshw -c network
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



**iwconfig**

> homer@Arbiter:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"10I63A72B"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:92:D6:DC:90   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-23 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**ifconfig**


> homer@Arbiter:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:A9:2A:54:CC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:16:6F:71:62:CB  
          inet addr:10.13.237.116  Bcast:10.13.237.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe71:62cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:217804 (212.6 KB)  TX bytes:9320 (9.1 KB)
          Interrupt:22 Base address:0x8000 Memory:b0108000-b0108fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


**sudo iwlist scan**

> homer@Arbiter:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:92:D6:DC:90
                    ESSID:"10I63A72B"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-24 dBm  
                    Extra: Last beacon: 8ms ago



---

### Post by jimrz on 2007-12-24
You might try going into "System" > "Administration" > "Network" > the "DNS" tab and make sure that you have the appropriate server(s) listed there.

---

### Post by Casual_Mohammed on 2007-12-24
Some of them were missing and I added the rest but it still won't work :confused:

---

### Post by Casual_Mohammed on 2007-12-24
t I can log into my msn messenger and talk to my friends no problem...I even downloaded a few plugins.

It's just that I can't browse the internet..it always says cannot connect to server.

---

### Post by Faud on 2007-12-24
How are you trying to connect to Firefox..from the menu or from a program like AWN ?

---

### Post by Casual_Mohammed on 2007-12-25
> **Faud said:**
> How are you trying to connect to Firefox..from the menu or from a program like AWN ?

From the menu..

---

### Post by bumanie on 2007-12-25
As you have some degree of connectivity, I am not sure with this is your problem or not. However for many running gutsy gibbon, the ipv6 stack released a number of months ago has caused problems with connecting to the internet. At this point, I have not heard of someone having 'partial connectivity' with the ipv6 stack problem. But as you don't seem to be getting anywhere, maybe it would be worth you tying to blacklist ipv6 and see whther that makes any difference. It is the only way I could get the internet working in gutsy. There are two methods you can choose from. Both ( as I undertand things) can be reversed by undoing changes you make. Here are the two methods
Method 1.
gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Method 2 (is to diable ipv6 in firefox)
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true
Hope this helps.

---

### Post by Casual_Mohammed on 2007-12-25
> **bumanie said:**
> As you have some degree of connectivity, I am not sure with this is your problem or not. However for many running gutsy gibbon, the ipv6 stack released a number of months ago has caused problems with connecting to the internet. At this point, I have not heard of someone having 'partial connectivity' with the ipv6 stack problem. But as you don't seem to be getting anywhere, maybe it would be worth you tying to blacklist ipv6 and see whther that makes any difference. It is the only way I could get the internet working in gutsy. There are two methods you can choose from. Both ( as I undertand things) can be reversed by undoing changes you make. Here are the two methods
Method 1.
gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Method 2 (is to diable ipv6 in firefox)
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true
Hope this helps.

Tried that and still no go...

The thing that's pissing me off is that i'm comparing my laptop with my brothers laptop and everything is seems normal..

DNS,Subnet Mask,default gateway...nothing seems out of place...

---

### Post by Casual_Mohammed on 2007-12-25
YES!!! I FIXED THE PROBLEM!

:D


I have to thank you bumanie! although your solution didn't work but it led me to the right path.

I was checking "about:config" on my firefox when I noticed that the proxy setting weren't there.. I checked my network proxy in the system tray and it was fine..

so I manually inputed all the proxies and there you go!!!

It's a good thing too because i was beginning to wonder if I should go back to windows but now I can start using the linux!

Thanks alot guys I appreciate your help!

---

### Post by bumanie on 2007-12-25
I am glad you got it sorted. As I said it didn't sound like the classic ipv6 problem, but it was worth a go. Fortunately you were observant enough to look at other things in firefox:config and found the problem. Well done.

---

