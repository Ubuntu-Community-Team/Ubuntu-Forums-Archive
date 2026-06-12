---
title: "wireless not working"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by jvanoort05 on 2007-03-30
my wireless looks like it is working but i can't conect to my wireless network. How do i do this?

---

### Post by overdrank on 2007-03-30
> **jvanoort05 said:**
> my wireless looks like it is working but i can't conect to my wireless network. How do i do this?

Hi could you tell us more about what your specs on you card is? Like what is the output of the command lspci in the terminal?

---

### Post by Maestro23 on 2007-03-30
Did you try what I suggested in your other thread?

[http://www.ubuntuforums.org/showthread.php?t=397248](http://www.ubuntuforums.org/showthread.php?t=397248)

---

### Post by jvanoort05 on 2007-03-30
for the second reply i am a new linux user and i don't now what you are talking about and for the 
 third reply my ethernet port is broken so i can only get internet through wireless and dialup therefore i can not download the ndiswrapper to easily but if you can point me to a bundle that includes every thing that i can download it on windowz and move it to ubuntu.

---

### Post by Maestro23 on 2007-03-30
> **jvanoort05 said:**
> for the second reply i am a new linux user and i don't now what you are talking about and for the 
 third reply my ethernet port is broken so i can only get internet through wireless and dialup therefore i can not download the ndiswrapper to easily but if you can point me to a bundle that includes every thing that i can download it on windowz and move it to ubuntu.

Try here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

If you ran that keyword search here on the forums, you will find some threads discussing your wireless nic.  Might put you on the path to solving your problem.

Good luck.

---

### Post by ricardisimo on 2007-03-30
Applications > Accessories > Terminal
Then type ```
lspci -v
``` in that terminal window, copy and paste in a reply to this thread. What version of Ubuntu are you on, by the way?

---

### Post by jvanoort05 on 2007-03-30
im using the 6.06 version

---

### Post by jvanoort05 on 2007-03-30
i typed that comand and it replyed with:
josh@DELL-UBUNTU:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=10, sec-latency=32
        I/O behind bridge: 0000e000-0000ffff
        Memory behind bridge: f4000000-fbffffff
        Prefetchable memory behind bridge: 20000000-23ffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03) (prog-if 80 [Master])
        Subsystem: Intel Corporation: Unknown device 4541
        Flags: bus master, medium devsel, latency 0
        I/O ports at bfa0 [size=16]

0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation: Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at dce0 [size=32]

0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 00e6
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at fd000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
        Subsystem: Dell ES1983S Maestro-3i (Dell Inspiron 8100)
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at ec00 [size=256]
        Memory at f8ffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:02:06.0 Communication controller: Agere Systems WinModem 56k (rev 01)
        Subsystem: Actiontec Electronics Inc: Unknown device 2000
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at f8ffdc00 (32-bit, non-prefetchable) [size=256]
        I/O ports at e8f8 [size=8]
        I/O ports at e400 [size=256]
        Capabilities: <available only to root>

0000:02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
        Subsystem: Dell PCI4451 PC card CardBus Controller (Dell Inspiron 8100)
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at f8000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: f4000000-f5fff000
        I/O window 0: 0000e000-0000e0ff
        I/O window 1: 00001000-000010ff
        16-bit legacy interface ports at 0001

0000:02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
        Subsystem: Dell PCI4451 PC card CardBus Controller (Dell Inspiron 8100)
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at f8001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 22000000-23fff000 (prefetchable)
        Memory window 1: f6000000-f7fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

0000:02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller (prog-if 10 [OHCI])
        Subsystem: Dell PCI4451 IEEE-1394 Controller (Dell Inspiron 8100)
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f8ffd000 (32-bit, non-prefetchable) [size=2K]
        Memory at f8ff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

---

### Post by jdoublep on 2007-03-30
Do you have WEP enabled on your wireless router?

---

### Post by jvanoort05 on 2007-03-31
what do you mean by WEP?

---

### Post by jdoublep on 2007-04-02
WEP=Wired Equivalent Privacy. It's a weak standard for encrypting wireless communications. 
You would probably be prompted for a key were it enabled, but you might log-in to your gateway just to double-check.

---

### Post by jvanoort05 on 2007-04-03
WEP is enabled on my wireless router but when i open the network proporties diolog box in ubuntu it does not display any SSID's. I typed my SSID in the box and filled out the password but is still does not connect?

---

### Post by wscheer on 2007-04-03
jvanoort05,
Do you know if your wireless routers is broadcasting its "SSID"?
There should be a Yes/No radio button for "Broadcast SSID" somewhere in your wireless settings.

That might help determine if your wireless card in you computer is working.
You can always set the Broadcast SSID back to No when your done checking.

---

### Post by jvanoort05 on 2007-04-03
Yes is is brodcasting my SSID and when i tried the Starbucks Hotspot it still never worked.

---

### Post by Scwounch on 2007-04-03
I was about the same problem.  The network utility that comes with Ubuntu doesn't make it clear that it is searching for broadcast SSIDs, if it is.  I was never able to get my network card to work.  Luckily I had just bought it, so I was able to return that sucker.  Though it seems like your network card is installed (it shows up in that network manager thingy) it really is using the wrong driver.  I'd recommend searching your card's make and model in the help.ubuntu.com community section.  See if anyone else has worked with your particular card before.  If not, there's always ndiswrapper and it's GUI you can try with the Windows drivers.  Sorry I couldn't help too much.  I just gave up on mine.

---

