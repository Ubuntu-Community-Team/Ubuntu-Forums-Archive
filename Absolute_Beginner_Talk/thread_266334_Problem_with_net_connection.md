---
title: "Problem with net connection"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Tamil on 2006-09-27
I figured out **Ethernet connection** was missing in **Network settings**. How to get it back?

---

### Post by Tamil on 2006-09-28
Any suggestions?

---

### Post by andriansah on 2006-09-28
What about in terminal?
$ifconfig

is there any result

---

### Post by Tamil on 2006-09-28
> **andriansah said:**
> What about in terminal?
$ifconfigGot the following:
> Line encap:Local Loopback
1net addr:127.0.0.1 Mask:255.0.0.0
1net6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:160 errors:0 dropped:0 overruns:0 frame:0
TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:8000 (7.8 KiB) TX bytes:8000 (7.8 KiB)

---

### Post by Tamil on 2006-09-28
Any suggestions?

---

### Post by Tamil on 2006-09-29
](*,)

---

### Post by Tamil on 2006-09-29
Is it possible to repair using live CD?

---

### Post by morphodone on 2006-09-30
how about

```
sudo ifconfig eth0 up
sudo dhclient
```

---

### Post by K.Mandla on 2006-09-30
You could look in your interfaces file and see if your connection is listed.

```
sudo nano /etc/network/interfaces
```
You should see something in there about eth0 (or a similar hardware alias).

If you're still lost finding it, make sure it's been identified in the hardware profile.

```
lspci -v
```
will give you a detailed list of the hardware that Ubuntu found. 

Hope that helps. ;)

---

### Post by Tamil on 2006-09-30
Thanks for your replies.

> **morphodone said:**
> how about

```
sudo ifconfig eth0 up
sudo dhclient
```
> tamil@TAMIL:~$ sudo ifconfig eth0 up
Password:
eth0: ERROR while getting interface flags: No such device
tamil@TAMIL:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

No broadcast interfaces found - exiting.


> **K.Mandla said:**
> ```
sudo nano /etc/network/interfaces
```
You should see something in there about eth0 (or a similar hardware alias).I have the following> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

> **K.Mandla said:**
> ```
lspci -v
```
will give you a detailed list of the hardware that Ubuntu found.
> tamil@TAMIL:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ff200000-ff2fffff
        Prefetchable memory behind bridge: bf900000-bf9fffff
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at ffa40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation 82915G Express Chipset Family Graphics Controller (rev 04)
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, fast devsel, latency 0
        Memory at ff980000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Intel Corporation: Unknown device e203
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at ffa3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: ff600000-ff6fffff
        Prefetchable memory behind bridge: 00000000bfd00000-00000000bfd00000
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: ff500000-ff5fffff
        Prefetchable memory behind bridge: 00000000bfc00000-00000000bfc00000
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: ff400000-ff4fffff
        Prefetchable memory behind bridge: 00000000bfb00000-00000000bfb00000
        Capabilities: <available only to root>

0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: ff300000-ff3fffff
        Prefetchable memory behind bridge: 00000000bfa00000-00000000bfa00000
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at dc00 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at e000 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at e400 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at e800 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 58
        Memory at ffa3bc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: ff700000-ff7fffff
        Prefetchable memory behind bridge: 00000000bfe00000-00000000bfe00000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, medium devsel, latency 0

0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 193
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Intel Corporation: Unknown device 4156
        Flags: medium devsel, IRQ 5
        I/O ports at d800 [size=32]

0000:06:02.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
        Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 9
        Memory at ff7e0000 (32-bit, non-prefetchable) [size=128K]
        Memory at ff7c0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at cc00 [size=64]
        Expansion ROM at bfe00000 [disabled] [size=128K]
        Capabilities: <available only to root>

---

### Post by Tamil on 2006-10-02
Bump.

---

