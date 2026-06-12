---
title: "broke my laptop - again... :("
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-01-05
Hi All, 

I have been trying to get my stoopid headphones and microphone to work on my laptop running edgy (Compaq V3118AU). I have been searching for the answer for a couple of weeks now, to no avail. Today, I went into synaptic package manager, searched for ALSA, and installed everything that was related to ALSA. 

When I start my computer with the headphone and mic jacks in, I get a couple of extra options in the volume control, but only if they are in when the computer is started. So that hasn't worked.

Also, my internet doesn't seem to be working. I can connect to the wireless network, but I can't view any websites, or download any package info, so I think that something I have done has knocked out something important to do with the internet. :( 

Please could someone help first and foremost with the internet issue, then secondly with the headphoens microphone issue? 

Many Thanks

Patrick

(ps, using desktop to post this ;))

---

### Post by kolinab on 2007-01-05
Sorry I can't help you with the internet connection stuff, but I recently fixed my headphone/microphone problems on my laptop. Check to see if the following bug applies to your chipset as well:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42600](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42600)[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42600]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42600")

There's a link to the solution at the bottom of the page. Check the descriptions and discussion in the bug report and see if that sounds like you. If it is, and you don't know how to implement the solution described, post back here and I'll walk you through it. I had no idea for a while and finally put it together . . . really simple in the end!

Good luck!

---

### Post by zmuth734 on 2007-01-05
try **sudo dhclient eth1(or w/e your wireless is)**

Please post the result of **iwconfig** in the terminal

---

### Post by petermck on 2007-01-05
Is this a wifi AP at home? Are you on ADSL from there? What kind of machine are you using? Can you give a bit more info on what hardware you have and the general configuration of your network link?

---

### Post by ozPATT on 2007-01-05
Hi, 

I am using the home wireless network to connect to the internet. I am able to connect to the internet using ethernet from the modem, which is what I am doing now. I just removed the bcm43xx driver I was using for my card, and have installed the ndiswrapper driver as found in several tutorials! 

I have tried the sudo dhclient eth1 and iwconfig as sugested above, and this is my output:

> patrick@localhost:~$ sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:bb:a1:5c
Sending on   LPF/eth1/00:14:a5:bb:a1:5c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.111 -- renewal in 268653 seconds.
patrick@localhost:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"default"  Nickname:"default"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:2A:C5:46   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Does this telly uo anything interesting? Doesn't mean too much to me...

I have a signal for the wirless, full strength, so back to where i once was, with trying to get the connection to be used by my browser/email/messenger etc.

I will look at the headphone mic thing now, thanks for the link, i am fairly new to command line stuff, so i may well need help. thanks for the help so far, 

Patrick

---

### Post by ozPATT on 2007-01-05
kolinab, 

I had a look at the link, and went to amend the end of the alsa-base file, only to find that it already said what was being suggested. not sure if that is a default or if i already put thgat there earlier, but however it got there, my mic and headphones still dont work.

The following output maybe helpful?

