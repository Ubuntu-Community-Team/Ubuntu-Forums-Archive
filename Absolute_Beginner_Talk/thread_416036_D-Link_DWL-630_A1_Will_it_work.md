---
title: "D-Link DWL-630 A1 Will it work???"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by connec2jim on 2007-04-20
Hello everyone, I have Fiesty Fawn and im trying to get my wireless card working. I downloaded the latest driver 0.9.3 and  I was trying to understand the concept of Being "In A Directory".  It says in source forge that I need to type MAKE when I'm in the "madwifi directory":confused: .Thanx

---

### Post by chamberlain2006 on 2007-04-20
I don't really know much about the specifics of your card, but looking on the Madwifi website, it doesn't seem to be compatible with that driver.  You'll probably have to use NdisWrapper.  Can you please post the output of "lspci -v".  To do this, go to Applications>Accessories>Terminal and type it in.

---

### Post by connec2jim on 2007-04-20
This is what i got: 
jim@jim-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at d0500000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin USB
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Audio
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 8400 [size=256]
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
        Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Modem Device
        Flags: medium devsel, IRQ 3
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8800 [size=256]
        Capabilities: <access denied>

00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
        Subsystem: Hewlett-Packard Company Unknown device 0024
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if b0)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin IDE
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 8080 [size=16]
        Capabilities: <access denied>

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Hewlett-Packard Company Pavilion ze4400
        Flags: medium devsel

00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network
        Flags: bus master, medium devsel, latency 90, IRQ 11
        I/O ports at 8c00 [size=256]
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 38000000 [disabled] [size=64K]
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Video
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by chamberlain2006 on 2007-04-20
Seems your card isn't a PCI card, probably should have asked.  Sorry, now do lsusb please :)

---

### Post by connec2jim on 2007-04-20
My card is a pcmcia card.  my laptop has two usb ports and only one being used right now jim@jim-laptop:~$ lsusb
Bus 001 Device 002: ID 0d62:a100 Darfon Electronics Corp. Benq Mouse
Bus 001 Device 001: ID 0000:0000  
jim@jim-laptop:~$   I didnt have the card plugged in when i ran the first command you gave but the following is WITH the card plugged in. Sorry:( 


jim@jim-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at d0500000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin USB
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Audio
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 8400 [size=256]
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
        Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Modem Device
        Flags: medium devsel, IRQ 3
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8800 [size=256]
        Capabilities: <access denied>

00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
        Subsystem: Hewlett-Packard Company Unknown device 0024
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if b0)
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin IDE
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 8080 [size=16]
        Capabilities: <access denied>

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Hewlett-Packard Company Pavilion ze4400
        Flags: medium devsel

00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network
        Flags: bus master, medium devsel, latency 90, IRQ 11
        I/O ports at 8c00 [size=256]
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 38000000 [disabled] [size=64K]
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Video
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <access denied>

jim@jim-laptop:~$

---

### Post by chamberlain2006 on 2007-04-20
Ok, wish I knew it was PCMCIA.  Anywho, now, last "ls" command.  Now do lspcmcia.  (See the pattern?  lspci for pci, lsusb for usb, lspcmcia for pcmcia!).  Post that output please.

---

### Post by connec2jim on 2007-04-20
yes i see what u mean about the different commands  jim@jim-laptop:~$ lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.0)
jim@jim-laptop:~$

---

### Post by chamberlain2006 on 2007-04-20
Ok, well I'll take your word that it's there.  We need to install a program that wraps around the Windows wireless driver.  It's called ndiswrapper.  You will need a wired internet connection for this.  To install it, do the following commands in terminal.

sudo apt-get install ndiswrapper-utils-1.8 ndiswrapper-common

(Unless you're using Feisty, in which case you use ndiswrapper-utils-1.9)

ndiswrapper -v

Make sure that the version is all good.

Now, copy the drivers from your CD.  You'll need to copy them to your home directory, and then install them.  To do so, do the following:

sudo ndiswrapper -i <FILENAME.INF>

Now, make sure it's installed properly:

sudo ndiswrapper -l

It should show something like: driver installed, hardware installed.  If it doesn't, try using the other .inf file that was on the CD (if any).

Now, we'll save the configuration.

sudo ndiswrapper -m
sudo modprobe ndiswrapper

Now we'll make sure that the module is all loaded and configure it.

sudo iwconfig

It should show wlan0.  Now set the Network Name.

sudo iwconfig wlan0 essid "YOUR ESSID"

And start the card:

sudo ifup wlan0

You should be all set.  Let me know!

---

### Post by connec2jim on 2007-04-20
The .INF file that was in the windows drivers was a text file and when I tried to use it I got a message that there was no such file and no such directory, but the .INF file was in the same place as the executable that I ran.   
jim@jim-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common 
Password: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Suggested packages: 
  ndiswrapper-source 
The following NEW packages will be installed: 
  ndiswrapper-common ndiswrapper-utils-1.9 
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded. 
Need to get 50.1kB of archives. 
After unpacking 225kB of additional disk space will be used. 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main ndiswrapper-common 1.38-1ubuntu1 [18.0kB] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main ndiswrapper-utils-1.9 1.38-1ubuntu1 [32.1kB] 
Fetched 50.1kB in 1s (47.3kB/s)              
Selecting previously deselected package ndiswrapper-common. 
(Reading database ... 134098 files and directories currently installed.) 
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ... 
Selecting previously deselected package ndiswrapper-utils-1.9. 
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ... 
Setting up ndiswrapper-common (1.38-1ubuntu1) ... 
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ... 
jim@jim-laptop:~$ ndiswrapper -v 
utils Error: no version specified! 
driver version:        1.38 
vermagic:       2.6.20-15-386 mod_unload 486 
jim@jim-laptop:~$ ndiswrapper-utils-1.9 -v 
bash: ndiswrapper-utils-1.9: command not found 
jim@jim-laptop:~$ sudo ndiswrapper -i AUTORUN.EXE 
Password: 
installing autorun.exe ... 
couldn't get manufacturer section - installation may be incomplete 
jim@jim-laptop:~$ sudo ndiswrapper -i 
install/manage Windows drivers for ndiswrapper 

usage: ndiswrapper OPTION 
-i inffile       install driver described by 'inffile' 
-a devid driver  use installed 'driver' for 'devid' 
-r driver        remove 'driver' 
-l               list installed drivers 
-m               write configuration for modprobe 
-ma              write module alias configuration for all devices 
-mi              write module install configuration for all devices 
-v               report version information 

where 'devid' is either PCIID or USBID of the form XXXX:XXXX, 
as reported by 'lspci -n' or 'lsusb' for the card 
jim@jim-laptop:~$ 
jim@jim-laptop:~$ sudo ndiswraper -m 
sudo: ndiswraper: command not found 
jim@jim-laptop:~$ sudo modprobe ndiswrapper 
jim@jim-laptop:~$ sudo iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

jim@jim-laptop:~$ 
      I'm gona give up on it and maybe research more suitable wireless cards.  Thankyou for trying to help.

---