### Post by Tamil on 2006-10-03
Bump. :(

---

### Post by Tamil on 2006-10-03
:eek: No answers?

---

### Post by dannyboy79 on 2006-10-03
well, i am a newbie but according to your lspci -v, the machine is seeing your ethernet controller. you need to make sure the driver for it is loading as well. i wish i could you. did you go into system, admin, networking? does it show anything in there? you could try to deactivate, then activate your interface, which is normally eth0. What does /var/log/messages say? did you try to shut down and then restart your computer?

---

### Post by Iowan on 2006-10-03
> **Tamil said:**
> eth0: ERROR while getting interface flags: No such device This doesn't look good...
[http://www.ubuntuforums.org/showthread.php?t=234761&highlight=82540EM]("http://www.ubuntuforums.org/showthread.php?t=234761&highlight=82540EM") 
Here's a post about the 82540EM - but it isn't much help.

---

### Post by Tamil on 2006-10-04
Thanks for your replies.

I reinstalled Ubuntu today and it works fine. :-D

---

### Post by dannyboy79 on 2006-10-04
you shouldn't have done that only because if you lose your eth0 interface again I am sure you're not gonna want to reinstall everytime!!! next time you need to be more patient and let people help since you did ask for help.

---

### Post by Tamil on 2006-10-05
> **dannyboy79 said:**
> you shouldn't have done that only because if you lose your eth0 interface again I am sure you're not gonna want to reinstall everytime!!! next time you need to be more patient and let people help since you did ask for help.I agree. I tried to solve this problem for about a week but not able to solve.

---

### Post by Tamil on 2006-10-11
Reinstalled once again due to same problem. :-?

---

### Post by dannyboy79 on 2006-10-11
> **Tamil said:**
> Reinstalled once again due to same problem. :-?


why don't you make a backup of your root partition so you don't have to do a reinstall everytime if you're not gonna try to trouble shoot it to the fix. that way you won't lose all your progress. i have a feeling that your resolv.conf file is being overwritten therefore your losing your dns settings therefore firefox can't resolve the name to the ip address. example would be: you type in [www.gogle.com](www.gogle.com) and what firefox goes and gets is 65.326.23.11, that may not be the exact ip just an example. so before this happens again why don't you at least do one of these things, i am simply copying and pasting so it may contains words that don't make sense. let us know if this does it

No problem. There are three different ways to overcome our windows-centric router hardware and to force it to use your known isp nameserver addresses instead of the dns address inside the router.

Option 1. Add your known isp nameservers in your router's setup page.

or

Option 2. Create a working /etc/resolv.conf file with the nameservers of your isp as the first or only ones in the list. Then edit /etc/dhcp3/dhclient-script and look inside for the make_resolv_conf( ) function lines. Fool dhclient into not overwriting your custom resolv.conf by editing this usually very lengthy function to do nothing: ( I much prefer option 3 below since dhclient-script does not like typo's!)

make_resolv_conf( ) {
echo "doing nothing to resolv.conf"
}

( don't forget the { } braces! )

If you bring your interface down and up again, or just plain reboot, you'll see that your custom resolv.conf stays intact.

or

Option 3. I don't like editing dhclient-script directly, so the third way is to either prepend or supersede the resolv.conf file with your known good isp nameservers.

Edit /etc/dhcp3/dhclient.conf
(sudo gedit /etc/dhcp3/dhclient.conf) and just before the "request" line, add this if you want to prepend your isp nameservers and have your routers dns address at the bottom of the list in resolv.conf:

prepend domain-name-servers 123.45.678.90, 123.45.678.91;

(For multiple addresses, separate with a comma and don't forget the semicolon at the end)

Reboot or just bring your interface down and up again:
sudo ifdown eth0
sudo ifup eth0

This has been such a problem for my friends running other systems that I've created a little page for it at:
[http://www.greertech.com/nixnotes/dhcpfix.html](http://www.greertech.com/nixnotes/dhcpfix.html)

---

### Post by Tamil on 2006-10-12
Thanks. I made a backup of root partition. :-D 

Your link is dead.

---

### Post by dannyboy79 on 2006-10-12
> **Tamil said:**
> Thanks. I made a backup of root partition. :-D 

Your link is dead.


It wasn't my link, it was just something I copied from a Ubuntu thread that helps people fix the issue regarding the resolv.conf file being overwritten upon reboot due to dhcp. So, instead of either reinstalling or using your backup of /, if I were you I would try 1 of those options to ensure that your resolv.conf doesn't get overwritten which may be the cause of you losing internet conneciton. like i said, it could also maybe the ipv6 thing. also, do you have seperate partitions for your home directory or anything else, cause if you only made a backup of / and you have home on a seperate partition, you'll want to back that up also otherwise you'll lose all your personal settings and whatnot.

---

### Post by Tamil on 2006-10-12
> **dannyboy79 said:**
> do you have seperate partitions for your home directory or anything else, cause if you only made a backup of / and you have home on a seperate partition, you'll want to back that up also otherwise you'll lose all your personal settings and whatnot.I have separate home partition.

I will try your 3rd sugesstion.

---

### Post by dupa on 2006-10-24
tamil i have the same problem with Ubuntu 6.06 of my eth0 that disappeared.

I had this problem with ubuntu 6.06 (not the 6.06.1) and WITHOUT updates installed.

At the same time both eth0 disappeared and the ps2 mouse stopped to work.

Which version of ubuntu experienced this problems? did you run ever a ubuntu update on your ubuntu?

---

### Post by Tamil on 2006-10-24
> **dupa said:**
> I had this problem with ubuntu 6.06 (not the 6.06.1) and WITHOUT updates installed.For me Ubuntu 6.06 with updates.

[QUOTE=dupa]At the same time both eth0 disappeared and the ps2 mouse stopped to work.[/QUOTE]This happened last time.

---

### Post by dupa on 2006-10-24
do you remember what you did before rebooting on the last session the system worked correctly?
did you do anything strange?

---

### Post by Tamil on 2006-10-24
> **dupa said:**
> do you remember what you did before rebooting on the last session the system worked correctly?
did you do anything strange?My friend installed some programs before the problem. I don't know what he installed. First problem occurred with net connection and then mouse.

---

### Post by dupa on 2006-10-25
i have "lan adapter", "audio chip", "video chip" all integrated on the motherboard. do you have too a motherboard that integrates all of this stuff?
do you know what is the model of your motherboard?

---

### Post by Tamil on 2006-10-25
> **dupa said:**
> i have "lan adapter", "audio chip", "video chip" all integrated on the motherboard. do you have too a motherboard that integrates all of this stuff?
do you know what is the model of your motherboard?Sorry, I don't know.

---

### Post by dca on 2006-10-25
On the back of your PC, you should have anywhere between two and seven horizontal slots starting from the bottom.  If you connect anything into those slots (some have connectors, some have covers) that would be separate PCI cards for network, etc.  If you plug your ethernet cable and/or VGA cable into an area in the same proximity as the PS/2 connectors for the mouse & keyboard, your NIC & graphics is then integrated w/ the mobo...  Trying not to be technical...

---

### Post by dupa on 2006-10-26
The fact is that I (and Tamil) have hardware that is corrected recognized by ubuntu, because after the installation all works correcly, but for some strange reasons the ethernet and the ps2 stop to work.

So, without considering the reasons that caused this, is there a way to force them to work?

---

### Post by dupa on 2006-10-27
I found the soluzion for my problem.
I noticed that the depmod config files was empty..
I just executed:

```
sudo depmod
```

I rebooted and the eth0 work again :)

---

