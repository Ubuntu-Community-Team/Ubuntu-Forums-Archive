---
title: "How to troubleshoot a problem?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by _Dan on 2006-10-23
Hi,

Main question: How do I go about troubleshooting a problem? Like, where do I look for error messages?

The problem is my family's ubuntu machine keeps freezing up. For no apparent reason. It started doing it a few days ago, the only prominent event around the time was they tried to play a DVD, which froze the system and crashed. But that may not be the cause. It may have been the problem which caused the DVD to freeze...

Another thing, the machine is 300 miles away so I have to fix it over ssh or hopefully remote desktop if I get that working.

Thanks,

Dan

---

### Post by aysiu on 2006-10-23
Freezing... Hm.

Do you have the proper drivers installed (Nvidia, for example)?

---

### Post by _Dan on 2006-10-23
Yes, ATI, although I know some updates to it have been broken (openoffice problems...) but never causing freezing before.

---

### Post by skymt on 2006-10-23
Yours is hands-down the hardest problem to debug, mostly because you often have no idea where to start.

Debugging is mostly knowing the right questions to ask (yourself, or the person you're helping). Here are some suggestions:

* How often does it freeze?
* Is freezing associated with an application or activity?
* When it freezes, can you move the mouse, use the keyboard, or switch to a virtual terminal (Ctrl-Alt-F1)?
* Does it "melt"? That is, does the freeze go away if you let it chew for a while?

Some places you may want to look:

/var/log/syslog  - This is the big one. Almost everything logs here.
/var/log/Xorg.0.log  - Xorg is one common source of freezing problems.
/var/log/kern.log  - Pray nothing goes wrong here. ;) 
/var/log/dmesg  - Mostly hardware and boot issues are logged here.
~/.xsession-errors  - If something goes wrong in a user application, it will log here.

Make sure to look at these as soon as possible after the crash.

Since you have ssh access, you may want to see if you can log in during a freeze event. It may be just X that freezes, and it locks up the input while it's at it. That would be ideal in this situation, since you would have access to the machine while the problem is occurring.

---

### Post by _Dan on 2006-10-29
It's proving really difficult to even get to look at it as it freezes usually within a few minutes of start up. ssh freezes too. But I finally managed to get the logs before it froze.

