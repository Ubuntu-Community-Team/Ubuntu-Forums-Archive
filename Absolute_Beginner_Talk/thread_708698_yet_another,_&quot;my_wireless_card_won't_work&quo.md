---
title: "yet another, &quot;my wireless card won't work&quot; question"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Fistofpaper on 2008-02-26
I've been spending a good amount of time on this, learning my way around my brand new Ubuntu install; how to install packages, work in terminal, etc. I'm still to new however to fix my problem myself, and there doesn't seem to be anything specific enough to my issue to help with online resourcing.

That said, I've a Linksys Wireless G+Speed Boost PCI adapter (WMP54GS) that I just cannot for the life of me get to install and load. I have ndiswrapper 1.52 running properly and I get all the way to the driver being loaded, but there are two things that I am expecting to happen that don't.

1) I only get the message that the driver is loaded, not that the hardware is present even though it appears in hardware configuration.
2) when I attempt to use "modprobe ndiswrapper" nothing happens. I get no message that the driver is loaded, or message that there is something wrong with what I've done.

i'm pretty much stuck here. I've been slogging through on my own for bits of time over a week now, making it a little project to get Ubuntu working the way it should so I can actually try it out properly with no luck. any thoughts on what is getting lost in translation? :guitar:

---

### Post by northern lights on 2008-02-26
For now, you could try the se two resources:
[Linksys WMP54GS with Broadcom BCM4306 chipset under Linux 2.6 kernel]("http://dossy.org/archives/000110.html") (blog entry)
[How to install linksys wireless-g pci adapter with speedbooster]("http://ubuntuforums.org/archive/index.php/t-618759.html") (Ubuntu forums archive, November '07)

[EDIT]
Also, could you post the output of```
cat /proc/network/interfaces
``` and maybe ```
lspci -v
```
[/EDIT]

---

### Post by anewguy on 2008-02-26
Once you have loaded the drivers with ndiswrapper there are just a couple of steps afterwards.  If you aren't sure your driver loaded correctly, use sudo ndiswrapper -e xxxxx (where xxxxx is the name of the driver that shows via ndiswrapper -l) until no list is returned, then retry loading with ndiswrapper.

After loading the driver:

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

You may also want to (via gksudo) edit the /etc/modules file and add ndiswrapper to the end of it - this will assure ndiswrapper is started on a reboot.

When you have done all the above, reboot.

When the system is back up, click your network icon and see if any wireless networks show, then post back here.

:)

EDIT:  Since the above poster is suggesting a bcm4306 driver, you will need to (via gksudo) edit the /etc/modprobe.d/blacklist file and add this to the end of the file:

blacklist bcm43xx

then save the file and reboot.  This will stop the included driver (really a skeleton, not a working item) from overriding your driver.

---

### Post by Fistofpaper on 2008-02-26
I will follow those suggestions this evening and get back with the results. I had used the Dossy's blog post as well as some other resources to get as far as I did working it out on my own.

---

### Post by TheMilitia on 2008-02-26
I just got mine working a few days ago, then screwed something up, re-installed linux, got my wireless working again, repeat like 3 times. 

So, on to the problem. The number one thing to check is to see if there are multiple ".sys" files that got loaded into the "/etc/ndiswrapper/-filenameofyourdriver-/" folder. If there are, move the ones you don't need, which could take some trial and error. Which means, do not delete these files until you get the correct one working. The ".sys" file should be the model number of your wireless card.

---

### Post by Fistofpaper on 2008-02-27
I'm posting this from the Ubuntu side of my boot disk, so it is now working.

Oddly enough, it was the help thread written by the 12 yo crack monkey that got it loaded; I am glad I learned more terminal etc while trying this, as it's helped immensely in my understanding of the OS.


Now to really mess with things and load Kubuntu and attempt to get it working with WPA.

---

### Post by Fistofpaper on 2008-02-27
> **northern lights said:**
> For now, you could try the se two resources:
[Linksys WMP54GS with Broadcom BCM4306 chipset under Linux 2.6 kernel]("http://dossy.org/archives/000110.html") (blog entry)
[How to install linksys wireless-g pci adapter with speedbooster]("http://ubuntuforums.org/archive/index.php/t-618759.html") (Ubuntu forums archive, November '07)

[EDIT]
Also, could you post the output of```
cat /proc/network/interfaces
``` and maybe ```
lspci -v
```
[/EDIT]

demon@demon-desktop:~$ cat /proc/network/interfaces
cat: /proc/network/interfaces: No such file or directory
demon@demon-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 8
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
        Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
        Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: f9000000-fbefffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Linksys WMP54GS version 1.1 [Wireless-G PCI Adapter]  802.11g w/SpeedBooster
        Flags: bus master, fast devsel, latency 64, IRQ 22
        Memory at f8ffe000 (32-bit, non-prefetchable) [size=8K]

00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at ec00 [size=8]
        I/O ports at e880 [size=4]
        I/O ports at e800 [size=8]
        I/O ports at e480 [size=4]
        I/O ports at e400 [size=16]
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d880 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at d480 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at f8ffdc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 81b5
        Flags: medium devsel
        Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. Unknown device 337e
        Flags: bus master, medium devsel, latency 128
        Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fbf00000-fbffffff
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 820b
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at fbee0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81e7
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

demon@demon-desktop:~$

---

### Post by northern lights on 2008-02-27
You got it workin', right?

Then I didn't quite need that output anymore... :)

Or did I understand that incorectly?

---

### Post by Fistofpaper on 2008-02-27
it's workin', now to get the vid card installed and find out why i keep getting an error loop when i try to install ubuntu-restricted-extras.

**[EDIT] Fixed that too, and had a V-8 moment[/EDIT]**


I'm beginning to think Linux is good for a project or hobby, but not as an alternative OS. Kinda like replacing your stereo with an electronics kit you buy at Radio Shack. Sure, you can get it to work with TLC and gobs of knowledge, but is the effort worth it aside from something to stimulate the mind?:lolflag:

**[EDIT]This was borne of frustration, as Linux is like learning a new language. Each language has it's own syntax/grammar and the only way to really learn it is to "think" it, not translate it back and forth. I had been falling under the latter there, when I wanted to be "thinking" it. Sorry if that comment came off as rude. I really appreciate the help ;) [/EDIT]**

---

