---
title: "[SOLVED] Absolutely NO SOUND!"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by 4l13n666 on 2008-02-28
Hi,

I'm an extremely new user to Ubuntu as well as to Linux. I don't know much about how to Use Ubuntu at all.
I have installed Ubuntu before on my Desktop computer and i had no problems with it whatsoever except i didn't know how to play games using Wine. But that is not my problem.

My problem is that i cannot hear any sounds whatsoever. No system sounds, no Ubuntu log on sounds, no MP3 music files, no movies, NOTHING! 
When i installed Ubuntu 7.10 on my desktop i had no problems with the sound at all. But when i installed Ubuntu 7.10 on my laptop, the problems came dropping down on me like a bomb. I have tried enabling and disabling all possible options in the "Sound" tab under preferences with no success at all. I am using HP Pavillion dv6500. I don't know what sound card i am using, and i don't know if Ubuntu has detected my sound card.

How can i find out what sound card that i am using? Are there any terminal commands?
How am i going to get my sound to work?
Do i need any drivers installed? If so, how do i install them? I need a very detailed description of how to do this.

When i open my BIOS i can't find any tab saying anything along the lines "Enable sound device" or such.

I really need help with this as soon as possible. I am very content with the performance and GUI of Ubuntu and i would love to continue using it. I don't want to be forced to switch back to Microsoft Windows Vista or XP, or any other OS. 

Things that will help me are any "SUDO" commands which can be entered in the "Terminal" that will help me to get my sound to work.

I need urgent help with this!

---

### Post by celticbhoy on 2008-02-28
Open a terminal & run 'alsamixer' you should then have control of your sound output

---

### Post by kellemes on 2008-02-28
> **celticbhoy said:**
> Open a terminal & run 'alsamixer' you should then have control of your sound output

Indeed, try this first..

A little reading in case this doesn't work..
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by 4l13n666 on 2008-02-28
Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ID 268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]                                            &#9474;
&#9474;                                                                              &#9474;
&#9474;           &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                                              &#9474;
&#9474;           &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;            &#9474;
&#9474;                                             &#9474;MM&#9474;             &#9474;MM&#9474;            &#9474;
&#9474;                                             &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;            &#9474;
&#9474;         100<>100           0<>0                                              &#9474;
&#9474;        < Master >          PCM            Caller I         Off-hook          &#9474;



This is what i get when i run the "Alsamixer" in the Terminal. Now how do i use this?:confused:

---

### Post by kellemes on 2008-02-28
First try "alsaconf".
This will try to detect and configure your card.


For alsamixer.. see to it the channels are not muted by pressing "M" when on a channel (I believe)
[http://en.wikipedia.org/wiki/Alsamixer](http://en.wikipedia.org/wiki/Alsamixer)
[http://alsa.opensrc.org/Alsamixer](http://alsa.opensrc.org/Alsamixer)

---

### Post by celticbhoy on 2008-02-28
I'm sure you just use the arrow keys to move between and set levels

---

### Post by 4l13n666 on 2008-02-28
> **kellemes said:**
> Indeed, try this first..

A little reading in case this doesn't work..
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I'm sorry, but i have tried using the information on that page you suggested several times, but i don't understand how to use most of the features and some of the terminal commands provided in the guide don't work, or they don't do anything whatsoever.

---

### Post by sneeks on 2008-02-28
hi there,have you tried opening your sound from the desktop and disabling digital,what i mean is uncheck the box,and then you should have sound
...

---

### Post by northern lights on 2008-02-28
Can you please post the output of ```
cat /proc/asound/cards
``` Thank you.

---

### Post by 4l13n666 on 2008-02-28
> **northern lights said:**
> Can you please post the output of ```
cat /proc/asound/cards
``` Thank you.


 cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8400000 irq 23

---

### Post by 4l13n666 on 2008-02-28
> **sneeks said:**
> hi there,have you tried opening your sound from the desktop and disabling digital,what i mean is uncheck the box,and then you should have sound
...

Which box do you want me to uncheck and where can i fin this box? Under which menu?

---

### Post by sneeks on 2008-02-28
i will re-word earlier post.....
had this myself today,and someone put me right,right click on the speaker in gnome,open sound and click on switches,uncheck the digi/anolouge box,it may give you the answer.

---

### Post by northern lights on 2008-02-28
Intel's HDA controller's have been a bit of trouble in Ubuntu for a while.

I'm sorry to ask you to post one more output, but unfortunately, your "/proc/asound/cards" did not reveal the info I wanted (of which ICH family is your card?). Can you also post the part of ```
lspci -v
```
that reads "Multimedia audio controller"?

For now, you might wanna check out this [HowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by 4l13n666 on 2008-02-28
I right clicked on the speaker box in the top right corner of the desktop and i disabled all options avaliable under the "switches" tab. Nothing made a difference.

---

### Post by 4l13n666 on 2008-02-28
> **northern lights said:**
> Intel's HDA controller's have been a bit of trouble in Ubuntu for a while.

I'm sorry to ask you to post one more output, but unfortunately, your "/proc/asound/cards" did not reveal the info I wanted (of which ICH family is your card?). Can you also post the part of ```
lspci -v
```
that reads "Multimedia audio controller"?

For now, you might wanna check out this [HowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Sorry for pasting such a long copy-paste thread but this is all i found, and since i found so much, i decided to post everything in order to give all information avaliable.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00007fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00008000-0000bfff
        Memory behind bridge: bc000000-bfffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f8000000-f80fffff
        Prefetchable memory behind bridge: 00000000a4000000-00000000a40fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: medium devsel, IRQ 10
        Memory at a4100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation PRO/Wireless 3945BG Network Connection
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c000 [size=256]
        Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at a4000000 [disabled] [size=128K]
        Capabilities: <access denied>

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at f8100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by sneeks on 2008-03-02
hi ,i have just checked for your sound card,and it is the dreaded realtek hi-def card.
i have had trouble with this one even when downgrading to xp for people!!!!
hp have the vista driver on their site so you maybe able to use ndis wrapper for this,but dont quote me on this one,someone with more knowledge on this will be able to tell you me thinks. 
p.s. there is also the xp driver on the toshiba site as they also use this card.

---

