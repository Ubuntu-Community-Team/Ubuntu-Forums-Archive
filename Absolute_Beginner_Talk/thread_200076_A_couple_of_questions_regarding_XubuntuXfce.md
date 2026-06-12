---
title: "A couple of questions regarding Xubuntu/Xfce"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Jozef on 2006-06-19
After some computer upgrades, I was able to install Xubuntu.  I even managed to learn a thing or two, and hopefully I'll move out of the newbie status soon.  Before that, however, I would appreciate if someone could help me with a few issues:

1. I wanted to add some shortcuts to the Applications menu.  I was told to open the Menu Editor.  After I tried that, nothing opened, but since then the Applications menu (either clicking on it or right-click) doesn't open.  Is there any way I can reenable it?

2. Despite the fact that I increased my RAM to 256MB, Xfce is very slow and occassionally crashes to command prompt.  I suspect a hardware issue.  Is there any way to check the hardware the Xubuntu is seeing?  I was told to use System Monitor from the Applications menu, but there was no such thing.  I was also told to use lspci, but without being able to open the Applications menu I don't know how to open a Terminal window.

3. Is there anything like a session log in Xubuntu or Xfce?  Sometimes, a program shuts down without warning, and I'd like to know what went wrong.

Thanks!

---

### Post by K.Mandla on 2006-06-19
1. That was a really nasty bug that got me too. I think it has been corrected in the updates; if you can't update, try the trick listed [here]("https://launchpad.net/distros/ubuntu/+source/xfce4/+bug/47776"). 

2. There should be a system monitor under Applications > System ... but then again, if your Applications menu was eaten, you'll have a tough time finding that. ;) Try CTRL+ALT+F1 (or F2 or F3 ... F7 to go back to the GUI), which should give you tty windows. 

Sorry I can't give more details. ... I'm one foot out the door. ... #-o

---

### Post by nalmeth on 2006-06-19
Can you right-click on the desktop? This is supposed to bring up the menu, but it may be disabled by default.

You can always CNTL-ALT-F1 to a virtual terminal screen, and CNTL-ALT-F7 to get back.

Sounds like video issue maybe, xubuntu is fast on my 128 megs of ram.

Did you install video drivers if you have ati or nvidia?

---

### Post by Jozef on 2006-06-19
**K.Mandla:** Many thanks; that solution did the trick!  And I learned something new in process :)

**nalmeth:** The right-click didn't work, either.

As far as my hardware goes, I've got ATI.  It did recognize my Rage Pro card, however, so I thought the drivers were installed, and didn't install anything myself.  However, as I'm not getting any sound and lspci shows two unidentified devices, my next question was to be how to install sound drivers, and what to do with the devices.  Searching through the forum has yielded plenty of results on those devices, but people were always talking about something else on the list, so I'm still clueless.  So here's my lspci output, and I'd be very grateful if you could tell me what to install in order to make the system more stable:

> 0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
        Subsystem: ALi Corporation ALI M1541 Aladdin V/V+ AGP System Controller
        Flags: bus master, slow devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: 80400000-804fffff
        Prefetchable memory behind bridge: 80500000-820fffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at 82100000 (32-bit, non-prefetchable) [size=4K]

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev b5)
        Subsystem: Unknown device 4341:5245
        Flags: bus master, medium devsel, latency 0

0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20) (prog-if 8a [Master SecP PriP])
        Subsystem: Unknown device 4341:5245
        Flags: bus master, medium devsel, latency 32, IRQ 14
        I/O ports at 7400 [size=16]

0000:00:14.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: Linksys: Unknown device 0574
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 7000 [size=256]
        Memory at 80100000 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at 80120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo AGP 2X
        Flags: bus master, stepping, medium devsel, latency 32
        Memory at 81000000 (32-bit, prefetchable) [size=16M]
        I/O ports at 8000 [size=256]
        Memory at 80400000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 80420000 [disabled] [size=128K]
        Capabilities: <available only to root>

---

### Post by Xzallion on 2006-06-20
You will need to install the ATI drivers, because its using a default driver (I believe).  That should speed up your video problems.  The [Dapper WIKI]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28ATI.29")  has some links along with some other helpful info.  Hope that helps.

---