> patrick@localhost:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
patrick@localhost:~$ 
patrick@localhost:~$ 
patrick@localhost:~$ 
patrick@localhost:~$ 
patrick@localhost:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43
  Mono:
  Front Left: Playback 31 [72%] [on]
  Front Right: Playback 31 [72%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 23
  Front Left: Capture 23 [100%] [on]
  Front Right: Capture 23 [100%] [on]


Should amixer list the two front jacks even if there is nothing plugged in to them? At the moment, it only lists them if I boot the computer with the mic/headphones plugged in. 

Thanks

Patrick

p.s., still no joy getting this wirless to talk.. :(

---

### Post by kolinab on 2007-01-05
Hmmm. I thought you might have had the same problem as me. 

Can you post the output of 

```

lspci  -v

```

That should give us more info on your sound adapter.

I'm not sure what amixer should show you about those jacks. I assume you've gone to Edit . . . Preferences in Volume Control and checked all the various checkboxes to see the levels of everything?

I bet you've already been inside alsamixer.

Go:

```

alsamixer

```

Then tab around inside there and turn the capture levels all the way up for everything. There might be an area to select different inputs. I'm not too sure what to tell you since I think the setup of this screen will be different depending on your configuration.

Hopefully once we see the output of lspci  -v we'll have more ammo for searching. Could be the chipset of your adapter exists on other machines out there . . . 

I'll check back to try to help but I'm really new to Ubuntu and linux myself - kind of groping in the dark! But maybe this thread will get some attention, I know how frustrating it is to not have a working mic and speakers.

---

### Post by kolinab on 2007-01-05
Hey - check this link - tons of info on that series of laptop.

[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A]("http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A")

Lots to digest there, I'm having a look.

---

### Post by ozPATT on 2007-01-05
Yeah, it is pretty frustrating as I am beginning to need skype for work, and so could do with getting it working - also is it just me or is skype without video in linux a bit of a disappointment?

Anyway, the output of lspci -v is as follows: (again, doesnt mean too much to me)

> patrick@localhost:~$ sudo lspci -v
Password:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: c3000000-c30fffff
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c8000000-c87fffff
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: [44] Power Management version 2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at c0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 3080 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at 30b0 [size=8]
        I/O ports at 30a4 [size=4]
        I/O ports at 30a8 [size=8]
        I/O ports at 30a0 [size=4]
        I/O ports at 3090 [size=16]
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        Memory behind bridge: c3100000-c31fffff
        Capabilities: [b8] #0d [0000]
        Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 58
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30b8 [size=8]
        Capabilities: [44] Power Management version 2

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1364
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint IRQ 0
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel

03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, medium devsel, latency 64, IRQ 233
        Memory at c3100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

03:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, medium devsel, latency 64, IRQ 50
        Memory at c3100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c3100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: medium devsel, IRQ 11
        Memory at c3101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: medium devsel, IRQ 11
        Memory at c3101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2


thanks

Patrick

---

### Post by ozPATT on 2007-01-05
also, with regards to the internet part of this question, I now can use the internet wirelessly, but it is intermittent. So, I can use it literally for about 2 minutes, then it cuts out for about 30mins. 

Is this to do with the ndiswrapper driver? the bcm43xx which apparently is not the right driver, although it had issues, wasnt as bad as what i am experiencing now - as it is right now it is practically unusable. any advice would be really greatfully received...

thanks

Patrick

---

### Post by kolinab on 2007-01-05
Hey,

Sorry you're still having trouble. The reason I had you post that output is because it tells us about your audio device. Now we know it's a nVidia MCP51 and can use this in our web searches.

If I have time I'll see if I can do some more searching today but I would recommend scouring that link I posted earlier re: the Compaq 3XXX series. There looked to be a lot of good information there, as well as links to informative threads on both your network problem and sound issues. And some other Compaq user is bound to come out of the woodwork!

---

### Post by petermck on 2007-01-05
I note you have a Broadcom Etherne card;
```
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 1364
Flags: bus master, fast devsel, latency 0, IRQ 233
Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 2
Capabilities: [58] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
Capabilities: [d0] Express Legacy Endpoint IRQ 0
Capabilities: [100] Advanced Error Reporting
Capabilities: [13c] Virtual Channel
```
Have a look at [http://www.leenooks.com/Broadcom+43XX]("http://www.leenooks.com/Broadcom+43XX"). I don't have a lot of experience with this card, but it sounds like your on the right track using Ndiswrapper. You may find some help at [http://bcm43xx.berlios.de/]("http://bcm43xx.berlios.de/") as well. Either stick with the Ndiswrapper approach, or use a Linux driver, whichever works best.
It looks like you have RTS and Fragmentation on,
```
RTS thr=2347 B Fragment thr=2346 B 
```. I would try it with lower values than this or off.
```
iwconfig eth1 rts 512
```
```
iwconfig eth1 frag off
```
see man iwconfig.
What make/model is the AP? I gather from the output of iwconfig your not using encryption. I would try turning off rts and frag first and see if things improve. By the look of your signal strength etc, you don't need these on.
Also, post the result from a ping to the AP.
```
ping 192.168.0.1
```

---

### Post by ozPATT on 2007-01-05
hi, i just tried to turn the rts and frag off, but that resulted in an error:
> patrick@localhost:~$ sudo iwconfig eth1 rts off
Error for wireless request "Set RTS Threshold" (8B22) :
    SET failed on device eth1 ; Invalid argument.


It did however let me set both to 512, so I did that. 

The results of the ping now are as follows:

> patrick@localhost:~$ ping 192.168.0.1 -c 4
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=1.28 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=1.14 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=1.06 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=127 time=1.12 ms

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 1.060/1.152/1.286/0.089 ms


@ kolinab: thanks for showing me what i was looking for! :D i will also have a search around for information on the nVidia MCP51

Many Thanks

Patrick

---

### Post by kolinab on 2007-01-05
Glad that I could help a bit. Hope you get things working. I guess that HP Wiki link I posted is probably the best resource I've found yet. There's a bunch of links there and since it's a Wiki there's got a to be a few people you can get in touch with on that page who should be able to help you more.

Good luck with it all,

K

---