syslog only contained these lines
> Oct 29 12:16:12 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct 29 12:16:12 localhost anacron[4709]: Job `cron.daily' terminated
Oct 29 12:16:12 localhost anacron[4709]: Normal exit (1 job run)
Oct 29 12:17:01 localhost /USR/SBIN/CRON[5596]: (root) CMD (   run-parts --report /etc/cron.hourly)

The only obvious thing in Xorg.0.log is

> drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
repeated many times with the card number increasing.
Full log is here: [http://xzist.org/temp/Xorg.0.log](http://xzist.org/temp/Xorg.0.log)

Looking at kern.log, [http://xzist.org/temp/kern.log](http://xzist.org/temp/kern.log)
> Oct 28 22:36:44 localhost kernel: [17179619.424000] Bluetooth: Core ver 2.8
Oct 28 22:36:44 localhost kernel: [17179619.424000] NET: Registered protocol family 31
Oct 28 22:36:44 localhost kernel: [17179619.424000] Bluetooth: HCI device and connection manager initialized
Oct 28 22:36:44 localhost kernel: [17179619.424000] Bluetooth: HCI socket layer initialized
Oct 28 22:36:45 localhost kernel: [17179619.464000] Bluetooth: L2CAP ver 2.8
Oct 28 22:36:45 localhost kernel: [17179619.464000] Bluetooth: L2CAP socket layer initialized
Oct 28 22:36:45 localhost kernel: [17179619.472000] Bluetooth: RFCOMM socket layer initialized
Oct 28 22:36:45 localhost kernel: [17179619.472000] Bluetooth: RFCOMM TTY layer initialized
Oct 28 22:36:45 localhost kernel: [17179619.472000] Bluetooth: RFCOMM ver 1.7

Seems to occur before each freeze. But maybe that is part of the boot or something? Because on the last line something occurs 5 minutes after this so it couldn't have caused the crash.

going by the times between log entries freezes occurred sometime after Oct 28 21:18:44, Oct 28 21:57:08, Oct 28 22:14:23, Oct 28 22:25:35, Oct 28 22:36:45
and before those dates too.

Also dmesg [http://xzist.org/temp/dmesg](http://xzist.org/temp/dmesg) does not seem to me to contain any errors.

Mouse, keyboard etc. cannot be used after a freeze. But the screen still displays.

Other possibly important things:

- it dual boots with windows 98. This also has the freezing problems (so I am told), I suppose they could have the same cause. Would this mean it is a hardware problem?

- freezing generally occurs within 5-10 minutes of startup
- often when it freezes it will not boot again for a while, 15 minutes or more as a guess (I think it freezes on the boot progress thing, i'm not sure where abouts although I could ask if it's important)

If you have any insights please let me know. Thanks.

---

### Post by dannyboy79 on 2006-10-30
i have this same problem lately. i don't understand why either, here is my lspci -v info, I run a p4 celeron 2.66ghz with 512mb ram.

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [c0] AGP version 3.5

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 128, IRQ 129
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 4000 [size=16]
        Capabilities: [58] Power Management version 2

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 129
        I/O ports at e000 [size=256]
        I/O ports at e100 [size=128]
        Capabilities: [48] Power Management version 2

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 145
        Memory at eb027000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 153
        Memory at eb028000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 161
        Memory at eb029000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 7002
        Flags: bus master, medium devsel, latency 32, IRQ 169
        Memory at eb024000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, medium devsel, latency 32, IRQ 137
        I/O ports at e200 [size=256]
        Memory at eb025000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2

0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01) (prog-if 85 [Master SecO PriO])
        Subsystem: Foxconn International, Inc.: Unknown device 0c56
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 121
        I/O ports at e300 [size=8]
        I/O ports at e400 [size=4]
        I/O ports at e500 [size=8]
        I/O ports at e600 [size=4]
        I/O ports at e700 [size=16]
        I/O ports at <unassigned>
        Capabilities: [58] Power Management version 2

0000:00:08.0 FireWire (IEEE 1394): Texas Instruments FireWire Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Texas Instruments: Unknown device 8010
        Flags: bus master, medium devsel, latency 32, IRQ 121
        Memory at eb026000 (32-bit, non-prefetchable) [size=2K]
        Memory at eb020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 1

0000:00:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR-350
        Flags: bus master, medium devsel, latency 32, IRQ 129
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc.: Unknown device 2144
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 113
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0

I unfortunately haven't been able to look at any logs after a freeze because I never thought about it before. The display is still up and I can move the mouse around but I can't click on anything, or I should say that mouse clicking doesn't do anything! I read somewhere that I could hit shift f1 or somthing like that and that would bring up a command line so I could open a terminal command but shift f1 opens another workspace I think so I can't remember how to try to bring up a terminal so that I could do some ps aux and then try to kill some processes? Can anyone tell me how I would try to bring up a terminal when I can't use my mouse to click anywhere? THen I always just hit control, alt, backspace to solve this and it just restarts my x server, at least I think that's what this does because I have to re login then. Please help anyone as I am trying to use ubuntu as a media and ftp server, as well as just trying to learn linux as a desktop os. Thanks

---

### Post by _Dan on 2006-10-31
If the mouse moves and ctrl+alt+backspace works then it ISN'T the same problem. So how about you start a separate thread.

> Oct 29 21:14:27 localhost -- MARK --
Oct 29 21:17:01 localhost /USR/SBIN/CRON[5746]: (root) CMD (   run-parts --report /etc/cron.hourly)
Oct 29 21:34:28 localhost -- MARK --


These are the last three lines in the messages log before a crash, what does the -- MARK -- mean?

---

### Post by Bartender on 2006-10-31
Maybe it's not software.  Can you get into BIOS and let it sit for a few hours?  See if it crashes then?  That's not a great test, because if it's a failing power supply or overheating the problem might not arise until the PC is doing some work.

---

### Post by bsussman on 2006-10-31
> **_Dan said:**
> what does the -- MARK -- mean?

Mark  messages are logged to show that parts of the system were alive and capable of logging - note they occur on a regular schedule.

They are no more than 'I am alive' messages.

---

### Post by podunk on 2006-10-31
The fact that Win 98 has the same problem suggests to me a hardware issue. Or maybe a bad setting in the BIOS( though usually BIOS problems prevent booting at all). You mentioned that you have to wait before you can restart.

Why don't you have them get a can of air and open the cover (unplug it first!) and dust everything out real well.Pay special attention to the heatsink and power supply.

Maybe wiggle stuff while in there to see if anything is lose, like a stick of ram or a PCI card for instance. 

Power up and boot up the system while the case is open (no gerbils or cats allowed in the room while doing this). Do all the fans spin good? Is there a nice draft out the back of the power supply?

Leave the case open for a bit - if the problem goes away you have a heat issue, add fans, replace the power supply, stuff like that.

---

### Post by skymt on 2006-10-31
Another idea for nailing down the problem: run a memory test. Ubuntu has a great memory tester built in. Just reboot, and at the grub screen, choose memtest86+. If it says you have bad RAM, that's probably your problem. The solution in that case is to buy new RAM, or just take out the bad stick and make do with less.

---

