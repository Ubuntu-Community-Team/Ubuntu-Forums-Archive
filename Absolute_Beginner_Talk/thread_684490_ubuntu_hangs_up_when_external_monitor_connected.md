---
title: "ubuntu hangs up when external monitor connected"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by loginjacek on 2008-02-01
Can not boot laptop (Dell Inspiron 1000) when external monitor  plug is connected to it. System hangs up when screen with the ubuntu logo is displayed at about 2/3 of the loading progress. If I connect external monitor (Samsung TV) is connected while system is on it displays half of the screen with the other half being displayed on laptop screen.
First of all I need to deal with system hang ups (its crazy to disconnect monitor each time when want to reboot). Can anybody advice?
Then would like to set both screens so they display full view - at the 'Screen and Graphic preferences' window 'Mirror default screen' option can not be activated.
Lastly I like to keep external monitor on when laptop lid is closed. At the moment it goes black same as laptop screen

---

### Post by Fizzzy on 2008-02-01
If i'm reading this right, it's showing half of the screen one one side and half on another (Like the other half of the screen or something), or it thinks you want to have a dual monitor setup.
I'm pretty sure it's the second one, but i'm just posting to see if I can get your question right so I can try to answer it ;)

---

### Post by loginjacek on 2008-02-05
Its the first one of two scenarios you described. Half of the screen is shown on external monitor and second half on laptop monitor, so I can drag the mouse from one screen to the other. In the SYSTEM -> ADMINISTRATION ->   SCREEN AND GRAPHICS window; SCREENS tab I Screen1 which is laptop display is set as 'Default screen' and when marking Screen2 as 'Secondary screen' the option to 'Mirror default screen' is not accessible (is highlighted in grey rather than in bllack), 'Extend default screen' is automatically made active and that's the only mode available except disabling it. See attached screen shoot.

How about not being able to boot when external monitor plug connected. Welcome screen freezes at about two third of a progress bar and is not showing progress for several minutes after that, so have to power laptop off.. When external monitor plug disconnected laptop boot as normal. This seems serious, does anybody have an idea what could it be?

---

### Post by ayenack on 2008-02-05
What graphics card are you using? To find this out do this in terminal.

lspci -v

It'll have VGA compatible controller: at the begin of the graphics card section with the name of the graphics card afterwards.

---

### Post by loginjacek on 2008-02-07
See graphic card:

VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 0195
        Flags: 66MHz, medium devsel, IRQ 7
        BIST result: 00
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e4300000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 9000 [size=128]
        Capabilities: <access denied>

---

### Post by ayenack on 2008-02-07
That's a problem. As far as I know  there are not Linux drivers for this chipset that allow hardware acceleration at the moment so setting up dual screen won't be possible I don't think. I could be wrong about this but I don't think so. Have you tried Restricted Drivers Manager to see if there are any drivers listed?

---

### Post by loginjacek on 2008-02-10
Thanks, a least I know what's on

---

