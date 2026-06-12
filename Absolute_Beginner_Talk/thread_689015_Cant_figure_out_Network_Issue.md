---
title: "Cant figure out Network Issue"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Bosox3 on 2008-02-06
I just installed Ubuntu 7.10 on my computer and I cant seem to get the internet to work. 
I have cable internet that runs through my wireless Netgear router. I have this computer hooked up w/ a cord but cant seem to get online.

here are some of my info.

jay@jay-desktop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02) 
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02) 
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01) 
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72 [GeForce 7300 SE] [10de:01d3] (rev a1) 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01) 
03:02.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20] 
jay@jay-desktop:~$ sudo lshw -c network 
[sudo] password for jay: 
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
 
jay@jay-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:21:D7:E7:94   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:16 Base address:0xe000  
 
eth0:avah Link encap:Ethernet  HWaddr 00:19:21:D7:E7:94   
          inet addr:169.254.9.97  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:16 Base address:0xe000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1392 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1392 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:102060 (99.6 KB)  TX bytes:102060 (99.6 KB)

---

### Post by njparton on 2008-02-06
What's in the following file:

/etc/networking/interfaces

---

### Post by oedha on 2008-02-06
isn't it supposed to be :==> /etc/network/interfaces ?

---

### Post by njparton on 2008-02-06
Yes, sorry, not in front of my linux box at the mo...

---

### Post by Golem XIV on 2008-02-06
"inet addr:169.254.9.97" shows that you haven't received a valid IP from the router's DHCP server.  Check that DHCP is enabled on your router (it should be by default).  Check that you don't have MAC address filtering enabled on the router.  If you do, either disable it or include the eth0 MAC (hwaddr) in the allowed MAC address list.

---

### Post by Bosox3 on 2008-02-06
> **oedha said:**
> isn't it supposed to be :==> /etc/network/interfaces ?


I get - Permission Denied

---

### Post by jan quark on 2008-02-06
run

```
gksudo gedit /etc/network/interfaces
```

---

### Post by Bosox3 on 2008-02-06
> **jan quark said:**
> run

```
gksudo gedit /etc/network/interfaces
```

ok..thanks. I typed that and now I get this:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

---

### Post by jan quark on 2008-02-06
please run one more time

```
lshw -C network
```

linux is case sensitive so it does make a difference if the c is c or C is C.

---

### Post by Bosox3 on 2008-02-06
> **jan quark said:**
> please run one more time

```
lshw -C network
```

linux is case sensitive so it does make a difference if the c is c or C is C.


jay@jay-desktop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:19:21:d7:e7:94 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 
jay@jay-desktop:~$

---

### Post by njparton on 2008-02-06
> **Bosox3 said:**
> ok..thanks. I typed that and now I get this:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

That looks fine...

---

### Post by Bosox3 on 2008-02-06
ok cool..so if everything seems ok...then the problem is getting an IP from my router?

---

### Post by njparton on 2008-02-06
Quite possibly. I imagine DHCP is enabled by default, so make sure that you don't have any other options enabled that would prevent an ip address being given out.

Can you connect with windows via this router on the same ethernet port?

---

### Post by lswest on 2008-02-06
can you post the results of running ```
sudo dhclient eth0
``` (this requests an IP from your router's dhcp server)

---

