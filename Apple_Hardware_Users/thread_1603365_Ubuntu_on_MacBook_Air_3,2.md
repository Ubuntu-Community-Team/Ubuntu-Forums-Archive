---
title: "Ubuntu on MacBook Air 3,2"
date: 2010-10-22
forum: Apple Hardware Users
---

### Post by SuperDodge on 2010-10-22
I just got one of the new MacBook Airs today and I'm trying to install Ubuntu.  I've installed refit, resized the Mac Partition, created two new partitions, used dd to image a bootable USB to one of the new partitions and I'm able to boot off of it.

When booting into Ubuntu, the screen is off-center with vertical colored bars that roll on the screen.  Has anyone figured out how to get around this yet?

---

### Post by SuperDodge on 2010-10-22
I've attached a picture of the screen during the installer.

---

### Post by Markrtoon on 2010-10-22
Hmm..that's an odd one...

---

### Post by kosumi68 on 2010-10-22
Are you able to get to a terminal with ctrl+alt+f1? It would be great to get as much data as you can provide. :-) For starters, files containing the output of these commands:
```

dmesg
sudo lsusb -vvv
sudo lspci -vvv
cat /var/log/Xorg.0.log
cat /proc/bus/input/devices 

```
Thanks!

---

### Post by kimptoc on 2010-10-22
Hi,

FWIW, I get that too, on my MBA 11"/64gb - when using the 10.10 live cd - via an external USB cd drive (not superdrive).

It works further with Ubuntu 8 - but hesitant to install that as it may not have working wifi ...but then 10.10 may have same issue.

Thanks,
Chris

---

### Post by SuperDodge on 2010-10-22
I'm making a bootable version of the alternate installer now to see if that helps my cause any.  I'll report back.

By the way kosumi68 - I like your signature.  It makes me think of a guy walking in saying "Lock up your scotch, hide your women and mark your threads solved!  kosumi is here!"

---

### Post by SuperDodge on 2010-10-22
No dice with the alternate installer...it can't detect the wireless card so there is no way to get access to the ubuntu servers.

---

### Post by kimptoc on 2010-10-22
The attached files have the output asked for - admitted from Ubuntu 8, which works fine... but 10.10 screen is unreadable...  mmm, must try for a ctrl-alt-f1/1 terminal...

---

### Post by kimptoc on 2010-10-22
And here are the files when under 10.10 when the display is all messed up - also messed up on the non-X terminals/consoles - but just about readable.

---

### Post by kimptoc on 2010-10-22
I have just tried a 10.04.1 desktop/i386 live cd, also has the display issue.

Probably a different issue, but under 8, neither gparted nor "sudo fdisk -l" see any disks...

But I can see the SSD under 10.10 :(

Gonna try a 9 disk...

---

### Post by forbes on 2010-10-22
A few questions.
[LIST]Which screen size you opted for (so we know which of the two resolutions you are having problems with)?
What do you mean by Ubuntu 8?
Are you trying i386 or AMD64?
Have you tried the Mini Display port to HDMI (or VGA, DVI, etc)?
[/LIST]
Thanks.

---

### Post by SuperDodge on 2010-10-22
I have the 13.3" and kimptoc has the 11" so both 1440x900 and 1366x768 have the same problem.

I am trying the i386 images.

I haven't tried the mini display port because I don't have an adapter.

---

### Post by forbes on 2010-10-22
Thanks SuperDodge.  I've ordered an 11", which should arrive later next week.  Hopefully we can figure out how to get the display to work soon.
Were you able to test anything else like headphone socket, suspend/hibernate, the new power button, function specific keys (brightness, volume, etc), wireless, bluetooth, touchpad, iSight, etc?  Or is the display so bad you can't really do an install?

---

### Post by kimptoc on 2010-10-23
Hi,

Sorry, by Ubuntu 8, I mean 8.1, i386

I have now tried 9.04/i386 , which displays ok, but still finds no devices/hard drives in gparted.

The 10.10 display is pretty unusable, though you can barely make out the dialog shape - so if you knew what options to  take, it might work.

I dont have the connector either to hook it up to VGA/TV :(

Thanks, 
Chris

PS Just tried using it a bit with the fuzzy screen.

Got the "try" option.  gparted runs and shows devices/partitions :)

I wonder if I partition in this mode, will it be visible under 9.04 - I am guessing not...

Tried the wireless, does not show any networks - so I think there is a driver issue there (dont have the usb/ethernet link - but then would it work under ubuntu?)

There was a nividia driver alert - I think it said no proprietary drivers found...

Sound does not seem to be working, no noise on boot - volume up/down does nothing. 

The normal F1 keys seem to be working, not sure about the Fn versions.

The fuzzy display seems to mean the right hand side of the screen is wrapped to the left... same on the terminal/command line too, ctrl-alt-f1.

Touchpad seems ok, though not sure how to do drag/right click on it - may need configuring...

---

### Post by ebsi on 2010-10-23
[http://ebsi4711.blogspot.com/2010/10/ubuntu-on-macbookair31-11.html](http://ebsi4711.blogspot.com/2010/10/ubuntu-on-macbookair31-11.html)

it is possible :D The patch for the keyboard and touchpad needs aditions.

Can someone provide me "lsusb and lspci" output of the MacBookAir3,2 ?

---

### Post by SuperDodge on 2010-10-23
I played with the garbled screen in 10.10 some as well.  I was able to get on my wireless network after installing a restricted driver.  There was also a restricted driver for the NVidia card in the list, but nothing got better after installing it.

---

### Post by kimptoc on 2010-10-23
Hey, thanks Ebsi - that "nomodeset" boot line sorted the screen problems out.

I now have an installed Ubuntu 10.10 :)

Right onto the wireless problems (and making nomodeset a permanent boot option...)

Thanks,
Chris

---

### Post by kimptoc on 2010-10-23
Output of dmidecode:

# dmidecode 2.9
SMBIOS 2.4 present.
37 structures occupying 1925 bytes.
Table at 0x000E0000.

Handle 0x0000, DMI type 4, 35 bytes
Processor Information
    Socket Designation: U2E1
    Type: Central Processor
    Family: Other
    Manufacturer: Intel(R) Corporation
    ID: 7A 06 01 00 FF FB EB BF
    Version: Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz
    Voltage: 1.6 V
    External Clock: 200 MHz
    Max Speed: 1400 MHz
    Current Speed: 1400 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x0002
    L2 Cache Handle: Not Provided
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Unknown
    Part Number: Not Specified

Handle 0x0001, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 8-way Set-associative

Handle 0x0002, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0003, DMI type 4, 35 bytes
Processor Information
    Socket Designation: U2E1
    Type: Central Processor
    Family: Other
    Manufacturer: Intel(R) Corporation
    ID: 7A 06 01 00 FF FB EB BF
    Version: Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz
    Voltage: 1.6 V
    External Clock: 200 MHz
    Max Speed: 1400 MHz
    Current Speed: 1400 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x0005
    L2 Cache Handle: Not Provided
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Unknown
    Part Number: Not Specified

Handle 0x0004, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 8-way Set-associative

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Unknown
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0006, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0007, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x0006
    Partition Width: 0

Handle 0x0008, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0006
    Error Information Handle: No Error
    Total Width: 2 bits
    Data Width: 65508 bits
    Size: 1024 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK 0
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1067 MHz (0.9 ns)
    Manufacturer: 0x02FE
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x45424A3130554538454655302D41452D4620

Handle 0x0009, DMI type 130, 186 bytes
OEM-specific Type
    Header and Data:
        82 BA 09 00 08 00 00 00 B0 00 92 10 0B 03 02 11
        02 01 03 52 01 08 0F 00 1E 00 69 78 69 3C 69 11
        2C 95 70 03 3C 3C 01 2C 83 81 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 0F 11 41 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 02
        FE 00 00 00 00 00 00 00 BE D2 45 42 4A 31 30 55
        45 38 45 46 55 30 2D 41 45 2D 46 20 30 20 02 FE
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00

Handle 0x000A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0006
    Error Information Handle: No Error
    Total Width: 2 bits
    Data Width: 65508 bits
    Size: 1024 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK 1
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1067 MHz (0.9 ns)
    Manufacturer: 0x02FE
    Serial Number: 0x00000000
    Asset Tag: Unknown
    Part Number: 0x45424A3130554538454655302D41452D4620

Handle 0x000B, DMI type 130, 186 bytes
OEM-specific Type
    Header and Data:
        82 BA 0B 00 0A 00 00 00 B0 00 92 10 0B 03 02 11
        02 01 03 52 01 08 0F 00 1E 00 69 78 69 3C 69 11
        2C 95 70 03 3C 3C 01 2C 83 81 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 0F 11 41 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 02
        FE 00 00 00 00 00 00 00 BE D2 45 42 4A 31 30 55
        45 38 45 46 55 30 2D 41 45 2D 46 20 30 20 02 FE
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00

Handle 0x000C, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x0008
    Memory Array Mapped Address Handle: 0x0007
    Partition Row Position: Unknown
    Interleave Position: 1
    Interleaved Data Depth: 1

Handle 0x000D, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x000A
    Memory Array Mapped Address Handle: 0x0007
    Partition Row Position: Unknown
    Interleave Position: 2
    Interleaved Data Depth: 1

Handle 0x000E, DMI type 0, 24 bytes
BIOS Information
    Vendor: Apple Inc.
    Version:    MBA31.88Z.0061.B00.1009101530
    Release Date: 09/10/10
    ROM Size: 4096 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        ACPI is supported
        IEEE 1394 boot is supported
        Smart battery is supported
        Function key-initiated network boot is supported
    BIOS Revision: 0.1

Handle 0x000F, DMI type 1, 27 bytes
System Information
    Manufacturer: Apple Inc.
    Product Name: MacBookAir3,1
    Version: 1.0
    Serial Number: C02DJ25MDDQX
    UUID: C52FEE79-7168-3457-A292-9BA902B2440F
    Wake-up Type: Power Switch
    SKU Number: System SKU#
    Family: MacBook

Handle 0x0010, DMI type 2, 16 bytes
Base Board Information
    Manufacturer: Apple Inc.
    Product Name: Mac-942452F5819B1C1B
    Version: 1.0
    Serial Number: C02039200DDDG4MAN
    Asset Tag: Base Board Asset Tag#
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Part Component
    Chassis Handle: 0x0011
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0011, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Apple Inc.
    Type: Notebook
    Lock: Not Present
    Version: Mac-942452F5819B1C1B
    Serial Number: C02DJ25MDDQX
    Asset Tag: Not Specified
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Other
    Security Status: Other
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: Unspecified
    Contained Elements: 0

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: None
    Internal Connector Type: None
    External Reference Designator: USB0
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: None
    Internal Connector Type: Other
    External Reference Designator: Mini DisplayPort
    External Connector Type: None
    Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: None
    Internal Connector Type: Other
    External Reference Designator: Microphone
    External Connector Type: None
    Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: None
    Internal Connector Type: Other
    External Reference Designator: Speaker
    External Connector Type: None
    Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: None
    Internal Connector Type: Other
    External Reference Designator: MagSafe DC Power
    External Connector Type: None
    Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA Port A
    Internal Connector Type: On Board IDE
    External Reference Designator: None
    External Connector Type: None
    Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: None
    Internal Connector Type: None
    External Reference Designator: Audio Line Out
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0019, DMI type 9, 13 bytes
System Slot Information
    Designation: AirPort
    Type: x1 PCI Express
    Current Usage: Available
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Hot-plug devices are supported
        SMBus signal is supported

Handle 0x001A, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description: Integrated Video Controller

Handle 0x001B, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: Azalia Audio Codec

Handle 0x001C, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: Yukon Ultra Ethernet Controller

Handle 0x001D, DMI type 10, 6 bytes
On Board Device Information
    Type: Other
    Status: Enabled
    Description: SATA

Handle 0x001E, DMI type 12, 5 bytes
System Configuration Options

Handle 0x001F, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        <BAD INDEX>
    Currently Installed Language: Not Specified

Handle 0x0020, DMI type 22, 32 bytes
Portable Battery
    Location: Unknown
    Manufacturer: Unknown
    Manufacture Date: Unknown
    Serial Number: Unknown
    Name: Unknown
    Design Capacity: Unknown
    Design Voltage: Unknown
    SBDS Version: Unknown
    Maximum Error: Unknown
    SBDS Chemistry: Unknown
    OEM-specific Information: 0x00000000

Handle 0x0021, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0022, DMI type 131, 6 bytes
OEM-specific Type
    Header and Data:
        83 06 22 00 02 03

Handle 0x0023, DMI type 128, 88 bytes
OEM-specific Type
    Header and Data:
        80 58 23 00 04 00 00 00 03 14 01 C0 FF FF 01 C0
        02 00 00 03 00 00 00 00 00 A0 CC FF FF 9F E0 FF
        00 A0 E0 FF FF 1F E3 FF 00 20 E3 FF FF BF FF FF
        00 00 C8 FF FF 7F CA FF 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 00 00 00

Handle 0xFFFD, DMI type 127, 4 bytes
End Of Table

---

### Post by kimptoc on 2010-10-23
Output of lspci:

00:00.0 Host bridge: nVidia Corporation MCP89 HOST Bridge (rev a1)
00:00.1 RAM memory: nVidia Corporation MCP89 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation Device 0d6d (rev a1)
00:01.1 RAM memory: nVidia Corporation Device 0d6e (rev a1)
00:01.2 RAM memory: nVidia Corporation Device 0d6f (rev a1)
00:01.3 RAM memory: nVidia Corporation Device 0d70 (rev a1)
00:02.0 RAM memory: nVidia Corporation Device 0d71 (rev a1)
00:02.1 RAM memory: nVidia Corporation Device 0d72 (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP89 LPC Bridge (rev a2)
00:03.1 RAM memory: nVidia Corporation MCP89 Memory Controller (rev a1)
00:03.2 SMBus: nVidia Corporation MCP89 SMBus (rev a1)
00:03.3 RAM memory: nVidia Corporation MCP89 Memory Controller (rev a1)
00:03.4 Co-processor: nVidia Corporation MCP89 Co-Processor (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:06.0 USB Controller: nVidia Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:06.1 USB Controller: nVidia Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:08.0 Audio device: nVidia Corporation MCP89 High Definition Audio (rev a2)
00:0a.0 IDE interface: nVidia Corporation MCP89 SATA Controller (rev a2)
00:0b.0 RAM memory: nVidia Corporation Device 0d75 (rev a1)
00:15.0 PCI bridge: nVidia Corporation Device 0d9b (rev a1)
00:17.0 PCI bridge: nVidia Corporation MCP89 PCI Express Bridge (rev a1)
01:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation Device 08a2 (rev a2)


Output of lsusb:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 05ac:821b Apple, Inc. 
Bus 003 Device 005: ID 05ac:820b Apple, Inc. 
Bus 003 Device 004: ID 05ac:820a Apple, Inc. 
Bus 003 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 002: ID 05ac:0243 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bc2:2000 Seagate RSS LLC Storage Adapter V3 (TPP)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ac:850a Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by kimptoc on 2010-10-23
On the wireless driver front, from the lspci output, it seems to be a Broadcom BCM43224 [14e4;4353] chip.

I tried the CD based install, as per [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") but no joy.

The b43 module seems to load, I get a message in the /var/log/messages about the Broadcom 43xx driver loaded, features PL, firmware-id FW13] - but no sign of wireless life.

It seems that according to the b43 page this device is not covered by that driver - wonder which I should be using...

[http://wireless.kernel.org/en/users/Drivers/b43#FAQ_-_Frequently_asked_questions](http://wireless.kernel.org/en/users/Drivers/b43#FAQ_-_Frequently_asked_questions)

Although "lshw -C network" shows a *-network UNCLAIMED entry for the Network controller - so it seems like I just need to start something to get it being used... but what?

It seems support for this network card was going to be built into 10.10:
[http://www.daemonnews.org/2010/09/10/linux-wi-fi-gets-easier-with-new-broadcom-driver.html](http://www.daemonnews.org/2010/09/10/linux-wi-fi-gets-easier-with-new-broadcom-driver.html)

But then since its got kernel 2.6.35 and 2.6.36 is the one with the driver in, perhaps not...

[https://lists.ubuntu.com/archives/natty-changes/2010-October/000022.html](https://lists.ubuntu.com/archives/natty-changes/2010-October/000022.html)

I guess there is an old driver that should support this card - but which...

/Chris

---

### Post by ebsi on 2010-10-23
@kimptoc: use the Bradcom bcmwl restricted driver for wlan

@all: Can someone with a MacBookAir 13" provide lspci, lsusb and dmidecode output. thx

---

### Post by kimptoc on 2010-10-23
YAY - got the wifi working, thanks again Ebsi - went for the 
[B]"b43/STA - No Internet access" 
[/B]

Option on this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Didnt appear on the restricted list, but loading the "wl" driver worked just fine and re-appeared following a reboot.

Thanks,
Chris

---

### Post by kosumi68 on 2010-10-23
> **kimptoc said:**
> And here are the files when under 10.10 when the display is all messed up - also messed up on the non-X terminals/consoles - but just about readable.

Very nice! Please find attached a (new and experimental) dkms version of applesmc that should get your temperature and fans working. It would be great it you would like to report back the output of
```

dmesg | grep applesmc:
cat /sys/devices/platform/applesmc.768/temp*label

```
Thanks!

---

### Post by kosumi68 on 2010-10-23
> **ebsi said:**
> [http://ebsi4711.blogspot.com/2010/10/ubuntu-on-macbookair31-11.html](http://ebsi4711.blogspot.com/2010/10/ubuntu-on-macbookair31-11.html)

it is possible :D The patch for the keyboard and touchpad needs aditions.

Can someone provide me "lsusb and lspci" output of the MacBookAir3,2 ?

Thanks for the patch! Since the device id is new, i wonder what actually changed... A picture created with mtview could help find any peculiarities ([http://bitmath.org/code/mtview/](http://bitmath.org/code/mtview/)).

Cheers!

---

### Post by kimptoc on 2010-10-23
Hi Kosumi,

Attached is the output, post reboot - seems like its a lot happier :)

Thanks,
Chris

---

### Post by kosumi68 on 2010-10-23
> **kimptoc said:**
> Hi Kosumi,

Attached is the output, post reboot - seems like its a lot happier :)

Thanks,
Chris

Sounds good! But I wonder about keyboard backlight support... I assume it should be present? Attached a somewhat different dkms package, in case that makes a difference. Otherwise, it would be very interesting to see the full register set, as per this thread: [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

Thanks!

---

### Post by kimptoc on 2010-10-23
No keyboard backlight on new MBAs :( or at least the 11"...

---

### Post by SuperDodge on 2010-10-23
ebsi - requested outputs are attached for the new 13" MacBook Air

---

### Post by SuperDodge on 2010-10-23
Also, the nomodeset option got me into the 10.10 installer and I'm now posting from my Ubuntu installation.  I installed the restricted nVidia and wireless drivers and everything seems to be working well except the trackpad which is acting kind of funky.

I'll do some more research tomorrow and see if I can figure it out.

---

### Post by forbes on 2010-10-23
If you've not seen it you guys might want to add your output details to this forum post, along with the amount of RAM installed and whether it is 3,1 or 3,2:
[http://ubuntuforums.org/showthread.php?t=1557326]("http://ubuntuforums.org/showthread.php?t=1557326")

---

### Post by SuperDodge on 2010-10-24
forbes - just did this for 13".  Someone should do this for the 11" as well.

---

### Post by SuperDodge on 2010-10-24
ebsi - how do I use the keyboard and touchpad patch you reference on your blog?

---

### Post by ebsi on 2010-10-24
@SuperDodge: What keyboard layout you have ?

---

### Post by ebsi on 2010-10-24
Added MacBookAir3,2 support to my patch ( keyboard,touchpad,smc ).

Aditional infos for a custom kernel on ubuntu :


[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")




Patch :

---

### Post by kosumi68 on 2010-10-24
> **ebsi said:**
> Added MacBookAir3,2 support to my patch ( keyboard,touchpad,smc ).

Aditional infos for a custom kernel on ubuntu :


[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")




Patch :

Two new usbid series, that's been a while. :-)

1. Does the applesmc-dkms (0.17.0~test2) package in this thread work for you? The old device list is on its way out, so it would be very valuable to know if the automatic detection of this package picks everything up as it should.

2. For bcm5974, turning debug information on with (as root) echo -n 9 > /sys/module/bcm5974/parameters/debug might reveal something.

Thanks!

---

### Post by ebsi on 2010-10-24
Here is the output of you apple smc.

dmesg :

[ 2776.889520] applesmc: driver unloaded.
[ 2787.468761] applesmc: Apple MacBook Air detected
[ 2787.522918] applesmc: key=313, fan=1, temp=27, acc=0, light=0, keyb=0
[ 2795.318492] applesmc: wait status failed: 5 != 0

sensors :

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  1994 RPM  (min = 2000 RPM)
TB0T:        +29.5°C                                    
TB1T:        +29.5°C                                    
TB2T:        +27.5°C                                    
TC0D:        +47.2°C                                    
TC0E:        +47.5°C                                    
TC0P:        +41.8°C                                    
TC1E:        +47.8°C                                    
TCZ3:       +255.8°C                                    
TCZ4:         +0.0°C                                    
TCZ5:         +0.0°C                                    
TG0E:        +58.5°C                                    
TG1E:        +58.5°C                                    
TG2E:        +58.2°C                                    
TGZ3:         +0.0°C                                    
TGZ4:         +0.0°C                                    
TGZ5:         +0.0°C                                    
TH0F:       +249.0°C                                    
TH0O:       +249.0°C                                    
ERROR: Can't get value of subfeature temp19_input: I/O error
TH0o:         +0.0°C                                    
TM0P:        +40.5°C                                    


One temp makes problems.

---

### Post by kosumi68 on 2010-10-24
> **ebsi said:**
> Here is the output of you apple smc.


Thanks for the feedback! It would be very helpful to also see the list of labels:
```

cat /sys/devices/platform/applesmc.768/temp*label

```

to see if the label is readable at all...

---

### Post by ebsi on 2010-10-24
cat /sys/devices/platform/applesmc.768/temp*label

```

TCZ5
TG0E
TG1E
TG2E
TGZ3
TGZ4
TGZ5
TH0F
TH0O
TH0o
TB0T
TM0P
TN0D
TN0P
TN1D
Th1H
Tp0P
Ts0P
Ts0S
TB1T
TB2T
TC0D
TC0E
TC0P
TC1E
TCZ3
TCZ4

```

---

### Post by kosumi68 on 2010-10-24
> **ebsi said:**
> cat /sys/devices/platform/applesmc.768/temp*label


I see - could have been a random misread, then. To make sure it is not a systemic problem due to a new data type, having the full smc scan as per [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) would be very helpful.

Thanks!

---

### Post by ebsi on 2010-10-24
Here we go with the smc scan.

---

### Post by ebsi on 2010-10-24
Backlight also works. Added MacBookAir3,1 and MacBookAir3,2 the the driver.

---

### Post by kosumi68 on 2010-10-24
> **ebsi said:**
> Here we go with the smc scan.

Much obliged. And yes, that seemed to be the reason. Thank you so much for the feedback. When the new applesmc is sufficiently well cooked, there will be a new thread with call for testing on all machines.

Thanks!

---

### Post by SuperDodge on 2010-10-24
> **ebsi said:**
> @SuperDodge: What keyboard layout you have ?

US

Also how do I apply your patch when compiling a custom kernel?  I really want to get keyboard and touchpad support working correctly.

---

### Post by ebsi on 2010-10-24
Updated patch. The Keyboard mapping on the funktion keys is now correct.

---

### Post by ebsi on 2010-10-24
Short howto compile a custom kernel :

```
cd /usr/src


apt-get source linux-image-2.6.35-22-generic
apt-get build-dep linux-image-2.6.35-22-generic
apt-get install fakeroot kernel-package

cd linux-2.6.35

patch -p1 -i ../macbookair_patch_2.txt

fakeroot make-kpkg --revision=1 --append-to-version=MacBookAir --initrd kernel_image kernel_headers
dpkg -i ../linux-image-2.6.35-*.deb

```

This is the poor mans way ;)

---

### Post by kosumi68 on 2010-10-27
New dynamic applesmc module available in [http://ubuntuforums.org/showthread.php?t=1607523](http://ubuntuforums.org/showthread.php?t=1607523), which should fix the read problem of the single temperature file. The scale is yet unknown, so the output of "sensors" would be very nice. Cheers!

---

### Post by ebsi on 2010-10-29
Here we go :

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (high = +105.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  1994 RPM  (min = 2000 RPM)
TB0T:        +32.5°C                                    
TB1T:        +32.5°C                                    
TB2T:        +31.0°C                                    
TC0D:        +50.0°C                                    
TC0E:        +50.8°C                                    
TC0P:        +44.8°C                                    
TC1E:        +51.2°C                                    
TCZ3:         +0.0°C                                    
TCZ4:         +0.0°C                                    
TCZ5:         +0.0°C                                    
TG0E:        +61.0°C                                    
TG1E:        +61.0°C                                    
TG2E:        +61.2°C                                    
TGZ3:       +255.8°C                                    
TGZ4:         +0.0°C                                    
TGZ5:         +0.0°C                                    
TH0F:       +249.2°C                                    
TH0O:       +249.0°C                                    
TH0o:        +28.0°C                                    
TM0P:        +43.0°C

---

### Post by apoth on 2010-10-29
If this is working reasonably yet, I'd appreciate it if someone could edit the OP or start a HOWTO thread and list the goodness in one place.

Especially if it doesn't require a USB DVD drive. :)

---

### Post by kosumi68 on 2010-10-29
> **ebsi said:**
> Here we go :

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (high = +105.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  1994 RPM  (min = 2000 RPM)
TB0T:        +32.5°C                                    
TB1T:        +32.5°C                                    
TB2T:        +31.0°C                                    
TC0D:        +50.0°C                                    
TC0E:        +50.8°C                                    
TC0P:        +44.8°C                                    
TC1E:        +51.2°C                                    
TCZ3:         +0.0°C                                    
TCZ4:         +0.0°C                                    
TCZ5:         +0.0°C                                    
TG0E:        +61.0°C                                    
TG1E:        +61.0°C                                    
TG2E:        +61.2°C                                    
TGZ3:       +255.8°C                                    
TGZ4:         +0.0°C                                    
TGZ5:         +0.0°C                                    
TH0F:       +249.2°C                                    
TH0O:       +249.0°C                                    
TH0o:        +28.0°C                                    
TM0P:        +43.0°C

Thanks! The TZ and TG do not seem active here, but the actual register with problems was TH0o. Does it ever change value, and if so does the temperature look reasonable?

---

### Post by corn13read on 2010-10-30
How is battery life in ubuntu? I have a macbook pro and I consistently get 1-2 hours less in ubuntu than in mac.

TIA

---

### Post by SuperDodge on 2010-10-30
ebsi - I created a new kernel using your keyboard patch.  While all my keyboard butons now function correctly, my trackpad no longer works.  Is there an id or something I can check to see if there are multiple hardware ids or something to that effect?

Reverting to the generic kernel works as before.

---

### Post by Dreamsorcerer on 2010-11-01
I just got a Macbook Air today, and compiled a new kernel with the patch as outlined before, but the only thing it seems to have done is fix click 'n' drag with the track pad, and added 2 and 3 finger click. It still doesn't have scrolling support, and the function keys don't work. Not sure what else the patch was supposed to do.

I've also noticed the speakers aren't working (headphones fine though). Any help with this would be appreciated. Has anybody started up a wiki page with any of this information yet?

Hardware: MacBookAir3,2 (13"), 4GB RAM.

Edit: Oh, and it can't reboot. Shutdown works fine, but restart doesn't.

---

### Post by apoth on 2010-11-01
No one had problems with the installer hanging at 'Detecting file systems...'?

---

### Post by npgall on 2010-11-01
@Dreamsorcerer to get reboot to work, you need to add reboot=pci to the kernel command line.

Open /etc/default/grub and add as follows:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset reboot=pci"

Then run: sudo update-grub. Note I also had to add nomodeset as above to get the screen to not go blank :)

@apoth Afraid not, it worked okay for me. I've done two installations so far - at first I wiped the whole disk replacing OS X entirely, and the installer set up the disk just fine. Then I found that I couldn't get sound to work over the speakers so I reinstalled OS X for the time being, installed rEFIt so I could dual boot, and I used OS X bootcamp to partition the disk.

Bootcamp creates a FAT32 partition. In the Ubuntu installer I selected manual partitioning, then I deleted that FAT32 partition which left a load of free space at the end of the disk. I created two partitions in that free space- one ext4 on '/' for the OS and one for swap (4GB swap). Ubuntu was happy to install into this.

Anyway I'm posting this from ubuntu on my 11" MacBook Air. My current situation in ubuntu is nvidia graphics (even 1080p youtube) works just fine, wifi no problems, iSight webcam no problems. The main issue is the sound, which won't play over the built in speakers. I haven't tried recompiling the kernel to get multi-touch on the trackpad working yet though. I'm dreading recompiling the kernel, that never works for me. I'm used to ubuntu 'just working' over the last few years, this reminds me of linux 5 years ago.

---

### Post by sublimespot on 2010-11-02
Can someone give me the low down on how to install Ubuntu 10.04 on the MB Air? I have read all the posts and I see many of the details being worked out, but I cannot find "the basics". 

Like, should I be using Boot Camp Assistant to resize the drive first, then use that with a Ubuntu CD as if it were windows? Or are you booting into Ubuntu install with a USB CD drive, or with a USB flash drive?

I am trying to boot to some of my ubuntu/backtrack usb sticks with no luck.

---

### Post by ebsi on 2010-11-02
Here is a new patchset for the MacBookAir3,1(3,2) it contains the following patches :

```

applesmc_macnbookair.patch
bcm5974_macbookair.patch
btusb_macbookair.patch
hid_macbookair.patch
mbp_backlight_macbookair.patch
snd_hda_macbookair.patch

```

---

### Post by Dreamsorcerer on 2010-11-02
> **sublimespot said:**
> Can someone give me the low down on how to install Ubuntu 10.04 on the MB Air? I have read all the posts and I see many of the details being worked out, but I cannot find "the basics". 

Like, should I be using Boot Camp Assistant to resize the drive first, then use that with a Ubuntu CD as if it were windows? Or are you booting into Ubuntu install with a USB CD drive, or with a USB flash drive?

I am trying to boot to some of my ubuntu/backtrack usb sticks with no luck.


I followed this: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Although I'm not sure the refit is actually necessary, as I skipped the step about fixing the partition tables, and all works fine.

---

### Post by apoth on 2010-11-02
> **npgall said:**
> 
@apoth Afraid not, it worked okay for me. I've done two installations so far - at first I wiped the whole disk replacing OS X entirely, and the installer set up the disk just fine. Then I found that I couldn't get sound to work over the speakers so I reinstalled OS X for the time being, installed rEFIt so I could dual boot, and I used OS X bootcamp to partition the disk.

Bootcamp creates a FAT32 partition. In the Ubuntu installer I selected manual partitioning, then I deleted that FAT32 partition which left a load of free space at the end of the disk. I created two partitions in that free space- one ext4 on '/' for the OS and one for swap (4GB swap). Ubuntu was happy to install into this.

Thanks, at least that gives me a couple of things to go on.

> **npgall said:**
> I'm dreading recompiling the kernel, that never works for me. I'm used to ubuntu 'just working' over the last few years, this reminds me of linux 5 years ago.

:)

Me too... though at least once you're at the stage of recompiling the kernel you're likely to get a decent error message if it does go wrong!

---

### Post by kosumi68 on 2010-11-02
> **ebsi said:**
> Here is a new patchset for the MacBookAir3,1(3,2) it contains the following patches :

```

applesmc_macnbookair.patch
bcm5974_macbookair.patch
btusb_macbookair.patch
hid_macbookair.patch
mbp_backlight_macbookair.patch
snd_hda_macbookair.patch

```

Nice going! I am trying to incorporate your findings into the mactel dkms packages and upstream, and have some questions:

1. I was under the impression that the two usb id series corresponds to the 11'' and 13'' variants, and yet, both seem to be using the new keyboard mapping, which seems to be for the smaller keyboard only. Some clarifications here would be great.

2. The new applesmc module in the ppa should work well for these new machines, so that patch won't be needed for the ppa.

3. I would expect the new versions of the trackpad chips and firmware to exhibit slightly different behavior. Have the MT capabilities been tested? Are the packet sizes the same? Any additional information on this part would be greatly appreciated.

Thanks!

---

### Post by _mario_ on 2010-11-02
> **ebsi said:**
> Here is a new patchset for the MacBookAir3,1(3,2) it contains the following patches :

```

applesmc_macnbookair.patch
bcm5974_macbookair.patch
btusb_macbookair.patch
hid_macbookair.patch
mbp_backlight_macbookair.patch
snd_hda_macbookair.patch

```

Thanks. I'm going to incorporate the patch into the display backlight driver. However, you should use nvidia_bl on this machine rather than mbp_nvidia_bl. Does it work as well? You might need the max_level=0x1ffff driver option right now. Please report back and I'll fix both drivers.

ciao,
Mario

---

### Post by bwatson009 on 2010-11-02
Should we put together a Wiki on this outlining the process from start to finish? My Air arrives today and I am willing to help!

---

### Post by apoth on 2010-11-02
> **bwatson009 said:**
> Should we put together a Wiki on this outlining the process from start to finish? My Air arrives today and I am willing to help!

Yes!

I've added a link in [here](https://help.ubuntu.com/community/MacBookAir) and ripped off the headings from a previous Air release.

Looks like [this](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages) and [this](https://wiki.ubuntu.com/MactelSupportTeam) at least will want updating too.

---

### Post by forbes on 2010-11-02
> **apoth said:**
> Yes!

I've added a link in [here](https://help.ubuntu.com/community/MacBookAir) and ripped off the headings from a previous Air release.

Looks like [this](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages) and [this](https://wiki.ubuntu.com/MactelSupportTeam) at least will want updating too.

Good job.
Maybe the link should be more like [this one](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid) though, as I suspect the 11" and 13" pages will be pretty much identical.  So MacBookAir3-1_3-2
Just thought I'd mention it before it gets too built out.

---

### Post by apoth on 2010-11-02
> **npgall said:**
> 
@apoth Afraid not, it worked okay for me. I've done two installations so far - at first I wiped the whole disk replacing OS X entirely, and the installer set up the disk just fine. Then I found that I couldn't get sound to work over the speakers so I reinstalled OS X for the time being, installed rEFIt so I could dual boot, and I used OS X bootcamp to partition the disk.

How did you have the option to wipe the whole disk? I've only been able to get rEFIt to boot when the installer is imaged onto a partition on the disk, so it won't let me wipe over the partition the installer's on?

I've partitioned about six different ways now and it still doesn't get past 'Detecting file systems' - a stage you'd miss if you blinked watching a virtualbox install. :(

---

### Post by furryomnivore on 2010-11-02
I have a 13" in the mail right now, I'll toss some help toward the wiki once it comes in.

---

### Post by Dreamsorcerer on 2010-11-02
Right, I just added basic installation to get it started. That's based on my experience with a 13", feel free to adjust it.

If someone could check if those installation instructions work without using rEFIt, that would be appreciated. I installed rEFIt as the general instructions said to, but then skipped the step it was supposed to be used for, so I don't think it is needed.

If somebody could now describe the easiest way to proceed with the post-install setup to get trackpad, screen brightness etc. working, that would be highly appreciated, as I'm still unsure about how to do this. And I don't want to unplug my laptop until I can change the screen brightness, it's practically halving the battery life.

---

### Post by Dreamsorcerer on 2010-11-02
Nevermind, tested it myself. It does need rEFIt, I'll change it later.

---

### Post by OsricTheKnight on 2010-11-03
> **apoth said:**
> How did you have the option to wipe the whole disk? I've only been able to get rEFIt to boot when the installer is imaged onto a partition on the disk, so it won't let me wipe over the partition the installer's on?

I've partitioned about six different ways now and it still doesn't get past 'Detecting file systems' - a stage you'd miss if you blinked watching a virtualbox install. :(

I have a sort of answer to your question - if you have the mac external drive, you can get refit to see it by rebooting while it is spinning up just after you insert the Ubuntu disc, or you can get it to boot by choosing it from the System Preferences / Startup Disk settings in mac os x.

Then you can delete the bootcamp partition if you want dual boot or blow everything away if you want the whole disc.

Osric

---

### Post by OsricTheKnight on 2010-11-03
I did a few things differently than described so far.

First off, I bought a USB->Ethernet dongle because I anticipated wireless problems would be annoying during install.

Then I followed more or less the same directions as everyone else until the end of the install process.

Then, before rebooting, I started a new terminal, and ran:

cd /tmp
mkdir mntroot
sudo mount /dev/sda3 mntroot

Note that /dev/sda3 is where I installed "/" for ubuntu.

sudo mount --bind /dev  ./mntroot/dev
sudo mount --bind /dev/pts  ./mntroot/dev/pts
sudo mount --bind /proc ./mntroot/proc
sudo mount --bind /sys  ./mntroot/sys
sudo chroot mntroot

at this point, I was sitting at a root prompt on my SSD "disk", ready to fix the grub install. Then I edited /etc/default/grub and made GRUB_CMDLINE_LINUX="nomodeset reboot=pci". Finally I ran

update-grub

and typed "reboot", hit enter when prompted, and had the system reboot. It's now running; the wireless driver was automatically chosen by the install process for me, and wireless is working without the dongle. The Nvidia driver was the first thing I needed to install after that.

Hope this is helpful to others,

Osric

---

### Post by bwatson009 on 2010-11-03
With rEFIt installed, and following the instructions to have the disk recognized during bootup, when I select "linux install cd", I just get a "Non-system disk Press any key to reboot" error. I am not using a Superdrive, but I didn't think that should matter.

If I select "Boot EFI\boot\bootx64.efi from" I get GRUB and the "try Ubuntu without installing" and "Install Ubuntu" menu, but if I select either option, I am left with a black screen and no disk activity.

The disk is a 64bit Meerkat CD-R, which has been used on several other machines. I've tried numerous combinations of actions, and nothing seems to be working.

Any thoughts?

---

### Post by litemotiv on 2010-11-03
> **_mario_ said:**
> Thanks. I'm going to incorporate the patch into the display backlight driver. However, you should use nvidia_bl on this machine rather than mbp_nvidia_bl. Does it work as well? You might need the max_level=0x1ffff driver option right now. Please report back and I'll fix both drivers.


nvidia_bl doesn't seem to work by merely adding the MBA models, it complains that no supported graphics adapter is found. 

I guess we also need to add another card match? There is a 320M listed in the driver but i don't think it has the right pci id for the 3,2.

---

### Post by Dreamsorcerer on 2010-11-03
Updated the installation wiki. I used a Superdrive for installation, as I was under the impression it was required. If anybody's installed without a Superdrive, and the installation is any different than would be expected, please add some information to the wiki.

I also still haven't figured out how to get the screen brightness, trackpad etc. working. I've spent the whole day today trying to figure out how to get Ubuntu to boot by default, rather than OSX/rEFIt, or how to install Ubuntu without OS X. I tried installing without OS X, but when I turn on the machine it sits at a black screen for 30 seconds before deciding to boot Ubuntu, so I gave up and reinstalled OS X. Not a very productive day :(

---

### Post by forbes on 2010-11-03
> **Dreamsorcerer said:**
> trying to figure out how to get Ubuntu to boot by default, rather than OSX/rEFIt

You can do this by editing the refit.conf file, and uncommenting the following line:
```
#legacyfirst
```

That will put the Tux on the left and be the default option.

To get to the refit.conf file, boot into OS X and by default I think it should be here: /efi/refit

---

### Post by forbes on 2010-11-03
In that conf file you can also reduce the default boot delay:
```
timeout 20
```

Here is the sample: [http://refit.sourceforge.net/doc/c3s3_config.html]("http://refit.sourceforge.net/doc/c3s3_config.html")

---

### Post by litemotiv on 2010-11-03
> **Dreamsorcerer said:**
> I tried installing without OS X, but when I turn on the machine it sits at a black screen for 30 seconds before deciding to boot Ubuntu, so I gave up and reinstalled OS X. Not a very productive day :(

You can try this to get rid of the boot delay when running without OSX: [https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB](https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB)

---

### Post by Dreamsorcerer on 2010-11-03
> **forbes said:**
> You can do this by editing the refit.conf file

Right, but now I have two bootloaders, because when I boot Ubuntu it runs GRUB first. How can I stop it running GRUB altogether, so the boot speeds up a little?

---

### Post by ebsi on 2010-11-03
> **_mario_ said:**
> Thanks. I'm going to incorporate the patch into the display backlight driver. However, you should use nvidia_bl on this machine rather than mbp_nvidia_bl. Does it work as well? You might need the max_level=0x1ffff driver option right now. Please report back and I'll fix both drivers.

ciao,
Mario

I did only try mbp_nvidia_bl because it exists upstream. I did also send the patches upstream. You can follow the status of them on the LKML.

---

### Post by Dreamsorcerer on 2010-11-03
> **litemotiv said:**
> You can try this to get rid of the boot delay when running without OSX: [https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB](https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB)

Thanks for that, really helpful, although it's still slower. :( It still takes about 6 seconds to pass control over to Ubuntu, whereas when OS X was installed it took about 1-2 seconds.

---

### Post by kosumi68 on 2010-11-03
> **ebsi said:**
> I did only try mbp_nvidia_bl because it exists upstream. I did also send the patches upstream. You can follow the status of them on the LKML.

Did the lcd backlight actually work? I get all these unknown pci device ids, and looking at nvidia_bl, it does not seem to be supported yet (machine has devices in the 0x0d00 range, nvidia_bl table ends at 0x0cbc).

---

### Post by _mario_ on 2010-11-04
> **kosumi68 said:**
> Did the lcd backlight actually work? I get all these unknown pci device ids, and looking at nvidia_bl, it does not seem to be supported yet (machine has devices in the 0x0d00 range, nvidia_bl table ends at 0x0cbc).

No. According to the previous posts, the device ID in question is 0x08a2 (the VGA device). Just to be sure: Can someone please run the command
```
lspci -nn
```

Then, its fairly trivial to add the ID to the list. Btw: For testing purposes, the driver does also work if using the dev_id=<hex ID> option.

Thanks & ciao,
Mario

---

### Post by _mario_ on 2010-11-04
> **ebsi said:**
> I did only try mbp_nvidia_bl because it exists upstream. I did also send the patches upstream. You can follow the status of them on the LKML.

Ok. Updated the mactel version. As of 0.25.2 it should work.

ciao,
Mario

---

### Post by litemotiv on 2010-11-04
> **_mario_ said:**
> No. According to the previous posts, the device ID in question is 0x08a2 (the VGA device). Just to be sure: Can someone please run the command
```
lspci -nn
```


10de:08a3

---

### Post by _mario_ on 2010-11-04
> **litemotiv said:**
> 10de:08a3

Thanks. That's interesting. Does Apple ship models with 2 different chips?

However, let's confirm its working by loading nvidia_bl with:
```

$ sudo rmmod mbp_nvidia_bl
$ sudo modprobe nvidia_bl dev_id=0x08a3 max_level=0x1ffff

```

ciao,
Mario

---

### Post by mfrey on 2010-11-04
I can not get brightness to work even with the new mbp_nvidia_bl patch.  Anyone else have it working?

---

### Post by _mario_ on 2010-11-04
> **mfrey said:**
> I can not get brightness to work even with the new mbp_nvidia_bl patch.  Anyone else have it working?

Which version are you using? Version 0.25.2? As of now, the packages aren't built yet. Sometime it takes a few minutes...

ciao,
Mario

---

### Post by mfrey on 2010-11-04
I actually rebuilt my kernel with the patch.  2.6.35 kernel.  The module loads and I get the screen indicator but the brightness does not change.

---

### Post by kosumi68 on 2010-11-04
For maverick users: I incorporated gimlis changes in the mactel repository, so that there is no need to compile kernels. All in all, to get fans, keyboard and trackpad working:

1. Make sure you have the mactel ppa among your sources

2. Install these packages:
```

sudo apt-get update
sudo apt-get install applesmc-dkms hid-apple-dkms bcm5974-dkms xf86-input-multitouch

```

3. Add this to your /etc/X11/xorg.conf:
```

Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
EndSection

```

Enjoy!

---

### Post by litemotiv on 2010-11-04
> **_mario_ said:**
> Thanks. That's interesting. Does Apple ship models with 2 different chips?

However, let's confirm its working by loading nvidia_bl with:
```

$ sudo rmmod mbp_nvidia_bl
$ sudo modprobe nvidia_bl dev_id=0x08a3 max_level=0x1ffff

```


No luck with a vanilla 2.6.35.8 kernel at least, it errors with "no such device".

---

### Post by _mario_ on 2010-11-04
> **litemotiv said:**
> No luck with a vanilla 2.6.35.8 kernel at least, it errors with "no such device".

Sorry my fault. Just uploaded version 0.17.1 that incorporates both devices (0x08a2 and 0x08a3). However, due to previous models it still assumes the machine supports 44000 brightness levels rather than 131072 (0x1ffff). Can you try to figure out the maximum?

ciao,
Mario

---

### Post by kosumi68 on 2010-11-04
To obtain the right trackpad dimensions for the MBA 3,2, it would be great if someone with that machine could do this:
```

sudo -i
echo 9 > /sys/module/bcm5974/parameters/debug
tail -f /var/log/debug | grep raw

```

Move the finger around the edges of the trackpad and note the minimum and maximum values in the X and Y direction. To restore:
```

echo 0 > /sys/module/bcm5974/parameters/debug
exit

```

Thanks!

---

### Post by litemotiv on 2010-11-04
> **_mario_ said:**
> Sorry my fault. Just uploaded version 0.17.1 that incorporates both devices (0x08a2 and 0x08a3). However, due to previous models it still assumes the machine supports 44000 brightness levels rather than 131072 (0x1ffff). Can you try to figure out the maximum?


Alright, the module is loading now. The brightness isn't changing however, no matter which value i echo to /nvidia_backlight/brightness...

---

### Post by Dreamsorcerer on 2010-11-04
> **kosumi68 said:**
> For maverick users: I incorporated gimlis changes in the mactel repository, so that there is no need to compile kernels. All in all, to get fans, keyboard and trackpad working:

Thanks for that, although the brightness keys still don't seem to be working. I've added the information to the wiki. What do you mean about the fans, what can you do now, that couldn't be done before installing?

Also still don't have speakers working, anybody got additional information on that?

---

### Post by mfrey on 2010-11-04
I've created a btusb-dkms package that makes bluetooth work.

[https://launchpad.net/~mfrey/+archive/ppa](https://launchpad.net/~mfrey/+archive/ppa)

I am happy for it to be in the Mactel PPA if anyone wants to add it there.

---

### Post by kosumi68 on 2010-11-04
> **mfrey said:**
> I've created a btusb-dkms package that makes bluetooth work.

[https://launchpad.net/~mfrey/+archive/ppa](https://launchpad.net/~mfrey/+archive/ppa)

I am happy for it to be in the Mactel PPA if anyone wants to add it there.

Great! I sent you a pm on the procedure to get it up there.

---

### Post by mfrey on 2010-11-04
OK -- I just uploaded btusb-dkms to the Mactel PPA.

---

### Post by kosumi68 on 2010-11-04
> **mfrey said:**
> OK -- I just uploaded btusb-dkms to the Mactel PPA.

Works like a charm - thanks!

---

### Post by npgall on 2010-11-04
> **apoth said:**
> How did you have the option to wipe the whole disk? I've only been able to get rEFIt to boot when the installer is imaged onto a partition on the disk, so it won't let me wipe over the partition the installer's on?

Hope this reply is not too late apoth, but to wipe the whole disk I booted the machine from the ubuntu CD in a USB CD-ROM drive (a standard CD-ROM drive, not the superdrive or anything). To boot from CD, you have to hold down the ALT key while you turn on the machine, and then it displays an icon for the internal disk and an icon for the CD-ROM and you can click the drive you want to boot from.

If you wipe the whole disk I don't think you need to install rEFIt, at least I had not installed rEFIt when I first installed ubuntu that way. I did notice that on startup after wiping the disk the machine would display a white screen for a long time before it would boot into ubuntu (possibly the EFI was still looking for OS X somehow). Someone else here has suggested [https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB](https://wiki.archlinux.org/index.php/Macbook#Avoid_long_EFI_wait_before_GRUB) as a way to fix that delay.

Anyway my plan is to wipe the machine again once we have figured out how to get all the hardware to work. At the current rate of progress in this thread, it sounds like that might just be a few more days :) Great work so far everyone!

---

### Post by npgall on 2010-11-04
Looks like support for sound is in progress: [http://groups.google.com/group/linux.kernel/browse_thread/thread/b8122f7d331a8442/88b4d4d3fb53f281?lnk=raot&fwc=1](http://groups.google.com/group/linux.kernel/browse_thread/thread/b8122f7d331a8442/88b4d4d3fb53f281?lnk=raot&fwc=1)

:)

EDIT:
@ebsi is that your patch for sound?
@mfrey/kosumi68 is there any way you can incorporate the patch for sound into the mactel ppa?

---

### Post by ebsi on 2010-11-05
> **npgall said:**
> Looks like support for sound is in progress: [http://groups.google.com/group/linux.kernel/browse_thread/thread/b8122f7d331a8442/88b4d4d3fb53f281?lnk=raot&fwc=1](http://groups.google.com/group/linux.kernel/browse_thread/thread/b8122f7d331a8442/88b4d4d3fb53f281?lnk=raot&fwc=1)

:)

EDIT:
@ebsi is that your patch for sound?
@mfrey/kosumi68 is there any way you can incorporate the patch for sound into the mactel ppa?

Yes, that are my patches which i try to bring into the kernel. Also the HID patch is accepted :D

---

### Post by kosumi68 on 2010-11-05
snd-hda-dkms available in the mactel ppa

With this (maverick-only) package, the cirrus-based MBP53, MBP71, MBA31 and MBA32 all get the latest support from linus' tree.

On my MBA31, I get stereo sound from the speakers and headphones. No luck with the microphone, though.

Enjoy!

---

### Post by kosumi68 on 2010-11-05
The pommed package is not overly useful on the MBA31, so here is an alternative way of switching the keyboard fn keys:
```

sudo -i
echo "options hid-apple fnmode=2" > /etc/modprobe.d/apple-fn-key.conf
depmod -a
update-initramfs -u

```

---

### Post by mfrey on 2010-11-05
I am still not having any luck with screen brightness.  Anyone else having any luck?

---

### Post by Dreamsorcerer on 2010-11-05
> **kosumi68 said:**
> snd-hda-dkms available in the mactel ppa

With this (maverick-only) package, the cirrus-based MBP53, MBP71, MBA31 and MBA32 all get the latest support from linus' tree.

On my MBA31, I get stereo sound from the speakers and headphones. No luck with the microphone, though.

Enjoy!

Just installed the package, but still no sound from the speakers... MBA 3,2

---

### Post by Dreamsorcerer on 2010-11-05
Has anybody tried installing 64 bit? I realised I had installed 32 bit and was only getting 2.7 GB RAM, so I tried to install 64 bit. The disc booted to a bland GRUB screen, and after selecting try Ubuntu, it goes to a blank screen and nothing happens, no disc activity or anything. Not very impressive.

---

### Post by Dreamsorcerer on 2010-11-05
> **mfrey said:**
> OK -- I just uploaded btusb-dkms to the Mactel PPA.

This seems to have backfired on my machine. I setup the mouse on OS X before I installed Ubuntu, and despite Ubuntu not believing that a BT adapter was present, the mouse worked just fine.

Now that it knows there's a BT adapter, it asked me if I wanted to allow the mouse to connect when I turned it on, and after granting access it didn't work. I then tried setting it up as a new device, it found it just fine, but failed to connect.

---

### Post by litemotiv on 2010-11-05
> **Dreamsorcerer said:**
> Has anybody tried installing 64 bit? I realised I had installed 32 bit and was only getting 2.7 GB RAM, so I tried to install 64 bit. The disc booted to a bland GRUB screen, and after selecting try Ubuntu, it goes to a blank screen and nothing happens, no disc activity or anything. Not very impressive.

I think most are running x64 here. Did you try adding nomodeset to the grub kernel line?

edit: also, please edit your posts instead of adding multiple new ones after each other, it helps to keep the thread clean.

---

### Post by kosumi68 on 2010-11-05
> **Dreamsorcerer said:**
> Just installed the package, but still no sound from the speakers... MBA 3,2

I trust you switched everything on in alsamixer while testing?

---

### Post by Dreamsorcerer on 2010-11-05
> **litemotiv said:**
> I think most are running x64 here. Did you try adding nomodeset to the grub kernel line?

I tried with, without, and the check disk for defects, all options resulting in a blank screen, doing nothing. If your running it on x64, then I'll try a new disc or something.

> **kosumi68 said:**
> I trust you switched everything on in alsamixer while testing?

Ahha, didn't think about it, found it, adding to the wiki now.

---

### Post by Dreamsorcerer on 2010-11-06
Right, I've tried with a new disc, still nothing. When I hit F1 to boot, it spins up the disc as if it were loading for about 20 seconds, and then the drive just dies. Blank screen all the way through.

---

### Post by bwatson009 on 2010-11-06
> **Dreamsorcerer said:**
> Right, I've tried with a new disc, still nothing. When I hit F1 to boot, it spins up the disc as if it were loading for about 20 seconds, and then the drive just dies. Blank screen all the way through.

I had this exact same experience. What type of optical drive are you using?

---

### Post by Dreamsorcerer on 2010-11-06
> **bwatson009 said:**
> I had this exact same experience. What type of optical drive are you using?

The Superdrive, it worked fine with the 32 bit installer.

---

### Post by ebsi on 2010-11-06
I was so free and added the grub settings to the wiki page.

---

### Post by Luke.Hoersten on 2010-11-06
Has anyone been able to get ubuntu installed on the air using just a USB key (no CD drive or anything)?

---

### Post by dave1164 on 2010-11-07
> **Luke.Hoersten said:**
> Has anyone been able to get ubuntu installed on the air using just a USB key (no CD drive or anything)?

Yes! The default Ubuntu Startup Disk Creator didn't work for me in this case, so I used Unetbootin (494) to create a USB stick to boot. 

I then shrinked the OS X partition (128GB -> 50GB), created a new 2GB FAT (sda3) partition (and another big FAT partition to satisfy OS X), installed rEFIT and dd'ed my 2GB USB boot partition to the new small FAT partition on the SSD - all from inside OS X.

When booted into the 10.10 installer (64bit, nomodeset) I had to do two things before the installer was able to run: "sudo umount -l -r -f /cdrom" (see: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452)) and fix patch "/usr/share/ubiquity/install.py" (see: [http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0](http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0)). (Fixed 'install.py' is attached.) 

Via Disk Util I removed the big FAT partition placeholder and created three partitions instead: a 10GB/ext4 (sda4) for Ubuntu target, one 4GB swap (sda5) and a big ext4 partition (sda6) for my working files. This way I can quickly dd clone the 10GB Ubuntu installation to a separate drive or filesystem. So in a case of emergency I don't have to go through all this again.

After the Ubuntu installer was done, I was still not able to boot into Ubuntu on the 10GB partiton. For some reason the installer did not create me a kernel. I had to boot via the 2GB installer partition again, mount the 10GB target partition, chroot to it (see: [http://ubuntuforums.org/showthread.php?t=1603365&page=7](http://ubuntuforums.org/showthread.php?t=1603365&page=7)) and (connected via WiFi now) manually run apt-get update / upgrade. 

While in chroot, I also added the mactel-support/ppa (see: [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)) and ran update/upgrade again. This way I never have to navigate through any display issues.

Still no boot! For some reason I had to manually install grub to sd4. So with the chroot in place I ran: "sudo grub-install --recheck --root-directory=/mnt /dev/sda4 --force".

Ubuntu is now a joy to use on the new Air. Many thanks to those that made this possible.

---

### Post by dave1164 on 2010-11-07
>> Fixed 'install.py' is attached

---

### Post by akbardotinfo on 2010-11-07
So, it's safe for me to buy macbook air 11" right ? I just want to use ubuntu on that :) does it work using external monitor/infocus thing for the presentation ?

Many thanks! :)

---

### Post by npgall on 2010-11-07
> **Dreamsorcerer said:**
> Has anybody tried installing 64 bit? I realised I had installed 32 bit and was only getting 2.7 GB RAM, so I tried to install 64 bit. The disc booted to a bland GRUB screen, and after selecting try Ubuntu, it goes to a blank screen and nothing happens, no disc activity or anything. Not very impressive.

I had been running 32-bit too, and when I saw your post I checked and yes mine was only showing 2.7GB RAM too. So today I tried to reinstall with 64-bit too, and got the same issue - screen goes blank during boot, even with nomodeset.

I think I figured it out- hold ALT when you switch on the machine. This causes the machine's built-in firmware to display icons for the various disks/partitions it can boot from.

With the 64-bit disc in the drive, it displays *2* icons for booting from CD - one labeled "Windows" and one labeled "EFI boot". With the 32-bit ubuntu disc it only displayed one icon, labeled "Windows" (even though it's a Linux disc :/).

Anyway by default (if you don't hold down ALT) with the 64-bit disc, the machine seems to choose the "EFI boot" option which doesn't work once you get past that bland grub menu. Instead, hold ALT, then click the CD icon labeled "Windows". This boots to the same graphical boot menu that the 32-bit ubuntu displays by default, and ubuntu does boot from that menu just fine (after choosing nomodeset as before).

Incidentally, I realised that this built-in boot menu effectively renders installing rEFIt on this machine unnecessary, since it lets you choose individual partitions to boot from and not just disks. Anyway that's no longer relevant for me as I have just wiped the machine and have ubuntu (64-bit) only now :)

---

### Post by npgall on 2010-11-07
> **akbardotinfo said:**
> So, it's safe for me to buy macbook air 11" right ? I just want to use ubuntu on that does it work using external monitor/infocus thing for the presentation ?

@akbardotinfo I think it's fairly safe. I pretty much had no intention of sticking with OS X either when I bought this (11" MB Air).

I think the install process is mostly painless now, and I didn't have to compile the kernel or anything! Still there are a few manual steps to be taken, but just follow the wiki. Certainly I'd guess it should be totally painless by the time the next ubuntu release comes out.

Re:connecting to external displays- I have tested HDMI output (using this Neet adapter: [http://www.amazon.co.uk/gp/product/B002ERBFYM/](http://www.amazon.co.uk/gp/product/B002ERBFYM/)) and I can report that video out to a HDTV works perfectly, but for now I can't get audio over HDMI to work.

In ubuntu sound preferences it does see HDMI audio output, but when I select it there is just silence. Audio over HDMI did work when I tested from OS X though, so it must be some issue with the nvidia driver (and yes audio over HDMI works out of the box on my other intel-based laptop). I actually wish this machine used intel graphics/chipset instead of nvidia, nvidia is a bit of a black sheep on linux these days. Nvidia are you listening? (probably not)

In terms of hardware, everything is working for me now (video, audio, webcam, wifi, bluetooth (even BT audio to my home stereo), 3D effects, webcam, touchpad, suspend) and the only remaining niggles that I have noticed are:

[LIST]
[*]audio over HDMI
[*]wifi only goes up to 54Mbps with the 'wl' driver for now (happily it looks like this will be fixed very soon though: [http://www.zdnet.com/blog/networking/broadcom-makes-its-wi-fi-chipsets-more-linux-friendly/138](http://www.zdnet.com/blog/networking/broadcom-makes-its-wi-fi-chipsets-more-linux-friendly/138))
[*]the lack of modesetting support by nvidia makes the boot up sequence a bit ugly
[*]it looks (to me) like nvidia graphics is running with 16-bit colour depth or something (even though nvidia settings says otherwise), as I see some colour banding on the default ubuntu wallpaper. It might just be me, because it looks fine when I view videos or photos. Or it might be some nvidia "feature" that I don't need like digital vibrance interfering, which I need to turn off somehow. Or alternatively, maybe the LCD on this new mac is so vivid that it shows detail that other LCDs just blur?
[/LIST]
 @ebsi a big thanks for those patches, the work you have done in the last week has been awesome

@kosumi68 thanks for adding to the ppa. Re: internal mic- both the internal speakers and internal microphone work for me now- check the mic is not muted in alsamixer and then make sure in sound preferences the radio button in "choose a device for sound input" is actually selected- there is only one item in that list but it was still not selected by default for me.

EDIT: above it's not Nvidia driver which is at fault as it turns out, it's actually that the Apple LCD supports only 6 bits per colour channel. As nice as the LCD looks, it doesn't support 24-bit colour, needs dithering. Discussed in later posts...

---

### Post by kosumi68 on 2010-11-07
> **npgall said:**
> 
@kosumi68 thanks for adding to the ppa. Re: internal mic- both the internal speakers and internal microphone work for me now- check the mic is not muted in alsamixer and then make sure in sound preferences the radio button in "choose a device for sound input" is actually selected- there is only one item in that list but it was still not selected by default for me.

Hehe, I have gotten so used to the microphone not working that I did not even try it exhaustively - thanks for the very good news!

Regarding open issues, what about LCD backlight?

---

### Post by litemotiv on 2010-11-07
> **kosumi68 said:**
> 
Regarding open issues, what about LCD backlight?

Not working yet on 3,2

---

### Post by Luke.Hoersten on 2010-11-07
dave1164, thanks a lot! Everything worked except the last step regarding grub. I can boot into the Ubuntu install once, but every time I reboot, I get dropped back into a grub shell and can't boot. Any ideas?

---

### Post by npgall on 2010-11-07
> **kosumi68 said:**
> Regarding open issues, what about LCD backlight?

Actually that is another issue, I just tested - on MBA 3,1 it doesn't work either- the GUI brightness indicator updates according to pressing backlight up/down buttons, but the actual LCD brightness doesn't change.

---

### Post by Luke.Hoersten on 2010-11-07
> **Luke.Hoersten said:**
> dave1164, thanks a lot! Everything worked except the last step regarding grub. I can boot into the Ubuntu install once, but every time I reboot, I get dropped back into a grub shell and can't boot. Any ideas?
Pre instructions from [http://ubuntuforums.org/showthread.php?t=1515526](http://ubuntuforums.org/showthread.php?t=1515526) I found that the grub boot prefix is incorrect.

---

### Post by Luke.Hoersten on 2010-11-07
Has anyone been successful at booting a USB key live image? That would make this whole process a lot easier for people without the external cdrom drive (probably most people).

---

### Post by eee.c on 2010-11-07
> **npgall said:**
> 
[*]it looks (to me) like nvidia graphics is running with 16-bit colour depth or something (even though nvidia settings says otherwise), as I see some colour banding on the default ubuntu wallpaper. It might just be me, because it looks fine when I view videos or photos. Or it might be some nvidia "feature" that I don't need like digital vibrance interfering, which I need to turn off somehow. Or alternatively, maybe the LCD on this new mac is so vivid that it shows detail that other LCDs just blur?

I noticed that as well. It can be improved in the nvidia settings, under "GPU 0 - (GeForce 320M)" -> "DFP-2 - (Apple Color LCD)", enabling dithering and choosing a depth of 6bpc.  Unfortunately, I have to reset that upon each reboot (all other nvidia settings are retained).

Clearly, that is not the ultimate solution, but it makes things a bit more bearable.

---

### Post by ebsi on 2010-11-08
> **npgall said:**
> Actually that is another issue, I just tested - on MBA 3,1 it doesn't work either- the GUI brightness indicator updates according to pressing backlight up/down buttons, but the actual LCD brightness doesn't change.


Check the [MacBookAir3,1(2) Wiki Page]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") and follow the instructions for "LCD Backlight".

---

### Post by kosumi68 on 2010-11-08
> **ebsi said:**
> Check the [MacBookAir3,1(2) Wiki Page]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") and follow the instructions for "LCD Backlight".

Thanks ebsi, I can confirm that the backlight works after following those instructions. It seems the vendor-specific settings did the trick.

To clarify: the settings make gnome-power-manager and the brightness keys work using /sys/class/backlight/mbp_backlight/brightness, which can also be changed manually. Pommed is thus not needed.

@mario: It seems mbp-nbidia-bl sets the wrong brightness after a resume from suspend, and for some reason, using the nvidia-bl module instead did not work.

---

### Post by litemotiv on 2010-11-08
For me adding:

```

Option          "RegistryDwords" "EnableBrightnessControl=1"

```

did the trick. 

Kudos. :)

---

### Post by ugtar on 2010-11-08
> **kosumi68 said:**
> 
@mario: It seems mbp-nbidia-bl sets the wrong brightness after a resume from suspend, and for some reason, using the nvidia-bl module instead did not work.

I noticed the same thing as well. After following the new instructions on the page today the backlight controls work like a charm (adding the vendor-specific setting). But, after resume from suspend to ram the screen is completely dark. I can do a blind login, and then the screen is at the lowest brightness at which point I can turn it back up using the brightness controls. Note, I need to hit the brightness DOWN button and then it pops back up to the highest setting (where it was when I suspended). Hitting brightness UP does nothing, presumably because it thinks its already there...

Thanks for all the effort guys! This is very close!

---

### Post by ashikase on 2010-11-08
I've been using Ubuntu Server 32-bit (with "awesome" window manager) for about a week on a MacBookAir3,1 with a Japanese keyboard. A few issues...

1) Initially, my trackpad was working well (tap to click, etc) with the synaptics driver. At some point, apparently after installing the hid-apple dkms module, my keyboard and trackpad quit working. I ended up removing and reinstalling the linux-image package (kernel and modules).

Now my trackpad does not seem to work with either synaptics or xf86-input-multitouch. (Actually, multitouch loaded *once*, for some unknown reason). I can only point and click, but not tap, scroll etc.

I'm assuming that hid-apple-dkms from the ppa is needed? What about hid-dkms?

With hid-apple-dkms, it does not get loaded at boot. When I added hid-apple to /etc/modules, it loaded but crashed in apple_report_fixup (it appears that rsize is being passed the actual value instead of a pointer to a value).

So... what modules, settings might I need to get the trackpad to work?

2) With macfanctld loaded, the fan turns on and off every few seconds. Judging from the output of sensors, my best guess is that it is due to TCZ3/TGZ3 which seem to switch between 0 and 255 degrees, but I am not familiar enough with sensors to know for certain.

3) Following the backlight directions on the wiki at this time, I am able to change the brightness by echoing a value, but not via the hotkeys. I have gnome-power-manager installed, but I'm guessing this issue might be because I don't have hid-apple loaded?

Any advice on any of these issues is appreciated.

---

### Post by Luke.Hoersten on 2010-11-08
> **ashikase said:**
> 
2) With macfanctld loaded, the fan turns on and off every few seconds. Judging from the output of sensors, my best guess is that it is due to TCZ3/TGZ3 which seem to switch between 0 and 255 degrees, but I am not familiar enough with sensors to know for certain.


I'm having the same issue. Quite annoying. If anyone needs help experimenting I'd be glad to help.

---

### Post by Dreamsorcerer on 2010-11-08
> **npgall said:**
> I think I figured it out- hold ALT when you switch on the machine. This  causes the machine's built-in firmware to display icons for the various  disks/partitions it can boot from.
 
Thanks for that, worked like a charm, added the trouble shooting info to the wiki.

 > **ebsi said:**
> Check the [MacBookAir3,1(2) Wiki Page]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") and follow the instructions for "LCD Backlight".

That also worked like a charm.

I've condensed the new additions to the wiki with the post-install instructions, in an attempt to reduce the number of steps required to fully configure the system. A new user should now be able to complete the post-install in under 5 mins, I just tried this out after installing the 64 bit version, and it all works.

There are only a handful of minor issues I have left, one of them specific to the Macbook.[INDENT]There is a discrepancy with the touchpad. I noticed that things like scrolling and and right click didn't work all the time. On closer inspection it seems that multitouch doesn't work if: atleast one finger is in the bottom ~20% of the trackpad AND the fingers are not positioned horizontally on the trackpad.
This is on a MacBookAir3,2

[/INDENT]Edit: Also, the backlight setting doesn't seem to save after a reboot. Keeps defaulting to max brightness, anybody got a fix for this?

---

### Post by litemotiv on 2010-11-08
I'm getting a make-error compiling bcm5974 with GCC4.5.1

```

c:356:2: error: implicit declaration of function ‘input_set_events_per_packet’

```

Does anyone know how i can fix that?

---

### Post by kosumi68 on 2010-11-08
> **litemotiv said:**
> I'm getting a make-error compiling bcm5974 with GCC4.5.1

```

c:356:2: error: implicit declaration of function ‘input_set_events_per_packet’

```

Does anyone know how i can fix that?

Looks like you are running the maverick version on a non-maverick kernel. That is not supported, sorry - all kinds of things could go wrong. In particular because the maverick package depends on a hid module that is tightly connected to the kernel version.

---

### Post by litemotiv on 2010-11-08
> **kosumi68 said:**
> Looks like you are running the maverick version on a non-maverick kernel. That is not supported, sorry - all kinds of things could go wrong. In particular because the maverick package depends on a hid module that is tightly connected to the kernel version.

Ouch, you're right, this is a problem...

These patches were already submitted upstream right? Maybe my best bet is to wait until this hits the kernel..

---

### Post by kosumi68 on 2010-11-09
> **kosumi68 said:**
> To obtain the right trackpad dimensions for the MBA 3,2, it would be great if someone with that machine could do this:
```

sudo -i
echo 9 > /sys/module/bcm5974/parameters/debug
tail -f /var/log/debug | grep raw

```

Move the finger around the edges of the trackpad and note the minimum and maximum values in the X and Y direction. To restore:
```

echo 0 > /sys/module/bcm5974/parameters/debug
exit

```



Did anyone get a chance to look at this? If those numbers are off too much, the clicking area will not be properly set, for instance. It would be great to get it right in the kernel from the beginning. Thanks!

---

### Post by hiboo on 2010-11-09
> **kosumi68 said:**
> Did anyone get a chance to look at this? If those numbers are off too much, the clicking area will not be properly set, for instance. It would be great to get it right in the kernel from the beginning. Thanks!

I tried that on my MBA3,2 (13") and those are the extremest values I could get:

x-axis: -4620 <-> +5140
y-axis: -150 <-> +6600

Thank you guys for your good work, I hope this can help!

---

### Post by OpenOS on 2010-11-09
is this about the recent release of the macbook air?

---

### Post by ebsi on 2010-11-09
> **kosumi68 said:**
> Did anyone get a chance to look at this? If those numbers are off too much, the clicking area will not be properly set, for instance. It would be great to get it right in the kernel from the beginning. Thanks!

Attached is a log output, moving the finger from the top left, to top right, to bottom right, to bottom left, to top left.

---

### Post by kosumi68 on 2010-11-09
> **hiboo said:**
> I tried that on my MBA3,2 (13") and those are the extremest values I could get:

x-axis: -4620 <-> +5140
y-axis: -150 <-> +6600

Thank you guys for your good work, I hope this can help!

It does, thank you very much! The bcm5974-dkms package has been updated with the new values.

---

### Post by npgall on 2010-11-09
> **eee.c said:**
> enabling dithering and choosing a depth of 6bpc.  Unfortunately, I have to reset that upon each reboot (all other nvidia settings are retained)

Yes, that does fix the issue. Apparently the root cause of the colour banding we see is that Apple use 6-bit LCDs which support only 262144 colours instead of 16 million. So we need to enable dithering at 6 bits per colour channel to smooth colour gradients.

The documentation for the Nvidia driver here - [http://us.download.nvidia.com/XFree86/Linux-x86/260.19.12/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.12/README/xconfigoptions.html) - mentions how to enable dithering and set dithering mode in xorg.conf, but unfortunately it does not mention how to save the required dithering depth (6 bpc) so that it persists after reboots. I have tried to set things like "DitheringDepth" but it does not seem to pick up on that.

I have mailed NVidia support to raise the issue / ask for advice, I'll post here when I hear back.

---

### Post by Luke.Hoersten on 2010-11-09
> **ashikase said:**
> With macfanctld loaded, the fan turns on and off every few seconds. Judging from the output of sensors, my best guess is that it is due to TCZ3/TGZ3 which seem to switch between 0 and 255 degrees, but I am not familiar enough with sensors to know for certain.

The following is a workaround for this.

Like ashikase mentioned, TCZ3 and TGZ3 both seem to be toggling between 0 and 255 degrees which causes the average temp to jump and triggers the fan. To exclude the misbehaving sensors:

[LIST=1]
[*]Stop the macfanctld with "sudo /etc/init.d/macfanctld stop".
[*]Run "macfanctld -f" to obtain the list of sensors and their associated ID numbers.
[*]Open "/etc/macfanctl.conf" and add the numbers for TCZ3 and TGZ3 sensors to the "exclude:" list. Mine were 8 and 14 respectively. Ex: "exclude: 8 14". Note it's "exclude" and not "excluded".
[*]Run "macfanctld -f | grep exclude" and confirm temp*_input are in the list.
[*]Restart the daemon with "sudo /etc/init.d/macfanctld start".
[/LIST]

---

### Post by ebsi on 2010-11-10
> **npgall said:**
> Yes, that does fix the issue. Apparently the root cause of the colour banding we see is that Apple use 6-bit LCDs which support only 262144 colours instead of 16 million. So we need to enable dithering at 6 bits per colour channel to smooth colour gradients.

The documentation for the Nvidia driver here - [http://us.download.nvidia.com/XFree86/Linux-x86/260.19.12/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.12/README/xconfigoptions.html) - mentions how to enable dithering and set dithering mode in xorg.conf, but unfortunately it does not mention how to save the required dithering depth (6 bpc) so that it persists after reboots. I have tried to set things like "DitheringDepth" but it does not seem to pick up on that.

I have mailed NVidia support to raise the issue / ask for advice, I'll post here when I hear back.

Try to run this commands :

```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/ColorRange[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```

I inserted them to :

```
/etc/gdm/Init/Default
```

at the end before the exit.

Will add it to the WIKI later.

---

### Post by ebsi on 2010-11-10
> **ebsi said:**
> Try to run this commands :

```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/ColorRange[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```

I inserted them to :

```
/etc/gdm/Init/Default
```

at the end before the exit.

Will add it to the WIKI later.

Added the infos for gdm to the WIKI and also howto calibrate the panel.

---

### Post by litemotiv on 2010-11-10
> **ebsi said:**
> Try to run this commands :

```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/ColorRange[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```



That's interesting stuff ebsi, if that works it will be very useful for MBP owners too (since they also have 6-bit panels). I can't find any background info on those switches though, DitheringDepth only shows up in Google for this thread and two source-code documents. Where did you get them from?

---

### Post by ebsi on 2010-11-10
> **litemotiv said:**
> That's interesting stuff ebsi, if that works it will be very useful for MBP owners too (since they also have 6-bit panels). I can't find any background info on those switches though, DitheringDepth only shows up in Google for this thread and two source-code documents. Where did you get them from?

```
nvidia-settings -q all
```

Shows all settings. Then i started to experiment.

---

### Post by _mario_ on 2010-11-10
> **dave1164 said:**
> 
...
Still no boot! For some reason I had to manually install grub to sda4. So with the chroot in place I ran: "sudo grub-install --recheck --root-directory=/mnt/dev/sda4 --force".

Ubuntu is now a joy to use on the new Air. Many thanks to those that made this possible.

But please note, there is a drawback. If you install grub into a partition using blocklists (this is what --force does), you have to reinstall grub the same way (via chroot) every time you upgrade grub, because you can't (re-)install grub from the running system. In fact the package upgrade will attempt to install grub, but the result isn't bootable. You have been warned. Does also happen with my install due to an encrypted root/home partition which needs a separate boot partition.

ciao,
Mario

---

### Post by Dreamsorcerer on 2010-11-10
> **kosumi68 said:**
> It does, thank you very much! The bcm5974-dkms package has been updated with the new values.

I updated, but it doesn't seem to have made a difference, there is still the multitouch discrepancy I mentioned earlier.

---

### Post by _mario_ on 2010-11-10
LCD backlight, Part 2: In order to finally track down those issues, I uploaded new versions of both packages, that also contain a diagnostics script.

1. As the MacBook Air 3,1(2) is identical to the MacBook 7,1 and the MacBook Pro 7,1, nvidia-bl should also work there. Please install nvidia-bl-dkms and run:
```
$ /usr/src/nvidia_bl-0.17.3/scripts/nvidia-bl-diagnostics --load
```
The script will display some information and finally load the driver (if necessary) and attempt to adjust backlight. Does it work? Please also report which graphics driver you are using as well as whether you enabled options like 'EnableBrightnessControl' (which shouldn't be necessary).

2. Same procedure for mbp-nvidia-bl:
```
$ /usr/src/mbp_nvidia_bl-0.25.4/scripts/mbp-nvidia-bl-diagnostics --load
```

Thanks & ciao,
Mario

---

### Post by litemotiv on 2010-11-10
> **ebsi said:**
> Try to run this commands :

```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/ColorRange[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```


I'm not sure about the ColorRange one, when i use that all the blacks become greys on my display.

---

### Post by kosumi68 on 2010-11-10
Greetings _mario_,

All tests below are performed after boot.

1. mbp-nvidia-bl + EnableBrightnessControl=1

Brightness keys work
Your diagnostics script for mbp works

2. mbp-nvidia-bl + comments brightness line

Brightness keys do not work
Your diagnostics script produces no error, but there is no effect

3. nvidia-bl + EnableBrightnessControl=1

Brightness keys do not work
Your diagnostics script produces no error, but there is no effect

Odd!

---

### Post by hiboo on 2010-11-10
> **Dreamsorcerer said:**
> I updated, but it doesn't seem to have made a difference, there is still the multitouch discrepancy I mentioned earlier.

I agree, I also updated and couldn't see much difference. For me, the touchpad works quite well, EXCEPT it doesn't have a proper "dead zone" at the bottom (~last 20%): leaving one finger placed here generates unwanted movements of the pointer (interferences).

Is this the current state of the driver or is it just a matter of tweaking the settings for this particular touchpad model?

I looked at the log file Ebsi posted and his values are more or less:
x-axis: -4550 <-> +5060
y-axis: -135 <-> +5240

versus the values I posted:
x-axis: -4620 <-> +5140
y-axis: -150 <-> +6600

There is a big difference on the +y axis, so maybe I went a bit too much to the extremes? Not sure what kind of values are expected.

Also, out of curiosity I wanted to checkout the source of bcm5974-dkms, but could only find an old version (using "git clone http://bitmath.org/git/bcm5974-dkms.git").
Is there an easy way to access the latest version on the Mactel PPA that I totally missed out..?

---

### Post by npgall on 2010-11-10
> **ebsi said:**
> Try to run this commands :

```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/ColorRange[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```I inserted them to :

```
/etc/gdm/Init/Default
```at the end before the exit..

@ebsi Nice fix, thanks. That solves the issue for me. However I'm not sure about the ColorRange one, I set DitheringMode there instead:

```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringMode[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```

---

### Post by npgall on 2010-11-10
Do I need to install macfanctld - what will that do? My laptop seems to be working quite well without this, is there a danger it will overheat without?

---

### Post by kosumi68 on 2010-11-10
> **hiboo said:**
> I agree, I also updated and couldn't see much difference. For me, the touchpad works quite well, EXCEPT it doesn't have a proper "dead zone" at the bottom (~last 20%): leaving one finger placed here generates unwanted movements of the pointer (interferences).

Is this the current state of the driver or is it just a matter of tweaking the settings for this particular touchpad model?

I looked at the log file Ebsi posted and his values are more or less:
x-axis: -4550 <-> +5060
y-axis: -135 <-> +5240

versus the values I posted:
x-axis: -4620 <-> +5140
y-axis: -150 <-> +6600

There is a big difference on the +y axis, so maybe I went a bit too much to the extremes? Not sure what kind of values are expected.

Also, out of curiosity I wanted to checkout the source of bcm5974-dkms, but could only find an old version (using "git clone http://bitmath.org/git/bcm5974-dkms.git").
Is there an easy way to access the latest version on the Mactel PPA that I totally missed out..?

The values are for the 11'' and 13'' models, respectively. The update was about getting accurate device data in the kernel. The multitouch experience with xf86-input-multitouch is a different matter, with its own thread.

You find the installed sources in /usr/src/bcm5974*. If you by old version meant the last version, that is correct - I was a bit slow to push.

---

### Post by kosumi68 on 2010-11-10
> **npgall said:**
> Do I need to install macfanctld - what will that do? My laptop seems to be working quite well without this, is there a danger it will overheat without?

This is actually very interesting -- the new MBA31 feels a lot, lot cooler. A combination of the new GPU and the plastic top side, perhaps. I only had the fans spin up a couple of times during heavy load. The question is what operating temperatures are good for these particular chips.

---

### Post by Luke.Hoersten on 2010-11-10
> **_mario_ said:**
> But please note, there is a drawback. If you install grub into a partition using blocklists (this is what --force does), you have to reinstall grub the same way (via chroot) every time you upgrade grub, because you can't (re-)install grub from the running system. In fact the package upgrade will attempt to install grub, but the result isn't bootable. You have been warned. Does also happen with my install due to an encrypted root/home partition which needs a separate boot partition.

ciao,
Mario

What do you suggest to do? How can I fix/recover from this? Installing grub on a separate boot partition?

---

### Post by ebsi on 2010-11-10
> **kosumi68 said:**
> This is actually very interesting -- the new MBA31 feels a lot, lot cooler. A combination of the new GPU and the plastic top side, perhaps. I only had the fans spin up a couple of times during heavy load. The question is what operating temperatures are good for these particular chips.

It is indeed. When you have a longer compile job running the fan spins itselfe up. Checked with sensors. Looks like the SMC controller in the MBP31 is doing it's job without telling it to it.

---

### Post by Luke.Hoersten on 2010-11-10
> **kosumi68 said:**
> This is actually very interesting -- the new MBA31 feels a lot, lot cooler. A combination of the new GPU and the plastic top side, perhaps. I only had the fans spin up a couple of times during heavy load. The question is what operating temperatures are good for these particular chips.

I added the fix for the oscillating fan problem to the wiki.

---

### Post by Luke.Hoersten on 2010-11-10
It seems like tapping is not as responsive as on OS X. Sometimes I have to tap 2-3 times before it's registered as a click.

---

### Post by ugtar on 2010-11-11
> **hiboo said:**
> 
versus the values I posted:
x-axis: -4620 <-> +5140
y-axis: -150 <-> +6600


FWIW I got pretty much the exact same values on my mba 3,2 13in.

> **ebsi said:**
> 
It is indeed. When you have a longer compile job running the fan spins itselfe up. Checked with sensors. Looks like the SMC controller in the MBP31 is doing it's job without telling it to it.

I agree, on my host the fan seems to spin up appropriately as needed already without having to install macfanctld.

---

### Post by ebsi on 2010-11-11
> **Luke.Hoersten said:**
> I added the fix for the oscillating fan problem to the wiki.

This macfanctld patch autoexcludes the suspecting sensors on the macbookair 3,1(2).

This are the excluded sensors :

```
"TCZ3" "TCZ4" "TCZ5" "TGZ3" "TGZ4" "TGZ5" "TH0F" "TH0O"
```

---

### Post by swidowski on 2010-11-11
I can not get the internal speakers working on either 32bit or 64bit 10.10. I walked through the post install instructions both times.  I have also checked alsamixer to make sure all volumes are up.  I have a 3,2 macbook air.  Is sound / the internal speakers working for other people? Any help is appreciated.

---

### Post by _mario_ on 2010-11-12
> **Luke.Hoersten said:**
> What do you suggest to do? How can I fix/recover from this? Installing grub on a separate boot partition?

First, I assumed you used the --force option to handle this particular warning:
```

/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

If yes, then a separate boot partition will not help. Read the [GRUB wiki]("http://grub.enbug.org/BIOS_Boot_Partition"). The bottom line is: Use a very small dummy partition, that isn't used for anything else. But not the EFI system partition if present. Unfortunately, this makes triple/quad-boot installations a mess.

ciao,
Mario

---

### Post by hiboo on 2010-11-12
> **kosumi68 said:**
> The values are for the 11'' and 13'' models, respectively. The update was about getting accurate device data in the kernel. The multitouch experience with xf86-input-multitouch is a different matter, with its own thread.

You find the installed sources in /usr/src/bcm5974*. If you by old version meant the last version, that is correct - I was a bit slow to push.

Thank you for taking time to clarify things, appreciate it. Arg, and I didn't know the package simply installed the sources in /usr/src so thanks for that as well :)

---

### Post by pbhedlund on 2010-11-12
Hello,

Thanks for a great thread.

> **dave1164 said:**
> Yes! The default Ubuntu Startup Disk Creator didn't work for me in this case, so I used Unetbootin (494) to create a USB stick to boot. 

I then shrinked the OS X partition (128GB -> 50GB), created a new 2GB FAT (sda3) partition (and another big FAT partition to satisfy OS X), installed rEFIT and dd'ed my 2GB USB boot partition to the new small FAT partition on the SSD - all from inside OS X.

When booted into the 10.10 installer (64bit, nomodeset) I had to do two things before the installer was able to run: "sudo umount -l -r -f /cdrom" (see: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452)) and fix patch "/usr/share/ubiquity/install.py" (see: [http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0](http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0)). (Fixed 'install.py' is attached.) 

Via Disk Util I removed the big FAT partition placeholder and created three partitions instead: a 10GB/ext4 (sda4) for Ubuntu target, one 4GB swap (sda5) and a big ext4 partition (sda6) for my working files. This way I can quickly dd clone the 10GB Ubuntu installation to a separate drive or filesystem. So in a case of emergency I don't have to go through all this again.

After the Ubuntu installer was done, I was still not able to boot into Ubuntu on the 10GB partiton. For some reason the installer did not create me a kernel. I had to boot via the 2GB installer partition again, mount the 10GB target partition, chroot to it (see: [http://ubuntuforums.org/showthread.php?t=1603365&page=7](http://ubuntuforums.org/showthread.php?t=1603365&page=7)) and (connected via WiFi now) manually run apt-get update / upgrade. 

While in chroot, I also added the mactel-support/ppa (see: [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)) and ran update/upgrade again. This way I never have to navigate through any display issues.

Still no boot! For some reason I had to manually install grub to sd4. So with the chroot in place I ran: "sudo grub-install --recheck --root-directory=/mnt /dev/sda4 --force".

Ubuntu is now a joy to use on the new Air. Many thanks to those that made this possible.

Unforutnately, I can still not boot into the new install. I think I have done everything as described above. After the grub-install I get the option to boot from the HD in rEFIt, but selecting this still only gives me the UNetbootin menu.

It says to manually install grub with the chroot in place. Does that mean from the resulting root prompt or from the ubuntu prompt in a separate terminal?

Also, in the example above does --root-directory=/mnt actually refer to /tmp/mntroot as described in the post referred to?

A later post recommends creating a small dummy partition for grub. Could someone give a little more details about that procedure?

I would hate to have to buy an external cd/dvd drive just to do the install.

Thanks,
Peter

---

### Post by swidowski on 2010-11-12
Nevermind about the sound.  I missed it in the wiki.  Thanks anyway.  Everything works great.

---

### Post by swidowski on 2010-11-13
.

---

### Post by fafhrd on 2010-11-13
I have the MacBookAir3,1, and am running Gentoo on it. This forum, and the wiki, have been a handy resource.

I'm trying to get sound working. The HDMI sounds seem available, but not the actual sound card.

I'm running 2.6.35-gentoo-r12, with the patches provided earlier in the thread. I've compared them to the sources available from the ppa, and from what I can tell, their close, however, I'm not quite sure.

If someone can point me to the version of alsa (kernel or not) that works here, as well as if a model=foo line was used with snd-hda-intel, or any other hints, I'd be very appreciative!

---

### Post by fafhrd on 2010-11-13
Well, it's working now.

I upgraded to gentoo-sources-2.6.36-r1, and initially didn't have much luck. I added cb89 to the quirks alongside 0d94, and got my sound! Upon the first alsa start, I was show this:

Found hardware: "HDA-Intel" "Nvidia MCP89 HDMI" "HDA:10134206,106b6300,00100301 HDA:10de000c,10de0101,00100200" "0x10de" "0xcb89"
Hardware is initialized using a generic method
alsactl: set_control:1255: failed to obtain info for control #5 (No such file or directory)
alsactl: set_control:1255: failed to obtain info for control #6 (No such file or directory)


... but sound works. Headphone, and mute-on-jack work as expected.

Cheers, all! What great linux laptops these are. :-)

---

### Post by corn13read on 2010-11-14
How is battery life in ubuntu? I have a macbook pro and I consistently get 1-2 hours less in ubuntu than in mac.

TIA

---

### Post by Dreamsorcerer on 2010-11-15
> **corn13read said:**
> How is battery life in ubuntu? I have a macbook pro and I consistently get 1-2 hours less in ubuntu than in mac.

TIA

I didn't use OS X for long, but based on the battery indicators, it looks like they are comparable, perhaps Ubuntu is half an hour less or something. But, you have to remember OS X has been customised specifically for the machine, so comparing it to a default Ubuntu install is hardly fair, a bit of tweaking would likely get Ubuntu to the same or longer battery life.

---

### Post by litemotiv on 2010-11-15
> **Dreamsorcerer said:**
> a bit of tweaking would likely get Ubuntu to the same or longer battery life.

You will never get it the same or longer than with osx, the macbooks have so many sensors for a reason; all of them are monitored and used for power tweaking, this is something you can hardly achieve on linux. 

In general, you can expect around 10-20% less battery in linux at best, which is still very good though.

---

### Post by dentifrice on 2010-11-15
> **fafhrd said:**
> Cheers, all! What great linux laptops these are. :-)

As far as I understood, pretty much everything works after a bit of patching and tweaking, is that right? 

However, I'm concerned with the need to use non-free drivers for wifi and for graphical display. Is there an alternative in both cases? Has anyone tried using the nouveau driver for the nvidia card, for instance?

---

### Post by litemotiv on 2010-11-16
> **dentifrice said:**
> 
However, I'm concerned with the need to use non-free drivers for wifi and for graphical display. Is there an alternative in both cases? Has anyone tried using the nouveau driver for the nvidia card, for instance?

In-kernel drivers for wifi are coming in 2.6.37. Nouveau will be a matter of time, maybe they have it supported in git already, otherwise it would help to file a bugreport with the developers at freedesktop or launchpad (the former being preferred).

---

### Post by ashikase on 2010-11-16
@kosumi68:

I see that you are in charge of the hid-apple-dkms package.

I have confirmed that this module contains a bug, specifically in the apple_report_fixup() function, which leaves users with Japanese keyboards without a working keyboard/trackpad... not a fun experience :)

I've attached a patch to this post; I hope that you will consider applying it to the official package.

---

### Post by lintweaker on 2010-11-16
> **fafhrd said:**
> Well, it's working now.

I upgraded to gentoo-sources-2.6.36-r1, and initially didn't have much luck. I added cb89 to the quirks alongside 0d94, and got my sound! Upon the first alsa start, I was show this:

Found hardware: "HDA-Intel" "Nvidia MCP89 HDMI" "HDA:10134206,106b6300,00100301 HDA:10de000c,10de0101,00100200" "0x10de" "0xcb89"
Hardware is initialized using a generic method
alsactl: set_control:1255: failed to obtain info for control #5 (No such file or directory)
alsactl: set_control:1255: failed to obtain info for control #6 (No such file or directory)


... but sound works. Headphone, and mute-on-jack work as expected.

Cheers, all! What great linux laptops these are. :-)
I am a happy camper using Linux on my MBA3,1 with the patches provided in this thread. Sound from the speakers is not working for me as well with the provided patch_cirrus.c. By adding another quirk for 0x10de, 0xcb89 I do get sound from the speakers (thanks to the poster!). Maybe this quirk is really needed for the MBA 11.6"...

---

### Post by ebsi on 2010-11-16
For kernel 2.6.36 and up you need the patch from [https://bugzilla.kernel.org/show_bug.cgi?id=21182]("https://bugzilla.kernel.org/show_bug.cgi?id=21182")

cu

---

### Post by lintweaker on 2010-11-16
I have an MBA 3,1 with International English keyboard. Two keys on my keyboard provide the wrong characters when pressed.

The key with "+/-" sign and paragraph sign give me ` and ~ and the key with ' and ~ give me < and >. I've searched through the layouts but could not get find the proper layout. How can I get the proper layout?

---

### Post by dentifrice on 2010-11-16
> **litemotiv said:**
> In-kernel drivers for wifi are coming in 2.6.37. Nouveau will be a matter of time, maybe they have it supported in git already, otherwise it would help to file a bugreport with the developers at freedesktop or launchpad (the former being preferred).

Thanks for the info. Looking at the Changelog for 2.6.37-rc2 (from kernel.org), it seems like a few more MBA3,[1-2] related patches are being merged upstream.

Has anyone tried to boot the MBA3,* in EFI mode (with grub-efi)?

---

### Post by dentifrice on 2010-11-16
For backlight handling and stuff, it may be good to know that Julien Blache has just released a new *pommed* version, supporting the new macbook air models (see the following blog post: [http://blog.technologeek.org/2010/11/13/407](http://blog.technologeek.org/2010/11/13/407)).

---

### Post by flusi100 on 2010-11-17
I'm still fighting with my air3,2 trying to install 10.10. without superdrive.

> **dave1164 said:**
> 
[...]
When booted into the 10.10 installer (64bit, nomodeset) I had to do two things before the installer was able to run: "sudo umount -l -r -f /cdrom" (see: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452)) and fix patch "/usr/share/ubiquity/install.py" (see: [http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0](http://forums.linuxmint.com/viewtopic.php?f=46&t=49841&start=0)). (Fixed 'install.py' is attached.) 
[...]


Until now I successfully unmounted the cdrom, bit my ubiquity still crashes. Do I have to do more than just replacing /usr/share/ubiquity/install.py with attached file before staring the installation?:confused:

---

### Post by Luke.Hoersten on 2010-11-17
> **flusi100 said:**
> Do I have to do more than just replacing /usr/share/ubiquity/install.py with attached file before staring the installation?:confused:

That's all I did. Just replaced the .py, ran it, and it worked.

What's it failing with?

Like mentioned earlier, there were 5 problems:
[LIST=1]
[*]Can't boot off USB key :: dd it to local partition
[*]Can't see anything on boot :: Press some keys at purple screen then append boot line with "nomodeset"
[*]Can't install to/from local partition :: "sudo umount -l -r -f /cdrom"
[*]Can't get installer through time update :: Choose "install" from boot selection instead of "try"
[*]Ubiquity keeps failing :: Replace with patched install.py
[/LIST]

After this the install fails to install some stuff but you can chroot in and fix it from there.

---

### Post by flusi100 on 2010-11-18
YEP!
my fault was point 4

thanks!

---

### Post by OldAbe on 2010-11-19
I have some problems with my partitions on my driver. I cant add the last 150GB free space on my SSD drive to FAT32. 

Any one that find the time to help me. please..
Hear is some information that my be to help what I have done wrong.

Thanks
/Abe

______________________________________________________

skitgubbe@macbook-air:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb000ebb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        6713    53710940   af  HFS / HFS+
/dev/sda3   *        6729       10498    30272512    7  HPFS/NTFS
/dev/sda4           10498       11957    11718656   83  Linux


_________________________________________________________________


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

---

### Post by gschwind on 2010-11-19
> **dentifrice said:**
> 
Has anyone tried to boot the MBA3,* in EFI mode (with grub-efi)?

I did, as MBP7.1, you can boot in console mode with the standard AHCI driver (in BIOS mode the driver used is ata_generic). however you cannot use nvidia driver (I tested) and probably nouveau driver, even with bios/int10 patch from grub-efi.

Best regards

---

### Post by dentifrice on 2010-11-20
> **gschwind said:**
> I did, as MBP7.1, you can boot in console mode with the standard AHCI driver (in BIOS mode the driver used is ata_generic). however you cannot use nvidia driver (I tested) and probably nouveau driver, even with bios/int10 patch from grub-efi.

I'm confused. Are you talking about EFI booting a MacBookPro 7,1, or a MacBookAir3,*?

---

### Post by ugtar on 2010-11-21
> **npgall said:**
> @ebsi Nice fix, thanks. That solves the issue for me. However I'm not sure about the ColorRange one, I set DitheringMode there instead:

```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringMode[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```

Hey guys, FYI, usually if you install the nvidia drivers through jockey (ubuntu), a startup script is added (System->Preferences->Startup Applications), called 'Nvidia X Server Settings'. It simply runs /usr/bin/nvidia-settings --load-config-only. What that does is load the configuration from ~/.nvidia-settings-rc.

The upshot of all this is, to set color-depth, dithering, etc, you can probably just add these lines to the end of your ~/.nvidia-settings.rc

```

0/Dithering[DFP-2]=1
0/DitheringMode[DFP-2]=1
0/DitheringDepth[DFP-2]=1

```

Then you shouldn't need to add anything to /etc/gdm/Init/Default

I just verified that this works. There are a couple of differences though that might make this solution less desirable. The plus side is you don't need to muck with system files, just files in your home directory. The downside is, the change is made only for the user with the modified .rc file. So, the change only takes effect after logging in, not on the login screen, or for any other users.

---

### Post by Dreamsorcerer on 2010-11-26
Does anybody know if there is anything we can do about the EFI, either a way to configure it, so that it boots faster. Or maybe replace it with a lighter EFI, with less features (I don't need wireless networking in EFI) that can boot faster?

It seems to take 3 times as long without OS X, before it starts booting the system.

---

### Post by dentifrice on 2010-11-26
> **Dreamsorcerer said:**
> Does anybody know if there is anything we can do about the EFI, either a way to configure it, so that it boots faster. Or maybe replace it with a lighter EFI, with less features (I don't need wireless networking in EFI) that can boot faster?

It seems to take 3 times as long without OS X, before it starts booting the system.

I'm afraid I don't really understand what you're talking about. Are you talking about Apple's EFI firmware, or booting Ubuntu in EFI mode through grub-efi rather than booting it in BIOS emulation mode through grub-pc?

I previously asked whether booting GNU/Linux in EFI mode had been attempted on these new MacBookAir3 computers or not, and didn't get an answer (at least not an answer I could understand).

So, in addition to my previous question, can you clarify the following :
- did you manage to boot Ubuntu in EFI mode on a MacBookAir3,* computer?
- if so, what are the limitations? (you're mentionning non-working wireless...)

Thanks in advance. I have a MBA3,1 in the mail, so I'm trying to gather as much info as possible before I get to install it. I hope I can contribute something to the thread afterwards.

---

### Post by npgall on 2010-11-27
> **Dreamsorcerer said:**
> It seems to take 3 times as long without OS X, before it starts booting the system.

@Dreamsorcerer Did you set EFI to boot in legacy BIOS mode by default? That made a big difference for me.

See: [https://wiki.archlinux.org/index.php/MacBook#Avoid_long_EFI_wait_before_GRUB](https://wiki.archlinux.org/index.php/MacBook#Avoid_long_EFI_wait_before_GRUB)

I just timed my machine from pressing the power button to useable desktop- it takes exactly 30 seconds (with 'log in automatically'). About 10 seconds of that is stuck at the white EFI startup screen. Before running the command above I think the EFI screen would delay for even longer, for at least 30 seconds IIRC.

I'll add the link above to the wiki.

@dentifrice I tried to boot in EFI mode from the Ubuntu 10.10 64-bit CD, see earlier in the thread. It hangs after about 20 seconds. It would be nice to boot in EFI mode, as I'd guess EFI wouldn't need to load the legacy BIOS and so we wouldn't have that extra 10-second delay. However I read that the nvidia driver doesn't work in EFI mode.

---

### Post by Dreamsorcerer on 2010-11-27
> **dentifrice said:**
> or  booting Ubuntu in EFI mode through grub-efi rather than booting it in  BIOS emulation mode through grub-pc?

- if so, what are the limitations? (you're mentionning non-working wireless...)
I don't even know what grub-efi is, I'm just talking about Apple's EFI. I didn't say wireless wasn't working, I said it was an unneeded feature for an EFI, so maybe if the EFI could be replaced with version that had less features, it might boot faster. The EFI seems to have wireless builtin, which is probably how OS X has wireless connected before it's even booted.

> **npgall said:**
> @Dreamsorcerer Did you set EFI to boot in legacy BIOS mode by default? That made a big difference for me.

See: [https://wiki.archlinux.org/index.php/MacBook#Avoid_long_EFI_wait_before_GRUB](https://wiki.archlinux.org/index.php/MacBook#Avoid_long_EFI_wait_before_GRUB)

I just timed my machine from pressing the power button to useable desktop- it takes exactly 30 seconds (with 'log in automatically'). About 10 seconds of that is stuck at the white EFI startup screen. Before running the command above I think the EFI screen would delay for even longer, for at least 30 seconds IIRC.

Yeah, I done that, get about the same speed as you. But, I'm sure with OS X it only spent like 2-4 seconds at EFI, so is it this legacy BIOS thing that slows it down?

---

### Post by npgall on 2010-11-27
Yes I bet the legacy BIOS thing slows it down.

So it would be good to get Ubuntu running in EFI mode.

Just read a report here that the closed source nvidia driver does work in EFI mode on some macbooks: [http://arunraghavan.net/2010/02/pure-efi-linux-boot-on-macbooks/](http://arunraghavan.net/2010/02/pure-efi-linux-boot-on-macbooks/)

---

### Post by OpenOS on 2010-11-29
when will ubuntu be on the macbook air

---

### Post by dave1164 on 2010-11-29
> **_mario_ said:**
> But please note, there is a drawback. If you install grub into a partition using blocklists (this is what --force does), you have to reinstall grub the same way (via chroot) every time you upgrade grub, because you can't (re-)install grub from the running system. In fact the package upgrade will attempt to install grub, but the result isn't bootable. You have been warned. Does also happen with my install due to an encrypted root/home partition which needs a separate boot partition.

Hi Mario. Is "grub-install --recheck --root-directory=/mnt/dev/sda4 --force" really different from the advice given at
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)? Where, under Dual-Boot / 5. it says: "...be sure to click the “Advanced” button and choose to install the boot loader (grub) to /dev/sda3". (sda4 vs. sda3 aside.) I went through a couple of automatic kernel + grub updates by now and I don't seem to experience the problem you describe.

My remaining two issues at this point: clicking the touch pad button down always makes the mouse pointer jump to the side a bit. Which makes it a little difficult to hit the right object on the screen in some cases. Could it be they use some kind of error correction in the OSX touch pad driver to prevent this from happening? The other thing: How am I supposed to generate right click events? (I'm using a mouse to bypass these two issues. But I would rather not.)
Thanks.

---

### Post by gschwind on 2010-11-30
Hello,  >  I'm confused. Are you talking about EFI booting a MacBookPro 7,1, or a MacBookAir3,*?    Yes, I booted my MacBookAir3,2 with EFI and it work as same as MacBookPro7,1, I'm able to get console with framebuffer, but not be able to start X with nvidia driver, with or without grub-efi memory patch (copy of nvidia bios @expected memory address).  For people which want boot on EFI, there is no 3D accel in the current state of drivers. I guess there is no 2D accel at all too. I guess (I did not try because it's will not fit my need) it possible to start X with fbdev.  Note : to make BIOS as default boot (in case you wipe all MacOS X) Press "option" at boot, them in boot selection press Ctrl them your MBR drive, the arrow should be round not linear (as default). click on it. The computeur should but on BIOS mode as usual, but when you reboot BIOS mode will be selected by default.  Note2 : I guess the extras boot time is produce by BIOS operation like in PC you have some splash screen, mem check and so on.  Best regards

---

### Post by Luke.Hoersten on 2010-11-30
> **dave1164 said:**
> 
My remaining two issues at this point: clicking the touch pad button down always makes the mouse pointer jump to the side a bit. Which makes it a little difficult to hit the right object on the screen in some cases. Could it be they use some kind of error correction in the OSX touch pad driver to prevent this from happening? The other thing: How am I supposed to generate right click events? (I'm using a mouse to bypass these two issues. But I would rather not.)
Thanks.

I'm still having issues with the track pad tapping (not clicking). It doesn't seem to work consistently. Anyone have any fixes for that?

---

### Post by dentifrice on 2010-12-01
@[npgall]("http://ubuntuforums.org/member.php?u=974230") : thanks for your answer ; I expected the non-free NVIDIA driver to be the bottleneck, but FYI, I did manage to configure EFI booting on a MacBook5,2 using the proprietary NVIDIA drivers (as I couldn't get "nouveau" to work). So the NVIDIA driver is known to be compatible with EFI booting in some cases...

@gschwind : thanks for the precisions, I get it now.

---

### Post by dentifrice on 2010-12-01
Has anyone installing GNU/Linux on the new MBA taken care of SSD partition alignment? If so, which values have you used, with which tool (fdisk?)? 

There's been a number of threads on that issue over mailing-lists since SSD started to appear on the market, but no definite answer as to what to do (and I figure each SSD model differs in terms of physical blocks and stuff). 

It was my understanding that recent toolsets and kernels would take care of the partition alignment in an ok fashion, but I'm not sure which ones (especially when throwing LVM2 and dm-crypt into the mix). So if anyone has some info to share, both on disk alignment in general and specs for the MBA SSDs precisely, that'd be great!

---

### Post by umba on 2010-12-02
Took some time to get everything working properly, but thanks for the help.

---

### Post by sanicki on 2010-12-02
Following the directions [here]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") I am in the LiveCD but [unable to install]("http://ubuntuforums.org/showpost.php?p=10190707&postcount=17"). Did anyone else run into this/have a solution?

EDIT: The post below got me further, but installer keeps crashing. Seems to be related to partitioning?
> **dave1164 said:**
> I had to do two things before the installer was able to run: "sudo umount -l -r -f /cdrom" (see: [https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/313452)) and fix patch "/usr/share/ubiquity/install.py"

---

### Post by dentifrice on 2010-12-02
> **umba said:**
> Took some time to get everything working properly, but thanks for the help.

Unfortunately, it can't *really* be said that everything works properly.

I just got my MBA today and after failing to get the SSD recognized by various versions of the Debian Installer, I stumbled upon this link: [https://bugzilla.kernel.org/show_bug.cgi?id=15923](https://bugzilla.kernel.org/show_bug.cgi?id=15923)

So, in short, we're forced to use the deprecated ata_generic driver instead of AHCI (which means poor performances). That's really bad in my opinion, since the fast SSD is one of the strongest points of that machine IMHO, besides its form factor...

The only way to circumvent the problem seems to be EFI booting, which hasn't been achieved yet. Unfortunately, it's easier said than done.

---

### Post by dentifrice on 2010-12-02
> **litemotiv said:**
> Nouveau will be a matter of time, maybe they have it supported in git already, otherwise it would help to file a bugreport with the developers at freedesktop or launchpad (the former being preferred).

Here's an unsuccessful attempt: [https://bugzilla.redhat.com/show_bug.cgi?id=650949](https://bugzilla.redhat.com/show_bug.cgi?id=650949)

Nothing on [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/) yet.

---

### Post by dave1164 on 2010-12-02
> **Luke.Hoersten said:**
> I'm still having issues with the track pad tapping (not clicking). It doesn't seem to work consistently. Anyone have any fixes for that?

Ah yes, forgot to mention this. Tapping does not always result in a click - and clicking does often results in the mouse pointer jumping away a bit. 
I would really like to take a look at the touch pad driver code. Where can I find it?

---

### Post by dentifrice on 2010-12-03
> **gschwind said:**
> Hello,    Yes, I booted my MacBookAir3,2 with EFI and it work as same as MacBookPro7,1, I'm able to get console with framebuffer, but not be able to start X with nvidia driver, with or without grub-efi memory patch (copy of nvidia bios @expected memory address).

Could you share your grub.cfg entry, and the command used to generate the grub.efi image?

Unfortunately, I couldn't even get the framebuffer console to work. Upon booting, I get *ROM image is present* and then a black screen. Adding *debug=video* adds the following to the black screen but results in a freeze nonetheless: *video/efi_gop.c:357: GOP: Success*

I've tried booting both 2.6.35-23 (from maverick) and 2.6.37-7 (from natty) without success.

---

### Post by litemotiv on 2010-12-03
> **dentifrice said:**
> 
So, in short, we're forced to use the deprecated ata_generic driver instead of AHCI (which means poor performances). That's really bad in my opinion, since the fast SSD is one of the strongest points of that machine IMHO, besides its form factor...


The ata_generic performance is really very decent though, so i wouldn't worry about it too much. You'll miss about 10% throughput for now, but it's still a lot faster than any traditional drive (and many other SSD's).

---

### Post by sanicki on 2010-12-04
I am still unable to get Ubuntu 10.10 x64 installed on my 3,2 Macbook Air. This is my first time installing on Apple hardware, though I've used Ubuntu since 6.06. Can someone please help? I would prefer only Ubuntu on it, not dual boot.

I don't have a SuperDrive and [EFI doesn't see my USB DVD-ROM]("http://ubuntuforums.org/showpost.php?p=9210258&postcount=3"). Nor does it recognize bootable USB flash drives created in Ubuntu using Startup Disk Creator or [Unetbootin]("http://ubuntuforums.org/showpost.php?p=10084254&postcount=114") or in [OSX]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick").

So I installed the USB image to the SSD. First I used the Apple-provided OS X restore USB drive to create a single 256gb FAT partition then [dd'ed]("http://ubuntuforums.org/showpost.php?p=10053887&postcount=15") the Startup Disk Creator image onto it. EFI still failed to see it. I had to reinstall OS X, install rEFIt, create a second partition (again I used FAT) and copy the Ubuntu image there. Two reboots later I am able to boot into the LiveCD. (Why two? I don't know but I've repeated all of this a few times and that seems to be consistent.)

After the F6 nomodeset screen [workaround]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") I go to Try Ubuntu and try the steps [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation"). I was thwarted by the cdrom being mounted and the installer freezing so I returned to the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=10084254&postcount=114").

Sometimes the partitioner crashes, sometimes it partitions then crashes, but I cannot get Ubuntu to install. Thanks in advance for any help.

EDIT: Business trip tomorrow so getting desperate. If I buy the $80 SuperDrive (which I'll end up only using this once, ugh) will the Ubuntu installer ISO boot from it?

---

### Post by dentifrice on 2010-12-04
> **dentifrice said:**
> Nothing on [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/) yet.

I hadn't looked close enough. Here's a bugreport about nouveau failing on the MacBookAir3,1 : [https://bugs.freedesktop.org/show_bug.cgi?id=31676](https://bugs.freedesktop.org/show_bug.cgi?id=31676)

---

### Post by dentifrice on 2010-12-04
> **sanicki said:**
> EDIT: Business trip tomorrow so getting desperate. If I buy the $80 SuperDrive (which I'll end up only using this once, ugh) will the Ubuntu installer ISO boot from it?

Yes, it will (that's how I installed mine, using Ubuntu's alternate install CD). I'll be using the SuperDrive more than once, so I didn't look into the alternatives.

---

### Post by sanicki on 2010-12-04
> **dentifrice said:**
> Yes, it will (that's how I installed mine, using Ubuntu's alternate install CD). I'll be using the SuperDrive more than once, so I didn't look into the alternatives.

If you ever make it to Sedona, AZ, I owe you a beer. Why doesn't the wiki say "You just spent an insane amount of money on Apple hardware, save yourself some pain and spring for the Superdrive and ethernet dongle" then direct folks to the Alternate CD? Would have saved me much aggravation. Thanks.

---

### Post by eyerouge on 2010-12-04
**Problem:** I get stuck after the install of Ubuntu 10.10 (64 bit) when selecting *"Try"* or *"Install"* in the LiveCD menu. After the purple screen and Ubuntu 10.10 text and loading dots disappear I get the following message:

```
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system. 
```

**What I have done so far**
[LIST]
[*]I don't have an external dvd/cd-rom and would like to avoid buying one, thus I have taken the course of installing Ubuntu without it, by dumping a dd of a USB stick with the install cd onto the Airs partitions.
[*]I partitoned the HD into 2 *additional* partitions, using the crap found in OSX:
[*]1 ms dos partition (fat) for the Ubuntu LiveCD that I have dd'd from a USB (which I created in Ubuntu 10.10 with the start disk utility)
[*]1 ms dos partition that will be the target of the installation and hold the actual Ubuntu 10.10  once it starts installing (which will also be turned into ext4 or whatever later on)
[*]In addition, I have kept the original EFI & OSX partitions, and they seem to be as they should.
[/LIST]

**Hardware**
Fully upgraded MacBook Air 3,2


**fdisk -l**
```

/dev/sda1 GPT
/dev/sda2 HFS/ HFS+
/dev/sda3 W95 FAT32 LBA
/dev/sda4 W95 FAT32 LBA

```

**More Q's**

*Am I special?*
From what I've read in this thread (yeah, read every post and all in Wiki) there seems only to be one single person that has had the same or similar problem as me. C'mon now, don't be shy - if you also have a rare & lame Air at home that has the same sickness as mine, please share. :)

*What buntu?*
What I also lack is clear info on exactly which Ubuntu you guys have succeeded with installing. Would everyone that has succeeded with the install be willing to elaborate on this? I am fiddling with normal install cd here, 10.10 (64) copied over to internal SSD partition. What was your mojo?

**Does filesystem matter?**
When I dd the LiveCD from my USB stick to the target partition I want to install Ubuntu from, does it matter what filesystem that partition has? (Yeah, I don't know exactly what dd clones..)

I'd happily buy anyone that comes with info that I can use to solve this a cup of coffee granted he/she takes paypal.

P.S: I edited the [Wiki page]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick") explaining that the "boot with usb"-info isn't really working out at all for an Air.

P.S again: Does the ethernet adapter for the Air work in Ubuntu 10.10 out of the box? Anyone had any luck with it?

**Installs that worked for somebody**
This is based on replies to my call out to all of those that actually managed to install Ubuntu on an Air 3,1 or 3,2:

Number of people / Ubuntu version / From what it was installed
1 x Alternate Cd Ubuntu 10.10 (x64), Superdrive.
1 x Normal Cd, Susperdrive
1 x Alternate cd 10.10 (x64), from usb stick dd'd to a partition

**Edit - Problem resolved**
My above problem with the installer not finding the filesystem was resolved by itself when I tried using the 10.10 (64) alterantive install cd. This is how I did it without using a cd-rom:

1) Partioned the HD into something that should result into 4 partitions: a) One that holds the untouched OSX crap that came with the Air b) One very huge where I would want to install Ubuntu c) One small where I will put all the installation files for Ubuntu, cloned of a USB live cd d) a swap partition, that's double the size of my RAM.

2) I made a start disk from within Ubuntu (10.10) using 10.10 (64) alterantive install cd iso.

3) I then, from inside of OSX, dd'd it over to a partition (c, in #1 above) which I booted with rEFIt. 

4) Installation launched and completed successfully, but only while I also had the live USB start disk attached as well, due to the live cd installation from the partition looking for a cd-rom device. 

After the install I had no graphical issues whatsoever, but graphics ran on low 800x600 due to Nvidia drivers not being installed during the install process since I had no ethernet or wifi connection. Wireless card didn't seem to be detected either. Sound in earphones worked, but not from speakers. I hooked the ethernet adapter to get out on the net. It installed drivers for nvidia and for the wifi. Wifi and graphics both worked directly after, and obviousley so did the ethernet adapter out of the box.

---

### Post by sanicki on 2010-12-05
> **eyerouge said:**
> Would everyone that has succeeded with the install be willing to elaborate on this?
I punted on moving the usb image to the ssd. It booted the installer but I never got through an install successfully. Superdrive was painless. I used the Alternate CD (10.10, x64.) There are some issues with the standard installer that are addressed in an earlier post, but the Alternate CD was the path of least resistance.

Ethernet dongle worked out of the box for me...and I believe it's necessary when using the Alternate CD since there isn't an option to install the 3rd party drivers for wireless during install.

Everything else in the wiki worked for me except for audio. I get sound through the headphones, but not through the built-ins or Bluetooth. Not sure if that's specific to this method or common, but the wiki says sound should work. I have seen conflicting posts about it.

EDIT: FYI, I am single-booting Ubuntu. Dual-booters' results may vary.

---

### Post by dentifrice on 2010-12-06
> **dentifrice said:**
> Could you share your grub.cfg entry, and the command used to generate the grub.efi image?

Unfortunately, I couldn't even get the framebuffer console to work. Upon booting, I get *ROM image is present* and then a black screen. Adding *debug=video* adds the following to the black screen but results in a freeze nonetheless: *video/efi_gop.c:357: GOP: Success*


EFI booting is explained in Brian Tarricone’s MacBookAir3,1 Gentoo install report : [http://spurint.org/misc/installing-gentoo-on-a-macbookair31/](http://spurint.org/misc/installing-gentoo-on-a-macbookair31/)

Basically, it requires a patch to force EFI booting in physical mode rather than virtual mode.

It's a very interesting read for anyone tweaking his/her MBA3,*

---

### Post by Dreamsorcerer on 2010-12-06
> **sanicki said:**
> If you ever make it to Sedona, AZ, I owe you a beer. Why doesn't the wiki say "You just spent an insane amount of money on Apple hardware, save yourself some pain and spring for the Superdrive and ethernet dongle" then direct folks to the Alternate CD? Would have saved me much aggravation. Thanks.

I installed with the main liveCD, following the steps on the wiki (I edited down to the simplest steps in the process). I used the superdrive, but was unsure if other installation methods worked. I've added a note about the Superdrive now.

---

### Post by eyerouge on 2010-12-06
**General question: Encrypted /home & Kernel updates**

1) Do you guys have the encrypted /home feature turned on or off when installing on the Air? Does it affect the flash disk somehow or anything else specific to the Air?

2) Is it safe to do casual kernel updates, suggested by Ubuntu? Or would it wreck the install?
 

**Hard & software**
I use a fully pimped 3,2 Air with Ubuntu 10.10 (#64) on it.


**My unsolved post install problems**
Are only two right now: Choppy/freezing trackpad and 400 MB missing RAM.

[I]

1. Choppy trackpad movement[/I]

Every now and then, pretty often actually, the mouse movements freeze for a short moment while it is (was) in motion. This always happens and can easily be reproduced by simply dragging your fingers back and forth repeatedly fast on the trackpad, from the left to the right, or any other directions for that matter.

a) Anyone knows the fix? 

b) Or have same problems?

c) What is this related to?

d) Is there some driver that would support basic functionality of the trackpad except for the Mactel packages that supposedly supports multitouch? 

e) In what ways is the multitouch supported in Ubuntu? What can I do with the trackpad for that to matter?



*2. Missing RAM*
I have 4GB in this machine. Yet, Ubuntu system info only detects 3,6GB. Where are the rest, and what causes this? (Is it eaten by the graphics card)


**My solved post install problems:**

[LIST]
[*]Sound comes from earphones, but not from speakers: Solved in wiki ("alsamixer" in terminal)
[*]Low resolution (Solved: Nvidia drivers from internet)
[*]Wifi card not detected (Solved with Ethernet adapter: Got drivers from inet)ne
[*]Crazy fan on steroids: Solved as described in [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)
[*]Screen brightness resetting to max after reboot when AC adapter was plugged in: Was a Ubuntu setting, not related to air. 
[/LIST]

---

### Post by javipas on 2010-12-07
I've read with great interest all the messages in this thread. I've just bought a MacBook Air 13'', base model, but with 4 Gbytes of RAM. 

I've tried to install Ubuntu as mentioned here: I have created the LiveUSB **both through Ubuntu and through Unetbootin**, and I've created a 2 Gbytes MSDOS partition on the MBA harddisk on which I've dd'ed that LiveUSB:

```
sudo dd if=/dev/disk1s1 of=/dev/disk0s3 bs=1m
```

The process finishes well, and when I reboot rEFIt recognizes a new Linux partition with a penguin icon. I try to boot from there, but **I always get the "Boot error" message**, it goes no further than that. 

Is there some special option to create the LiveUSB from the ISO image downloaded from the Ubuntu website? Or **some special option to dd or rEFIt **that I haven't considered?

Thanks!

---

### Post by eyerouge on 2010-12-07
> **javipas said:**
> Is there some special option to create the LiveUSB from the ISO image downloaded from the Ubuntu website? Or **some special option to dd or rEFIt **that I haven't considered?
Thanks!

Creating the bootable USB from Ubuntu 10.10 works fine, that is not the problem. I'd advise you to use the alternative installation ISO. That was the only thing that worked for me using the dd/usb/partition method. All else failed for one or another reason.

Btw, please feel free to contact me via mail (spam at.thingie eyerouge dot.thingie com) with your chat info if you want to discuss different setups: I am also in the middle of (re)installing my Ubuntu on the Air again and would love it if we could keep in touch on our progress and shared experiences. I have written about my adventures in previous recent threads but need to reinstall it again.

---

### Post by dentifrice on 2010-12-07
After successfully testing Ubuntu Maverick on the MBA3,1, I went on to install Debian GNU/Linux (as it is my system of choice). It's not *quite* as easy as installing Ubuntu, though efforts are being made by the kernel team to merge patches pretty quickly before the next stable release.

If anyone reading this thread is interested in getting Debian to work on the MacBookAir, or if people feel like proofreading/shading some light on the stuff I haven't got to work yet, feedback is really appreciated. Enough said, here it is: [http://dentifrice.poivron.org/laptops/macbookair3,1/](http://dentifrice.poivron.org/laptops/macbookair3,1/)

PS: the document gathers a number of links for reference. So I hope it can be useful to Ubuntu users too.

---

### Post by javipas on 2010-12-07
> **dentifrice said:**
> 

If anyone reading this thread is interested in getting Debian to work on the MacBookAir, or if people feel like proofreading/shading some light on the stuff I haven't got to work yet, feedback is really appreciated. Enough said, here it is: [http://dentifrice.poivron.org/laptops/macbookair3,1/](http://dentifrice.poivron.org/laptops/macbookair3,1/)

PS: the document gathers a number of links for reference. So I hope it can be useful to Ubuntu users too.

Uauh, that's what I'd call a fantastic step by step tutorial. Congrats, good work ;)

I'm still dealing with my Ubuntu install, but it's good to see other distros have good suport & install guides. Cheers :p

---

### Post by javipas on 2010-12-07
> **eyerouge said:**
> Creating the bootable USB from Ubuntu 10.10 works fine, that is not the problem. I'd advise you to use the alternative installation ISO. That was the only thing that worked for me using the dd/usb/partition method. All else failed for one or another reason.

Btw, please feel free to contact me via mail (spam at.thingie eyerouge dot.thingie com) with your chat info if you want to discuss different setups: I am also in the middle of (re)installing my Ubuntu on the Air again and would love it if we could keep in touch on our progress and shared experiences. I have written about my adventures in previous recent threads but need to reinstall it again.

Didn't think about that option, but I'll try that, thanks for your suggestion. I'll let you know what happens :)

---

### Post by sanicki on 2010-12-07
> **eyerouge said:**
> 
**My solved post install problems:**
[LIST]
[*]Sound comes from earphones, but not from speakers: Solved in wiki (alsa in terminal)
[/LIST]

alsamixer! overlooked it, thanks.

---

### Post by javipas on 2010-12-07
No luck again. I've downloaded the alternate ISO image (64 bits), created the USB from Ubuntu 10.10, dd'ed the LiveUSB to one 2,5 Gbytes partition on Mac OS X, and tried to boot from that partition using rEFIt.

The same message that had appeared returns: "Boot error".

Can't go further :( Ideas, please?

---

### Post by eyerouge on 2010-12-08
[SIZE="4"]javipas:[/SIZE]
[LIST=1]
[*]Did you download the Ubuntu 10.10 alternative installer cd?
[*]Did you try booting it on any other computer after you put it onto the USB? You must know that the USB stick boots correctly before proceeding.
[*]Did you re-sync partition tables in rEFIt after dd:ing it to the small partition? (Power down and up again may help before and after resync.)
[*]What icon does rEFIt show in its menu, for the HD-partition where you put the dd of the USB? Is it a penguin or win icon? (Mine shows Pingo)
[*]Tried to uninstall/reinstall rEFIt?
[*]Are you sure the HD partition where you put the dd on was completly wiped out? Maybe removing it and re-creating a new one would help. (Can be done from within OSX)
[/LIST]

---

### Post by dentifrice on 2010-12-08
There's an EFI firmware update for the MBAs. Who knows, with a lot of luck, it may fix a bug or two? Source: [http://www.macrumors.com/2010/12/08/apple-addresses-macbook-air-issues-with-firmware-update/](http://www.macrumors.com/2010/12/08/apple-addresses-macbook-air-issues-with-firmware-update/)

---

### Post by javipas on 2010-12-09
Sorry for the delay :(

I have finally succeeded!! Instead of re-trying the USB-dd method I was able to connect a external DVD reader I had (I almost forgot I had this), and everything went perfectly fine after following the next steps:

[INDENT]1. Follow the famous tutorial on [Lifehacker]("http://www.lifehacker.com.au/2010/05/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/").

2. As I had no Internet connection on the MBA and no USB to Ethernet adapter, I just followed this other fantastic tutorial with instructions to install and [enable STA drivers with no Internet connection]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA - No Internet access")

3. Follow the post-install guide on the [MacBookAir3-2Meerkat tutorial]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") [/INDENT]

Everything running perfect now, I'm really happy to have a working MBA 3,2 with Mac OS X, Windows 7 and Ubuntu 10.10 with a nice triple boot. Let's see which one of those dissapears first :D

Thank you for all your support!

---

### Post by dentifrice on 2010-12-10
> **dentifrice said:**
> There's an EFI firmware update for the MBAs. Who knows, with a lot of luck, it may fix a bug or two? Source: [http://www.macrumors.com/2010/12/08/apple-addresses-macbook-air-issues-with-firmware-update/](http://www.macrumors.com/2010/12/08/apple-addresses-macbook-air-issues-with-firmware-update/)

Has anyone using rEFIt managed to carry the EFI firmware upgrade? I can't.

My guess is that it is related to the bootup delay problem that appears when booting in MacOS X after doing a GNU/Linux install in BIOS emulation mode (meaning installing grub2).

I installed GNU/Linux twice on my MBA (Ubuntu and then Debian), and had the same problem both times. Before the install, rEFIt appears within a few seconds after pressing the power button. After the install, nothing changes, rEFIt shows up super fast, until I go into MacOS X again.

From that moment onwards, I get a gray screen for 15-30 seconds (I think the delay varies) before rEFIt appears. I tried to carry the EFI firmware upgrade earlier today, but it doesn't work: the computer restarts and instead of showing the gray progress bar, it goes into the long delay and then shows rEFIt.

I guess it has to do with the hybrid GPT/MBR partitionning, which seems to confuse MacOS X, for the OS X partition does not show anymore in the list of bootable media in the MacOS X "bootup" config panel (or whatever it is called in english).

Does anyone understand what these issues are about?

---

### Post by dentifrice on 2010-12-10
I still can't get the backlight keys to work under X. I have the properly patched *mbp_nvidia_bl* kernel driver, and when I modprobe it I get:

```
mbp_nvidia_bl: MacBookAir 3,1 detected
```But here's what I read in */var/log/Xorg.0.log*:

```
(II) Dec 10 21:53:12 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Dec 10 21:53:12 NVIDIA(0):     enough to receive ACPI hotkey events.
(WW) Dec 10 21:53:12 NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
(WW) Dec 10 21:53:12 NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
(WW) Dec 10 21:53:12 NVIDIA(0):     respond to ACPI brightness change hotkey events.
```Can someone with backlight working share the output of *find /proc/acpi/video* or anyone knowledgable in nvidia driver matters tell me what softare component should be responsable for creating the missing file(s)?

---

### Post by eyerouge on 2010-12-12
There are no "backlit" keys on the 3,1 and 3,2, if you with "backlight keys" mean any/all keys on the keyboard that [can glow]("http://www.google.se/#hl=sv&source=hp&biw=1280&bih=637&q=backlight+keys&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=90ad869e5c254bcf").

---

### Post by dentifrice on 2010-12-12
> **eyerouge said:**
> There are no "backlit" keys on the 3,1 and 3,2, if you with "backlight keys" mean any/all keys on the keyboard that [can glow]("http://www.google.se/#hl=sv&source=hp&biw=1280&bih=637&q=backlight+keys&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=90ad869e5c254bcf").

No, I'm talking about the F1/F2 keys that adjust the screen backlight/brightness (see log extract).

---

### Post by npgall on 2010-12-12
> **dentifrice said:**
> Has anyone using rEFIt managed to carry the EFI firmware upgrade? I can't.

@dentifrice
I have the same issue. On the internal hard disk I only have ubuntu. I don't have rEFIt installed. I have OS X on an external usb disk. Even when I set OS X on the external disk to boot by default I don't get the grey progress bar, and OS X just reboots and still shows that firmware update as available to install.

I'll be quite annoyed if apple have somehow locked firmware updates to installing only when OS X is the primary OS on the internal disk. Any advice there would be appreciated.
[U]
[/U]> **sanicki said:**
> Why doesn't the wiki say "You just spent an insane amount of money  on Apple hardware, save yourself some pain and spring for the  Superdrive

@sanicki
Actually it's not strictly true that you need the superdrive, I installed just fine using an LG drive, EFI seemed to support it without probs: [http://www.lg.com/us/computer-products/optical-media/LG-external-dvd-burner-GP08LU10.jsp](http://www.lg.com/us/computer-products/optical-media/LG-external-dvd-burner-GP08LU10.jsp)

__

---

### Post by juustomuna on 2010-12-12
No screeen backlight control here either. It worked with 32-bit, but I had to install 64-bit ubuntu because I have 4 GB of RAM.

Otherwise, all I can say is great work! This machine was released a couple of months ago. I ordered it right away when it was released. I would have never even imagined that I would get Ubuntu running on it before next summer, but surprise surprise -- it is working perfectly already! If this works well during the next couple of months, I'll probably wipe out OS X completely and run ubuntu only, like I did with my old macbook air. 

I remember those days when you had to spend an all-nighter recompiling and patching kernels and tweaking XF86Config just to get your PC running normally.

---

### Post by dentifrice on 2010-12-13
> **juustomuna said:**
> No screeen backlight control here either. It worked with 32-bit, but I had to install 64-bit ubuntu because I have 4 GB of RAM.


Do you get the same error message as me in the Xorg logs?

When I installed Ubuntu (the amd64 version), screen backlight adjustement did work, following instructions on the wiki. So I guess it's not architecture related.

> **juustomuna said:**
> 
I remember those days when you had to spend an all-nighter recompiling and patching kernels and tweaking XF86Config just to get your PC running normally.

Well, it is still the case for some of us ;)

---

### Post by eyerouge on 2010-12-15
[B]
screen brightness not working[/B]
This is really ironic: Up until today or yesterday my F1/F2 worked flawlessly and as expected to control the screen brightness with. All I ever did was to follow the [post-install in the wiki]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat").  (I'm running 10.10 #64 on the 3,2).

Today it just stopped. The only thing I know I've done here is to hook the Air to a projector at work, where it all ran perfectly in nvidias clone view, using "nvidia-settings"...but I don't really know if that could be relevant somehow, it seems like a longshot and totally unrelated.

Here's the dump from my file that dentifrice asks for. As you can see I get the same error as (s)he:

```
[    11.937] (II) NVIDIA(0): Initialized GPU GART.
[    11.948] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[    11.948] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[    11.949] (WW) NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
[    11.949] (WW) NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
[    11.949] (WW) NVIDIA(0):     respond to ACPI brightness change hotkey events.
[    11.952] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
```

My screen is stuck on max brightness, and it is really a problem since it eats battery and also hurts my eyes whenever I'm in a somewhat darker room.

Edit: Fixed the problem now! In my case it was because my /etc/X11/xorg.conf had been reset by Ubuntu or the nvidia-driver(? when I saved my settings in it?) In any case the xorg.conf was totally free from the post install stuff I did to it in the Wiki link above in this post. I re-did the few mods to it as described there, and it all works now as before. 

On a totally other topic:

**mouse doesnt move while typing**
Am I the only one that use a mouse connected to the Air? If not, could you guys please try to move the mouse cursor while at the same time you are QWERTY key on the keyboard? 

What happens on my Air is that the mouse cursor stops moving as soon as I press a key. When key is released again, it continues to move, but while key is pressed it's frozen.[B]

remap the keys?[/B]
How can I remap the FN keys with the ctrl / alt / cmd keys? "XEV" doesnt even show what keycode it has, it doesnt even register that Fn is pressed.... hard to remap it then, not to mention I don't know what the best method for the remapping would be even if the Fn keys code would be known.

I would also like to invetr how F12 currently works: Now if I press F12 it works as the EJECT button. I don't care about such a button, especially on my cdrom-less Air. I would want F12 to be simply original F12 when I press it. If I press Fn + F12 THEN it would EJECT. Currenty it's the other way around - I have to press Fn + F12 to make it work as normal F12. 
[B]
the missing keys on the Air?[/B]  
Fn + arrow up/down seems to work as Pg Up and Pg Down. Fn + backspace seems to be DEL. But how do I press:

PrntScr? Home? End? INS?  ...on the air?

---

### Post by Dreamsorcerer on 2010-12-16
> **eyerouge said:**
> [B]
the missing keys on the Air?[/B]  
Fn + arrow up/down seems to work as Pg Up and Pg Down. Fn + backspace seems to be DEL. But how do I press:

PrntScr? Home? End? INS?  ...on the air?

Didn't know about the Pg Up/Down keys, thanks for that. Based on that information, it would seem that Fn + left/right also works for Home/End respectively. Only key missing that bothers me now is the PrntScr/SysRq key. I just had to use the command line to get a screenshot :P Does anyone know how you would normally get a screenshot on OS X?

---

### Post by _mario_ on 2010-12-16
> **eyerouge said:**
> 
**remap the keys?**
How can I remap the FN keys with the ctrl / alt / cmd keys? "XEV" doesnt even show what keycode it has, it doesnt even register that Fn is pressed.... hard to remap it then, not to mention I don't know what the best method for the remapping would be even if the Fn keys code would be known.

you can't simply change the behaviour of FN. although Apple's keyboards (unlike other keyboards) report whether the FN key is pressed to software, the linux kernel transparently maps combinations with FN to other keycodes. hence, no user-land application, such as the X server ever notices, that you pressed FN.

> **eyerouge said:**
> 
**the missing keys on the Air?**  
Fn + arrow up/down seems to work as Pg Up and Pg Down. Fn + backspace seems to be DEL. But how do I press:

PrntScr? Home? End? INS?  ...on the air?

the linux kernel translates like this (actually the module hid_apple):
```

FN+Backspace => Delete
FN+Return    => Insert
FN+Up        => Page Up
FN+Down      => Page Down
FN+Left      => Home
FN+Right     => End

```
just like Apple's drivers for windows.

ciao,
Mario

---

### Post by quickk on 2010-12-17
Hi everyone, 

   I have the first version of the macbook air (1,1), and have installed kubuntu 10.10 32 bit using an external usb dvd drive + refit.   Installation works without any problems.  So contrary to what is said in many tutorials, the macbook air can use other usb dvd drives (at least the 1,1 can).  I did spend countless hours trying to get the installation to proceed with a bootable usb key, but to no avail (I just can't get the mba to boot from the usb key).  
 
Out of the box, most things work.  I installed pommed which seemed to get rid of most nagging issues.  

The remaining problems are:

0. Seems like I can't use the toolbar buttons to insert code, quotes, etc... sorry for the long pastings below.

1. Fan is blowing full blast all the time.  I've installed macfanctld, and configured it properly (I think), but it does not seem to do anything.  I've set it up so that it will keep the fan at 2000 rpm for temperatures below 60C, but no luck.

Here is the output of "sudo macfanctld -f" with the "1" verbosity setting:

Using parameters:
        temp_avg_floor: 60
        temp_avg_ceiling: 80
        temp_TC0P_floor: 60
        temp_TC0P_ceiling: 80
        temp_TG0P_floor: 60
        temp_TG0P_ceiling: 80
        fan_min: 2000
        exclude: temp1_input temp2_input temp3_input temp4_input temp5_input temp8_input temp9_input temp10_input temp11_input temp12_input temp13_input temp14_input temp15_input 
        log_level: 1
Found 1 fan.
Found 15 sensors:
         1: TB0T - Battery TS_MAX Temp    ***EXCLUDED***
         2: TB1S - ?    ***EXCLUDED***
         3: TB1T - Battery TS1 Temp    ***EXCLUDED***
         4: TB2S - ?    ***EXCLUDED***
         5: TB2T - Battery TS2 Temp    ***EXCLUDED***
         6: TC0D - CPU 0 Die Temp 
         7: TC0P - CPU 0 Proximity Temp 
         8: TCFP - ?    ***EXCLUDED***
         9: TTF0 - ?    ***EXCLUDED***
        10: TW0P - ?    ***EXCLUDED***
        11: Th0H - ?    ***EXCLUDED***
        12: Tp0P - ?    ***EXCLUDED***
        13: TpFP - ?    ***EXCLUDED***
        14: Ts0P - Palm Rest Temp    ***EXCLUDED***
        15: Ts0S - ?    ***EXCLUDED***
Speed: 2000,  AVG: 55.8C,  TC0P: 50.8C
Speed: 2000,  AVG: 55.2C,  TC0P: 50.8C
...

2. Backlighting cannot be changed.  This doesn't bug me too much.  

3. It's kind of slow...

Any advice or comments for problem 1 especially would be very welcome.

Thanks!

---

### Post by dentifrice on 2010-12-17
> **eyerouge said:**
> [B]
screen brightness not working[/B]

Edit: Fixed the problem now! In my case it was because my /etc/X11/xorg.conf had been reset by Ubuntu or the nvidia-driver(? when I saved my settings in it?) In any case the xorg.conf was totally free from the post install stuff I did to it in the Wiki link above in this post. I re-did the few mods to it as described there, and it all works now as before. 


Wow, that's interesting. So all you did was adding ```
Option "RegistryDwords" "EnableBrightessControl=1"
``` to */etc/X11/xorg.conf* (considering you also appended ```
acpi_backlight=vendor
``` to the kernel options) ?!

So, this means the 'nvidia' X driver is actually responsable for creating the necessary files under */proc/acpi/video* ?! Problem is, I don't know which file(s)! I have exact the same stuff, but it NEVER worked, and I get the output you pasted in your post. **Could you be so kind as to share the ouput of *tree /proc/acpi/video* ?** Thanks a bunch...

---

### Post by Dreamsorcerer on 2010-12-17
> **eyerouge said:**
> 
**mouse doesnt move while typing**
Am I the only one that use a mouse connected to the Air? If not, could you guys please try to move the mouse cursor while at the same time you are QWERTY key on the keyboard? 

What happens on my Air is that the mouse cursor stops moving as soon as I press a key. When key is released again, it continues to move, but while key is pressed it's frozen.

Just checked this, and no problems for me. Tested with the trackpad and the Magic Mouse.

---

### Post by akbardotinfo on 2010-12-17
.

---

### Post by akbardotinfo on 2010-12-17
Great Tutorial on this thread!
Thank you very much, now I'm working with ubuntuk on mba 3,2 :)
No probs found when installing ubuntu on new efi firmware also, no long delay when loading grub from refit.

btw how do I enable right click on the default trackpad ?

Thank you :)

---

### Post by rmaus on 2010-12-17
**Thanks to all in this thread who made these two guides possible:**

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
and
[https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

My brand new Macbook Air 3,2 runs OSX and 10.10 flawlessly; I do have a superdrive.  I would suggest some slight modifications to the first install guide, here were the exact steps that I took from a fresh OSX install:

**In OSX:**
1.  Install rEFIt, make sure to run this command to get rEFIt to actually start up: ```
sudo /efi/refit/enable.sh
```

2.  Use Disk Utility to create a 33 GB 'free space' partition. (why 33GB? see step 6)

**In Ubuntu 10.10 LiveCD / Ubiquity:**
(Connect your superdrive, put in the Ubuntu 10.10 install disc, hold 'c' at startup to boot to the CD drive)

3.  Hit 'enter' when the purple screen (with the two icons at the bottom) shows up to bring up the Ubuntu install menu.  Select your language, and then hit 'F6' to enable the 'nomodeset' boot option (this fixes a graphical issue that would prevent the visual installer from showing up).

4.  I used the direct 'Install Ubuntu' option, rather than the "Try Ubuntu Without Installing" option.  If you use the "Try Ubuntu" option, you may get some random errors when trying to launch Ubiquity to install Ubuntu.

5.  Once Ubiquity shows up, answer the questions (make sure to select the option to "Install this third party software") and navigate to the screen where it asks you how you want to partition the disk space.  Choose the 'advanced' option.

6.  In the partition screen, you should see the 33GB of free space you made earlier.  I allocated as follows: sda3=10GB mounted to '/', sda4=15GB mounted to '/home', and the rest is 8GB of swap (my RAM * 2).  There are lots of guides on how to use this partitioning tool, so I won't go into that here.

7.  At the bottom of the partition screen, set the boot loader (GRUB) to be installed to 'sda3' (or wherever your '/' is mounted to).  Do not leave this field as the default.

8.  Start the install.  Once it's completed, make sure to use rEFIt to sync your MGR and GPT.

9.  At this point, you can pretty much follow the directions from the MacBookAir3-2/Meerkat community wiki linked above (start at approximately the second-to-last paragraph of the 'Installation' section).

Cheers,
-REM

---

### Post by yanik on 2010-12-18
Can someone help me please, don't know what I'm doing wrong here, but it doesn't work.

I used another ubuntu pc to create the usb key and I can boot the USB key on the PC.  On my MBA I installed refit, and wether I boot the USB ley before refit or after refit, I get;

```
syslinux bla bla bla
no default or ui configuration directive found

```
I trie dd'ing the usb key to a small 2G partition, and when I choose to boot from that partition I get the same message.

Any hints?

---

### Post by akbardotinfo on 2010-12-19
anybody realize that wireless power on ubuntu not as strong as on leopard ?

and the wireless device known as eth0 instead of wlan0 ?
I tried to increase with command iwpriv eth0 power_profile 0, still dont work.

anybody have workaround this issue ?

Thank you

---

### Post by sandyxb on 2010-12-20
I installed via the given steps:
1- repartition under MAC OS
2- installed refit
3- dd'ed unetboot ubunutu 10.10 to a partition /dev/sda3, swap /dev/sda4,, root /dev/sda5
4- unmounted CD, fixed install.py, installed sucessfully
5- grub-install --recheck -root-directoru=XXX /dev/sda5 --force

I get another linux icon under refit, but when I boot it, I end up in the same unetboot menu. Never does it actually boot the installed ubuntu. What did I do wrong? Thanks,

---

### Post by dentifrice on 2010-12-20
> **akbardotinfo said:**
> anybody realize that wireless power on ubuntu not as strong as on leopard ?
and the wireless device known as eth0 instead of wlan0 ?
I tried to increase with command iwpriv eth0 power_profile 0, still dont work.


Have you tried the open source driver ? It's in the 2.6.37 kernel (soon to be released as stable).

---

### Post by dentifrice on 2010-12-20
> **akbardotinfo said:**
> 
No probs found when installing ubuntu on new efi firmware also, no long delay when loading grub from refit.


Can you be more precise?

Do you mean you could carry the firmware upgrade after installing Ubuntu, or did you upgrade the firmware, and then install Ubuntu?

I had the very same issue (long delay before rEFIt shows up) after installing Ubuntu on a MacBook4,1, with GRUB located in a BIOS Boot partition. So I suspect this is a possible cause, even though this kind of partition is claimed to be recognized as of rEFIt 0.14.

---

### Post by pbhedlund on 2010-12-20
> **sandyxb said:**
> I installed via the given steps:
1- repartition under MAC OS
2- installed refit
3- dd'ed unetboot ubunutu 10.10 to a partition /dev/sda3, swap /dev/sda4,, root /dev/sda5
4- unmounted CD, fixed install.py, installed sucessfully
5- grub-install --recheck -root-directoru=XXX /dev/sda5 --force

I get another linux icon under refit, but when I boot it, I end up in the same unetboot menu. Never does it actually boot the installed ubuntu. What did I do wrong? Thanks,

There should be an item in the unetbootin menu about booting from the first harddrive. This should take you to your new install. I then erased but not deleted the unetbootin partition from within Ubuntu and reinstalled grub again. This resulted in a correct grub boot menu. I still have tux x 2 in the rEFIt menu, but that does not bother me as much.

---

### Post by pbhedlund on 2010-12-20
> **pbhedlund said:**
> There should be an item in the unetbootin menu about booting from the first harddrive. This should take you to your new install. I then erased but not deleted the unetbootin partition from within Ubuntu and reinstalled grub again. This resulted in a correct grub boot menu. I still have tux x 2 in the rEFIt menu, but that does not bother me as much.

It's been a while. I seem to remember that you have to edit the command line for the harddrive boot option to actually point to the partition where you installed ubuntu.

---

### Post by akbardotinfo on 2010-12-21
> **dentifrice said:**
> Can you be more precise?

Do you mean you could carry the firmware upgrade after installing Ubuntu, or did you upgrade the firmware, and then install Ubuntu?

I had the very same issue (long delay before rEFIt shows up) after installing Ubuntu on a MacBook4,1, with GRUB located in a BIOS Boot partition. So I suspect this is a possible cause, even though this kind of partition is claimed to be recognized as of rEFIt 0.14.

I upgrade the EFI first after that install ubuntu :)

---

### Post by pwright on 2010-12-21
Macbook Air 3,2

When I used the "Try Ubuntu..." install I was able to get wireless access out of the box.  I just had to enable the broadcom driver.  Since I had wireless I was able to do the install with all updates.  I was also able to install the nvidia driver.

But, the problem I'm having is post-install.  When I get to the GRUB Bootloader and select the default Ubuntu list item it loads a black screen with a little bit of text and then rapidly the screen goes blank.  The text that appears only displays for an instant and I was able to catch the word "nouveau."   Because of that I feel confident this is a nvidia driver issue.

When I edit the GRUB boot command and append nomodeset I am able to get into the system via command line only.  I no longer have network access since the drivers were most likely overwritten when I did the full install.  When I run "startx" I get a failure related to the nivida driver not existing.

Anyone else have this particular issue with the blank screen after a "successful" install?  I've gone though several blogs and forums related to graphics issues, but they seem to assume that I would have either a "fuzzy" screen or low-graphics.  I can not load the UI at all.

Any help is appreciated!

---

### Post by Dreamsorcerer on 2010-12-21
> **eyerouge said:**
> 
PrntScr?

Pretty obvious, but only just thought of it myself, but if you go to System > Preferences > Keyboard Shortcuts, you can find the "Take a Screenshot" entry and set it to another key, I just set mine to the eject key (after disabling the eject shortcut), the eject key is hardly useful on the Air anyway (you can run 'eject' from the command line in the rare case you need it for the Superdrive). :)

---

### Post by pwright on 2010-12-21
> **pwright said:**
> Macbook Air 3,2

When I used the "Try Ubuntu..." install I was able to get wireless access out of the box.  I just had to enable the broadcom driver.  Since I had wireless I was able to do the install with all updates.  I was also able to install the nvidia driver.

But, the problem I'm having is post-install.  When I get to the GRUB Bootloader and select the default Ubuntu list item it loads a black screen with a little bit of text and then rapidly the screen goes blank.  The text that appears only displays for an instant and I was able to catch the word "nouveau."   Because of that I feel confident this is a nvidia driver issue.

When I edit the GRUB boot command and append nomodeset I am able to get into the system via command line only.  I no longer have network access since the drivers were most likely overwritten when I did the full install.  When I run "startx" I get a failure related to the nivida driver not existing.

Anyone else have this particular issue with the blank screen after a "successful" install?  I've gone though several blogs and forums related to graphics issues, but they seem to assume that I would have either a "fuzzy" screen or low-graphics.  I can not load the UI at all.

Any help is appreciated!

Update on how I got around this.

On the GRUB screen edit the Ubuntu recovery mode line.  Append nomodeset to linux boot line.  When the recovery options are displayed select the graphics fail safe option.  I was able to log in and install the nvidia drivers.  Reboot.

---

### Post by gschwind on 2010-12-22
Hello,

I will just add a comment about slow boot of MacBookAir 3,1. I experienced that plug usb device before turn on the computer greatly slow the boot time.

Best regards.

---

### Post by eyerouge on 2010-12-25
[SIZE="5"]@dentifrice:
[/SIZE]
> **dentifrice said:**
> Wow, that's interesting. So all you did was adding ```
Option "RegistryDwords" "EnableBrightessControl=1"
``` to */etc/X11/xorg.conf* (considering you also appended ```
acpi_backlight=vendor
``` to the kernel options) ?!
All I did was to follow the instructions in [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat) that cover the editing of the xorg.conf file. (I have of course followed any and all instructions in there previous to that as well.)

I have included a copy of my xorg.conf for your viewing pleasure. Please notice: All the crap in my xorg.conf is not needed. Half of it is there due to the mouse/pad and rest is a result of me using external projector(s) and monitor on my work, hence there's plenty you can shave off that is totally unrelated to yout problems.




> **dentifrice said:**
> So, this means the 'nvidia' X driver is actually responsable for creating the necessary files under */proc/acpi/video* ?! Problem is, I don't know which file(s)! I have exact the same stuff, but it NEVER worked, and I get the output you pasted in your post. **Could you be so kind as to share the ouput of *tree /proc/acpi/video* ?** Thanks a bunch...

I don't have a clue what it means or what the nvidia drivers create since I'm really not into the technical part of things and just love Linux (preferably without us *having* to constantly hack it to get it working, but always with the* ability *to do so when we want to) and wouldn't ever use what is an inferior, for my needs as well as my wallets, OS X.

Here is what you requested:

```
snowdrop@ubuntu:~$ tree /proc/acpi/video
/proc/acpi/video
`-- IGPU
    |-- DOS
    |-- info
    |-- LCD1
    |   |-- brightness
    |   |-- EDID
    |   |-- info
    |   `-- state
    |-- POST
    |-- POST_info
    `-- ROM

2 directories, 9 files

```

---

### Post by eyerouge on 2010-12-25
[SIZE="5"]@Dreamsorcerer[/SIZE]
> **Dreamsorcerer said:**
> Pretty obvious, but only just thought of it myself, but if you go to System > Preferences > Keyboard Shortcuts, you can find the "Take a Screenshot" entry and set it to another key, I just set mine to the eject key (after disabling the eject shortcut), the eject key is hardly useful on the Air anyway (you can run 'eject' from the command line in the rare case you need it for the Superdrive). :)

I think this is a simple missunderstanding: I didn't ask how to take a screesnhot without using the PrntScrn button. I asked how to *press that button* on my MacBook Air. 

So far we have figured that *Fn + somekey* produces Pg Up/Pg Down/Home/End etc. (Notice: Fn + Enter does not produce INS, at least not when using Ubuntu 10.10 #64 on the Air 3,2 using a *Swedish* keyboard.) 

Question remains: What combo needs to be pressed to make Ubuntu believe that we have pressed the PrtScrn key?

---

### Post by eyerouge on 2010-12-25
[SIZE="5"]@akbardotinfo[/SIZE]
> **akbardotinfo said:**
> anybody realize that wireless power on ubuntu not as strong as on leopard ?
/../
anybody have workaround this issue ?

How do you know that? 

Since signal strength could very well be a) measured differently and also b) displayed differently in OSX and in 10.10 there is no way of telling for sure by just *looking* at e.g. the signal icon in the system tray. 

Only proper method to know this for sure, unless you're a linux and osx guru and have some in-depth knowledge about what happens behind the scenes, is to actually try this out in a series of experiments on a location, where you slowly move away from the modem/signal source until it disconnects you for being out of reach (notice it might dc you way before that for a zillion reasons. e.g. heavy torrent usage or whatnot)

Edit: I'm maybe fast in my conclusions here that you with power mean signal strength.... :P

---

### Post by dentifrice on 2010-12-26
> **eyerouge said:**
> 
Here is what you requested:

```
snowdrop@ubuntu:~$ tree /proc/acpi/video
/proc/acpi/video
`-- IGPU
    |-- DOS
    |-- info
    |-- LCD1
    |   |-- brightness
    |   |-- EDID
    |   |-- info
    |   `-- state
    |-- POST
    |-- POST_info
    `-- ROM

2 directories, 9 files

```

Thanks a lot ! I have the exact same layout... 

Could you also post the contents *LCD1/brightness*, *LCD1/EDID*, *LCD1/info*, *LCD1/state* ? On my laptop, all but *info* say the following:

```
$ cat /proc/acpi/video/IGPU/LCD1/brightness 
<not supported>
```Thanks a bunch...

---

### Post by Lucien.Malavard on 2010-12-30
Having completed all the steps in [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)
I soon discovered that Suspend and Hibernate do not work in 10.10 for a MacbookAir 3,1 (11"). After either suspend or hibernate, the system wakes up to a black screen, with occasional one-time flash of something before going back to black again. Manual power off and restart was required every time.

Has anyone tried Suspend or Hibernate, either with/without "Spin down disk whenever possible" in the System > Preferences > Power Management setup? If so, did you find a similar problem? How did you work around it? Thanks!

---

### Post by Dreamsorcerer on 2010-12-30
> **Lucien.Malavard said:**
> Having completed all the steps in [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)
I soon discovered that Suspend and Hibernate do not work in 10.10 for a MacbookAir 3,1 (11"). After either suspend or hibernate, the system wakes up to a black screen, with occasional one-time flash of something before going back to black again. Manual power off and restart was required every time.

Has anyone tried Suspend or Hibernate, either with/without "Spin down disk whenever possible" in the System > Preferences > Power Management setup? If so, did you find a similar problem? How did you work around it? Thanks!

Just in case it's a silly mistake, did you try moving the trackpad or hitting some keyboard buttons? When it resumes it should resume to a locked screen, any input will make the password field appear. If not, then I don't know what might be wrong.

Suspend works fine for me, I get a black screen for a couple of seconds before it allows me to login. Couldn't comment on hibernate as I don't have a swap partition. This is on a 3,2 (13"). And yes, I have "spin down disk" turned on, although I imagine this doesn't actually do anything.

---

### Post by npgall on 2010-12-30
> **Lucien.Malavard said:**
> I soon discovered that Suspend and Hibernate do not work in 10.10 for a MacbookAir 3,1 (11").

@Lucien.Malavard
I have 10.10 on the 11"inch/3,1 version and suspend and hibernate work for me. You might have missed the "Fix backlight problem after suspend" section in the wiki? -that was required for me.

---

### Post by wersdaluv on 2010-12-31
On first boot, after replacing "quiet splash" with "nomodeset", I land on the command line. I even logged in and tried "startx, but I got
```
Fatal server error:
no screens found
```

Any idea how to fix this? Thanks in advance!

---

### Post by wersdaluv on 2011-01-01
> **wersdaluv said:**
> On first boot, after replacing "quiet splash" with "nomodeset", I land on the command line. I even logged in and tried "startx, but I got
```
Fatal server error:
no screens found
```

Any idea how to fix this? Thanks in advance!
Ubuntu is finally up and running. I think the fix was to not to upgrade packages to latest versions while installing Ubuntu. That's the only thing I did that wasn't stated on the wiki page.

Can you confirm this? If it's correct, let's put it on the wiki.

---

### Post by Lucien.Malavard on 2011-01-02
> **wersdaluv said:**
> Ubuntu is finally up and running. I think the fix was to not to upgrade packages to latest versions while installing Ubuntu. That's the only thing I did that wasn't stated on the wiki page.

Can you confirm this? If it's correct, let's put it on the wiki.

Unfortunately, I don't think that your conjecture is true. I installed without any problems when I selected the option to update packages on the fly while installing.

---

### Post by Lucien.Malavard on 2011-01-02
> **npgall said:**
> @Lucien.Malavard
I have 10.10 on the 11"inch/3,1 version and suspend and hibernate work for me. You might have missed the "Fix backlight problem after suspend" section in the wiki? -that was required for me.

Thanks, NPGALL and DREAMSORCERER on #260 and #259, respectively. I tried the physical acts suggested by DREAMSORCERER when it first was observed -- no go there. Also I went through all the steps (as per NPGALL) including the backlight fix as suggested by on the Community page. 

Strange thing was the first time around when I installed 10.10, the suspend/wake function worked fine. But I had to reformat my machine and do it all again a few days later and this is when the suspend/wake problem surfaced. I guess this is one of the random facts destined for the X-files ... unless someone else faced the same set of events as me :P ... if so, do let us know!

Thanks everyone and happy new year!

---

### Post by Lucien.Malavard on 2011-01-02
Thanks again NPGALL (post #260). I finally figured out my problem! It was a silly mistake the second time around when I re-installed 10.10 on the MBA. In fixing the backlight problem, i.e.
```

sudo gedit /etc/pm/config.d/defaults
```
I had forgotten to _uncomment_ the parameter options on the defaults file:
```
HIBERNATE_RESUME_POST_VIDEO="yes"
SUSPEND_MODULES="mbp-nvidia-bl"
ADD_PARAMETERS="--quirk-reset-brightness"
DROP_PARAMETERS="--quirk-none"
```So now suspend/wake is working normally, as what I had after my first install. Merci beaucoup!

---

### Post by wersdaluv on 2011-01-02
I miss the instant sleep and wake (plus instant wifi connection) from closing and opening the laptop lid when running OS X. I hope we'll get that experience on Ubuntu

---

### Post by wersdaluv on 2011-01-03
I'm following the "Fan" instructions [on the wiki]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat"). 

Running **macfanctld -f** gives me
```
$ macfanctld -f
Running in foreground, log to stdout.
Using parameters:
	temp_avg_floor: 45
	temp_avg_ceiling: 55
	temp_TC0P_floor: 50
	temp_TC0P_ceiling: 58
	temp_TG0P_floor: 50
	temp_TG0P_ceiling: 58
	fan_min: 2000
	log_level: 0
Found 1 fan.
Found 27 sensors:
	 1: TB0T - Battery TS_MAX Temp 
	 2: TB1T - Battery TS1 Temp 
	 3: TB2T - Battery TS2 Temp 
	 4: TC0D - CPU 0 Die Temp 
	 5: TC0E - ? 
	 6: TC0P - CPU 0 Proximity Temp 
	 7: TC1E - ? 
	 8: TCZ3 - ? 
	 9: TCZ4 - ? 
	10: TCZ5 - ? 
	11: TG0E - ? 
	12: TG1E - ? 
	13: TG2E - ? 
	14: TGZ3 - ? 
	15: TGZ4 - ? 
	16: TGZ5 - ? 
	17: TH0F - ? 
	18: TH0O - ? 
	19: TH0o - ? 
	20: TM0P - ? 
	21: TN0D - MCP Die 
	22: TN0P - MCP Proximity 
	23: TN1D - ? 
	24: Th1H - ? 
	25: Tp0P - ? 
	26: Ts0P - Palm Rest Temp 
	27: Ts0S - ? 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual

```

so I can't get the numbers for my TCZ3 and TGZ3. 

Any idea what's wrong? I'd like to make sure my fan is fine.

---

### Post by litemotiv on 2011-01-09
If any of the devs are still reading here:

I've just upgraded to kernel 2.6.37 vanilla, most of the important hardware is working out of the box now:

- backlight
- audio
- wireless (manual modprobe of brcm80211, udev not using it yet)

Still needs custom module:

- keyboard

The touchpad i'm not sure about, the bcm5974 is not automatically inserted at least. Is the patched module supposed to be incorporated in 2.6.37 yet? How can i find this out?

---

### Post by henrique on 2011-01-10
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) suggests using the discard mounting option for ext4 in order to enable the TRIMM command support.

Any opinions on this? Maybe it should be added to the wiki.

---

### Post by User4519 on 2011-01-10
Hello all!

I've been reading this thread with great interest as I'm seriously considering cancelling my preorder for the ASUS U36jc that is to be in stock tomorrow according to the dealer and chosing the MBA3,2 instead.

After reading this it seems pretty clear that Maverick should run pretty nicely, but I do have a couple of outstanding questions that I hope someone may be able to clear up for me:

1) Having to press the fn key to get at F1, F2, etc. Is this still needed with Linux? I'm uncertain as I read that you can't have this info (about the fn key being pressed) available to X or other high-level apps, but I don't see how that would make it impossible. Aren't there driver-level settings to tweak?

2) Battery life. I only hear answers guessing about it in percentages compared to OS X battery life, but that doesn't really tell me anything. Can someone provide HH:MM numbers? For instance, on my ASUS UL30A which was stolen last year, I'd get about 4-5 hrs normal browsing and work time with full screen brightness and wifi+bt on.

3) Touchpad functionality. I hear people talking about inconsistencies, having to double or triple click to get a click, but don't hear any rebuttals. In particular:
* Does tapping (not the "press hard and it clicks") work like a "normal" supported touchpad?
* Do two- and three-finger tapping work? (and if so, which is middle and which is right click, and is it configurable?)
* Does vertical two-finger scrolling work?
* Does horizontal two-finger scrolling work?
* Does pinching and rotating work? (provided that any apps actually support this, I haven't ever used it myself :) )

4) Does the microphone work? I read one write that his didn't, haven't seen otherwise.

5) Does displayport audio work?

@Henrique: I'd like to know this, too. I'm thinking that the fact that the SSD is handled by the ata driver would prevent TRIM from working? But I don't know. Either way, OS X doesn't support TRIM either, so at least this wouldn't be a step down ;)

I guess that's all my questions :D

Hope to hear something :)

Thanks

---

### Post by User4519 on 2011-01-10
@Henrique:

It seems it might not be necessary to do any active TRIMming with this SSD, if this article is right:

[http://www.anandtech.com/show/3991/apples-2010-macbook-air-11-13inch-reviewed/4](http://www.anandtech.com/show/3991/apples-2010-macbook-air-11-13inch-reviewed/4)

---

### Post by User4519 on 2011-01-10
@myself, regarding fn+f keys, this IS configurable, see:
[http://blog.adamsbros.org/2009/06/14/linux-macbook-function-key-mode-fnmode/](http://blog.adamsbros.org/2009/06/14/linux-macbook-function-key-mode-fnmode/)

---

### Post by Dreamsorcerer on 2011-01-12
> **DanielBuus said:**
> 2) Battery life. I only hear answers guessing about it in percentages compared to OS X battery life, but that doesn't really tell me anything. Can someone provide HH:MM numbers? For instance, on my ASUS UL30A which was stolen last year, I'd get about 4-5 hrs normal browsing and work time with full screen brightness and wifi+bt on.
With mid screen brightness (which is very viewable in most environments), light-moderate usage, I definitely get over 5 hours. I have noticed that if I run Powertop, Ubuntu is not brilliant at power management, so I think this could be improved with some tweaking somehow.

> **DanielBuus said:**
> 3) Touchpad functionality. I hear people talking about inconsistencies, having to double or triple click to get a click, but don't hear any rebuttals. In particular:
* Does tapping (not the "press hard and it clicks") work like a "normal" supported touchpad?
* Do two- and three-finger tapping work? (and if so, which is middle and which is right click, and is it configurable?)
* Does vertical two-finger scrolling work?
* Does horizontal two-finger scrolling work?
* Does pinching and rotating work? (provided that any apps actually support this, I haven't ever used it myself :) )
I became accustomed to the click and got annoyed with it clicking when my hand brushed over the trackpad, so I turned tapping off, but I think it did work (just not sure how well).
Two finger click works for a right-click, and 3 finger click works for a middle click. That's the norm, so I've never looked into configuring it.
Horizontal/vertical scrolling works fine.
Not aware of anything that uses pinching or rotating to be able to test this out.

The only problem I have with it, is the discrepancy at the bottom of the trackpad. If you have a finger in the bottom ~20% of the trackpad, and your fingers are not positioned horizontally, then multi-touch (right-click, scrolling etc.) doesn't work, it acts as if you only had one finger on the trackpad. Doesn't seem that anyone has come up with a fix for this yet.

> **DanielBuus said:**
> 4) Does the microphone work? I read one write that his didn't, haven't seen otherwise.
Just opened sound recorder, and it's working fine for me. Does seem a tiny bit quiet though.

And, thanks for the Fn key tip, added to the wiki.

---

### Post by Dreamsorcerer on 2011-01-12
-Stupid servers...-

---

### Post by Dreamsorcerer on 2011-01-12
-...posting my message 4 times...-

---

### Post by Dreamsorcerer on 2011-01-12
-...or, maybe I just like editing these messages.-

---

### Post by User4519 on 2011-01-12
LOL :D Thanks for the message(s) ;)

5 hours sounds pretty good, especially considering the nVidia chip.

Also very nice to hear that both double and triple clicking works properly. I never managed to get triple clicking to work properly on my UL30A.

Thanks! :)

---

### Post by Dreamsorcerer on 2011-01-13
> **DanielBuus said:**
> @myself, regarding fn+f keys, this IS configurable, see:
[http://blog.adamsbros.org/2009/06/14/linux-macbook-function-key-mode-fnmode/](http://blog.adamsbros.org/2009/06/14/linux-macbook-function-key-mode-fnmode/)

Just realised this configuration doesn't persist after boot, anybody know how to make it permanent?

---

### Post by User4519 on 2011-01-14
> **Dreamsorcerer said:**
> Just realised this configuration doesn't persist after boot, anybody know how to make it permanent?

You could always add it to /etc/rc.local (as root). It'll then run at the end of every boot sequence.

---

### Post by Kevincav on 2011-01-19
Hello,

I just received my 13" macbook air today.  I'm trying to install Ubuntu per the wiki page, although I'm installing with the USB.  It recognizes it and goes through everything normal except for I can't select f6 nor nomodeset.  Is there a way to do this still.  I'm doing the 32 bit version.

---

### Post by User4519 on 2011-01-19
First off, I'd say use the 64-bit one?

---

### Post by kurogumo on 2011-01-19
Anyone get the trackpad working properly yet?  Everything on on mine works properly except "tap to click", basically crashes/freezes/stops working after a period of time/randomly.  The strange thing is that 2 finger scroll still works and "press to click, 2 finger press to right click" still work properly.  Works again when I log out and log in again though.  Any ideas?

---

### Post by dupdupdup on 2011-01-19
hi guys what program can i use to install via usb? not sure what program to make my usb bootable.

---

### Post by Kevincav on 2011-01-19
> **DanielBuus said:**
> First off, I'd say use the 64-bit one?

I just have 2gb of ram.

---

### Post by User4519 on 2011-01-19
> **Kevincav said:**
> I just have 2gb of ram.

That's Microsoft talk ;) 32-bit Linux can allocate up to 64GB of memory. 64-bit is not just about address space, it's also about pushing more data per clock cycle between your memory banks, video cards, caches, etc. and your CPU. Stuff like video en/decoding, database applications, well basically any application that will benefit from being able to push large amounts of data back and forth will benefit from a 64-bit environment.

32-bit apps on 64-bit *buntu a year or two back were a bit "quirky". Today you won't even notice that you're running a mix of 32 and 64-bit applications. It all happens seamlessly thanks to the ia32libs and nice package maintenance.

---

### Post by alissa.huskey on 2011-01-22
> **dave1164 said:**
> After the Ubuntu installer was done, I was still not able to boot into Ubuntu on the 10GB partiton. For some reason the installer did not create me a kernel. I had to boot via the 2GB installer partition again, mount the 10GB target partition, chroot to it (see: [http://ubuntuforums.org/showthread.php?t=1603365&page=7](http://ubuntuforums.org/showthread.php?t=1603365&page=7)) and (connected via WiFi now) manually run apt-get update / upgrade. 

While in chroot, I also added the mactel-support/ppa (see: [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)) and ran update/upgrade again. This way I never have to navigate through any display issues.

Still no boot! For some reason I had to manually install grub to sd4. So with the chroot in place I ran: "sudo grub-install --recheck --root-directory=/mnt /dev/sda4 --force".

Ubuntu is now a joy to use on the new Air. Many thanks to those that made this possible.

Hey there,

Thank you for your helpful instructions!  By following this post, I've been able to get ubuntu 10.10 amd64 installed on a partition on my macbook air 3,2.  However, I believe I've run into the problem that you mentioned--when I select the linux partition from refit, grub loads but does now show a line for booting into linux!  (The lines are something to the effect of "memory test" and "osx /dev/sda3".)  

You mentioned that you are able to connect via wifi when you are booted into the installer partition.  How did you accomplish that?  I am not connected to the internet when booted into the 2GB installer partition, and my attempts to activate the driver in that partition have failed.

I would appreciate any insight you could provide.

Thank you,

Alissa

---

### Post by sekom on 2011-01-26
> **SuperDodge said:**
> I've attached a picture of the screen during the installer.

boot without GRAPHIC
from the ALTERNATE ubuntu CD [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)
and PRESS ESC to enter BOOT in EXPERT mode

---

### Post by rgclark84 on 2011-01-26
Hi all, new to the forums. Thanks to all that have contributed here and to the wiki article. I have successfully installed Ubuntu (ver. 10.10, 32-bit) on my MacBook Air (3,2). However, I have the following three issues:

1. The mic volume is very low. I have verified in alsamixer that the volume is turned up. However, within the Sound preference, no input (i.e. my voice) is recognized at all. The radial button for the device is selected and the active profile is "Analog Stereo Duplex." Only Sound Recorder recognizes inputs. 

2. After every reboot, Bluetooth is reenabled. I would like to keep Bluetooth off the majority of the time to conserve battery life.

3. I would like to disable the touchpad clicks and use the button as the only "click" source. Under the Mouse preferences, I disabled the option entitled "Enable mouse clicks with touchpad" to no avail.

Any help is greatly appreciated. Thanks in advance!

P.S: Would using the 64-bit version solve any of these issues?

---

### Post by marceljj on 2011-02-21
> **SuperDodge said:**
> I've attached a picture of the screen during the installer.
Exact same thing happens to me.

---

### Post by cyberco on 2011-02-25
I'm trying to install 10.10 from the 64-bit alternate CD but that leaves me without wireless. There are no 'restricted drivers' in the restricted driver manager's list so I tried using this guide and install the drivers from the CD:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

But there is no 'bcmwl-kernel-source' in a folder '/pool/restricted/b/bcmwl' on the alternate-64 CD. Both are not on the CD. 

This guy seems to have it working although he doesn't mention if he uses 32 or 64 bit:

[http://ubuntuforums.org/showpost.php?p=10016134&postcount=22](http://ubuntuforums.org/showpost.php?p=10016134&postcount=22)

Anybody got 64-bit 10.10 running properly? Or am I at a dead end and are there no proper restricted 64-bit drivers for the wifi of the MBA?

---

### Post by npgall on 2011-02-26
> **cyberco said:**
> 
Anybody got 64-bit 10.10 running properly? Or am I at a dead end and are there no proper restricted 64-bit drivers for the wifi of the MBA?

I'm running 64-bit 10.10, everything works fine incl. wireless. I installed from an LG USB CD-ROM though, installing from USB flash stick is much more complicated.

FYI there are two Broadcom wifi drivers which will work. I'm using the broadcom STA/binary driver (aka the "wl" driver), which was included on the standard 10.10 64-bit CD.

Since 10.10 Broadcom have released their drivers as 100% open source, so you could try to build/install the other "brcm80211" driver by hand if you prefer that. brcm80211 will probably be used by default in 11.04.

There is a wiki here, details all the steps you need to follow: [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

I'd still recommend using a USB CD-ROM though.

---

### Post by cyberco on 2011-02-26
Thanks npgall! It turns out that the Alternate CD didn't include restricted drivers. After burning an Ubuntu Desktop CD I was able to install all required drivers.

I must say my network connection is quite bad. Somehow the latency and download speed are horrible compared to OSX. In OSX pages load within a second while in Chromium or Firefox in Ubuntu 10.10 (64-bit) it always takes seconds. I had the same issue with my previous MBA (2,1) on both wireless and wired connections and at different places. Anyone here that has a speedy internet experience?

---

### Post by npgall on 2011-02-26
> **cyberco said:**
> Somehow the latency and download speed are horrible compared to OSX.

That will be power management in the STA/wl driver.

Try this command:
sudo iwconfig eth0 power off

...that 'power off' means disable the aggressive power management in the wifi driver. Then reconnect to your wifi network. Monitor latency by pinging your router.

As far as I can tell, this is an issue when I boot the machine while not plugged into the mains. When power management is not active I can get 33 Mbps (speedtest.net), when it is active the most I get is 5. 

It does bother me a bit, brcm80211 might be a better solution. See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008)

EDIT: So effectively, if you want to permanently disable wifi power management...

STEP 1: 
gksu gedit /etc/pm/power.d/wireless
--- paste this ---
#!/bin/sh
/sbin/iwconfig eth0 power off

------------------
STEP 2:
sudo chmod +x /etc/pm/power.d/wireless


You should be able to check if power management is active using: sudo iwconfig eth0

---

### Post by c3n on 2011-02-27
hi,

i installend maverick 64 on a macbookair3,1 and here's just a quick hint: i had some problems with wlan (it was extremely slow). the solution was to put

/sbin/iwpriv eth1 set_pm 0

in a new executable file in

/etc/network/if-pre-up.d

now it's as fast as on my old notebook :-)
dunno if theres a more "standard" place to put that bit of config, but hey, it works

EDIT: sorry i only just now realized that someone already posted something similar, but maybe you can save some power by reenabling set_pm in if-post-down.

---

### Post by npgall on 2011-02-27
@c3n that's interesting, thanks. That might solve an issue I had with the wl driver where if I connect to my router on the 5GHz band, the 'sudo iwconfig eth0 power off' command wouldn't have an effect for very long (strangely connecting via the 2.4GHz band was fine).

Re: discussion of the brcm80211 driver earlier...
I just bit the bullet and upgraded to brcm80211, as of 10 minutes ago. It was fairly painless, and took about 10 minutes. I scripted the process (below) in case anyone is interested.

The approach I took was to install on my 10.10 laptop the kernel 2.6.38 (release candidate 6) which will ship with 11.04 (which includes the brcm80211 driver), plus install the firmware which brcm80211 requires. This is based on discussions in this thread, but with the latest Natty kernel: [http://ubuntuforums.org/showthread.php?t=1617380&page=12](http://ubuntuforums.org/showthread.php?t=1617380&page=12)

STEP 1: Save this as 'install_kernel_2.6.38-rc6.sh':
---
#/bin/sh

if [ ! "`cat /etc/issue`" = "Ubuntu 10.10 \n \l" ] ; then
     echo "This script is for Ubuntu 10.10 only"
     exit 1
fi

if [ ! "`whoami`" = "root" ] ; then
     echo "This script must be run as root"
     exit 1
fi

mkdir /tmp/install_kernel_2.6.38-rc6 2>/dev/null
cd /tmp/install_kernel_2.6.38-rc6
rm *

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc6-natty/linux-headers-2.6.38-020638rc6_2.6.38-020638rc6.201102220910_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-rc6-natty/linux-headers-2.6.38-020638rc6_2.6.38-020638rc6.201102220910_all.deb") && \
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc6-natty/linux-headers-2.6.38-020638rc6-generic_2.6.38-020638rc6.201102220910_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-rc6-natty/linux-headers-2.6.38-020638rc6-generic_2.6.38-020638rc6.201102220910_amd64.deb") && \
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc6-natty/linux-image-2.6.38-020638rc6-generic_2.6.38-020638rc6.201102220910_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-rc6-natty/linux-image-2.6.38-020638rc6-generic_2.6.38-020638rc6.201102220910_amd64.deb") && \
wget [http://ftp.uk.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-brcm80211_0.28_all.deb](http://ftp.uk.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-brcm80211_0.28_all.deb) && \
dpkg --install --recursive . && \
update-grub && \
echo "Installed new kernel without errors (but check above for warnings)."

---

STEP 2: Run it: sudo sh install_kernel_2.6.38-rc6.sh
STEP 3: Reboot
STEP 4: After reboot (maybe before reboot?) go into System -> Administration -> Additional Drivers, and deactivate the Broadcom STA driver
STEP 5: Reboot again


So far I can report that I'm connected to my router on the 5GHz band at 86.7 Mb/s (which must be wireless n) according to iwconfig. My internet is running at full speed. And the driver is very fast at connecting to my router, no longer does it take ages to scan before connecting. Ping latency to my router averages <1ms.

I did notice a dropout while I was running a speedtest when connected on the 2.4GHz band, but it recovered to full speed after a few seconds. So far no issues at 5GHz.

A bit concerned that I'm running an alpha release kernel though, fingers crossed!! I still have the standard kernel+wl installed just in case :)

UPDATE :: Sound doesn't work in this kernel, /var/log/messages contains lots of errors like "snd_hda_codec_cirrus: Unknown symbol snd_hda_get_connections (err -22)" and "snd_hda_codec_cirrus: disagrees about version of symbol snd_hda_set_vmaster_tlv" etc. Looks like an incompatibility with the sound libraries in 10.10? Arrgh. Also the machine froze while shutting down in one instance. It was going so well... :(

---

### Post by c3n on 2011-02-27
different question: does anybody know how to change touchpad parameters? it's driving me crazy that i have to wait a bit between moving the mouse and tapping to click somewhere

---

### Post by cyberco on 2011-02-27
Disabling powermanagement solved my networking problems indeed. Now I'm browsing around at full speed again! One problem I'm still experiencing is the time it takes after a suspend before the network reconnects. It takes at least 30 seconds. This is quite different from OSX where the laptop gets out of suspend mode and onto the network within 2 seconds!

---

### Post by vickoxy on 2011-03-17
Sorry for not reading all posts-one question only-if i buy the new macbook air 11, could i install ubuntu 64 bit (dual-boot with mac os, or only ubuntu-no matter)...?

---

### Post by npgall on 2011-03-17
Yes.

---

### Post by User4519 on 2011-03-18
> **vickoxy said:**
> Sorry for not reading all posts-one question only-if i buy the new macbook air 11, could i install ubuntu 64 bit (dual-boot with mac os, or only ubuntu-no matter)...?

Seriously... Read the f**king posts... You can't be bothered? The posts aren't there for you, they're there for the interwebs... You're an idiot. Damn you.

---

### Post by Dreamsorcerer on 2011-03-19
> **DanielBuus said:**
> Seriously... Read the f**king posts... You can't be bothered? The posts aren't there for you, they're there for the interwebs... You're an idiot. Damn you.

Lol, to avoid this in future, perhaps SuperDodge or an admin could edit the first post and put a link to the wiki page?
[https://help.ubuntu.com/community/MacBook Air]("https://help.ubuntu.com/community/MacBook%20Air")

---

### Post by dentifrice on 2011-03-21
Hey there,

Haven't been here in a while. Has there been any progress in :

[LIST]
[*]featurefull EFI booting?
[/LIST]

[LIST]
[*]*nouveau* FLOSS driver for the NVidia chipset?
[/LIST]
 
On a sidenote, what patches are still needed for kernel 2.6.38 ? last I looked quite a few bits were missing still - has there been more efforts towards merging with upstream? any pointer would be appreciated.

Thanks,

---

### Post by DarkTide on 2011-04-12
I had been running 32-bit too, and when I saw your post I checked and  yes mine was only showing 2.7GB RAM too. So today I tried to reinstall  with 64-bit too, and got the same issue - screen goes blank during boot,  even with nomodeset.

---

### Post by User4519 on 2011-04-12
> **DarkTide said:**
> I had been running 32-bit too, and when I saw your post I checked and  yes mine was only showing 2.7GB RAM too. So today I tried to reinstall  with 64-bit too, and got the same issue - screen goes blank during boot,  even with nomodeset.

FTR, you don't **have** to run the 64-bit version to address +4GB of mem, just switch from the -generic kernel to the -pae one :)

---

### Post by eyerouge on 2011-04-30
[SIZE="3"]**Updating from 10.10 to 11.04 & sound issues**[/SIZE]

After updating my perfectly working 10.10 (64) to 11.04 yesterday, my mousepad and sound wasn't working any longer. 

I redid *all* the steps in [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat?action=show&redirect=MacBook+Air](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat?action=show&redirect=MacBook+Air) and that took care of the mousepad. 

Sound issue remains though: I get no sound in 11.04. I have included two screenshots showing my settings and possibilities from the sound config in Ubuntu and also alsamixer. 

Have you guys had any luck with this? Is this a problem or am I the only lucky one? 

[IMG]http://chaosrealm.net/wtactics/files/pics/2011_04_%24d_16.jpeg[/IMG]  

[IMG]http://chaosrealm.net/wtactics/files/pics/2011_04_%24d_15.jpeg[/IMG]

---

### Post by skypilott on 2011-04-30
Audio driver from Mactel repository is not needed anymore with 11.04.
Just remove it and reboot.

See :
[ http://ubuntuforums.org/showthread.php?t=1701895]("http://ubuntuforums.org/showthread.php?t=1701895")

---

### Post by eyerouge on 2011-04-30
> **skypilott said:**
> Audio driver from Mactel repository is not needed anymore with 11.04.
Just remove it and reboot.

See :
[ http://ubuntuforums.org/showthread.php?t=1701895]("http://ubuntuforums.org/showthread.php?t=1701895")

Thanks a bunch! :)  

Removed *snd-hda-dkms* from within Synaptic package manage, rebooted, and sound seems to work.

---

### Post by Dreamsorcerer on 2011-05-01
Hey guys, just updating the wiki for Narwhal, going through a clean install, many of the steps are no longer needed, as they work out of the box now. But, some steps seem to have changed.

For backlight support, it says to edit  /etc/X11/xorg.conf, and add a line to the Nvidia section. My xorg.conf after a clean install only consists of:

```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```

There appears to be no Nvidia section. I tried replacing that with the nvidia block, but no luck, anybody know what needs to be changed to get backlight working?

---

### Post by User4519 on 2011-05-02
> **Dreamsorcerer said:**
> ```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```There appears to be no Nvidia section. I tried replacing that with the nvidia block, but no luck, anybody know what needs to be changed to get backlight working?

Try running ```
sudo nvidia-xconfig
``` first. That should generate nVidia stuff. Make sure you have installed the proprietary driver, of course ;)

---

### Post by Dreamsorcerer on 2011-05-02
> **DanielBuus said:**
> Try running ```
sudo nvidia-xconfig
``` first. That should generate nVidia stuff. Make sure you have installed the proprietary driver, of course ;)

OK, still not working. It's generated a full xorg.conf file, but brightness is still not changing. The Device block now looks like this:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

---

### Post by User4519 on 2011-05-02
> **Dreamsorcerer said:**
> OK, still not working. It's generated a full xorg.conf file, but brightness is still not changing. The Device block now looks like this:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

Sorry - I actually missed the point about brightness controls... This is probably ACPI related, and it may just be broken right now. Like this thread, which I'm following (though my machine isn't a Lenove/IBM): [https://bugs.launchpad.net/bugs/625364](https://bugs.launchpad.net/bugs/625364)

I have multiple issues with ACPI in kernels since 2.6.38-3 IIRC (current being -8), also with brightness controls. Just for the heck of it, try using the brightness keys straight after grub launches. For some weird weird reason, if I use mine while booting up, they work and keep working. If I boot into X without having used them, they do not.

Also, since Natty I no longer have a /var/log/messages (!!!!!).

I experienced ACPI regressions with Maverick on the desktop (had to boot with nolapic noapic or get kernel panics), and with Natty, the trouble is making its way to my laptop :( I believe patience will prove virtuous now. Guess that's why a lot of other distros are faaar from using 2.6.38 ATM.

---

### Post by Luke.Hoersten on 2011-05-05
My Nvidia display fails when I upgrade from linux-image-2.6.38-8-generic to linux-image-2.6.38-9-generic. Not sure what the problem is but if you hit this, roll back the kernel.

Anyone know how to actually fix the -9 kernel?

---

### Post by lonflavio on 2011-05-14
Hi,

I'm having an issue with installing the graphics card, I cant get the first step on to work
[https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

sudo apt-get install btusb-dkms applesmc-dkms hid-apple-dkms bcm5974-dkms xf86-input-multitouch snd-hda-dkms mbp-nvidia-bl-dkms -y

i get the following error

> flavio@flavio-MacBookAir:~$ sudo apt-get install btusb-dkms applesmc-dkms hid-apple-dkms bcm5974-dkms xf86-input-multitouch snd-hda-dkms mbp-nvidia-bl-dkms -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package btusb-dkms
E: Unable to locate package applesmc-dkms
E: Unable to locate package snd-hda-dkms
E: Unable to locate package mbp-nvidia-bl-dkms


I am running Ubuntu Ubuntu 11.04 64bit on a MacBook Air late 2010 11" (new model)

any suggestions?

---

### Post by pbhedlund on 2011-05-14
> **lonflavio said:**
> 

any suggestions?

These are the mactel packages available for natty [https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=natty]("https://launchpad.net/%7Emactel-support/+archive/ppa?field.series_filter=natty"). I simply ignored the rest on a fresh install and have not had any problems. I am on a Macbook Air 3,2.

---

### Post by vickoxy on 2011-05-15
Hi,
could someone post how long does air work on battery? My Macbook Pro has at least 60-90 min less with 10.10 as under MacOS.

And another question-after hibernation/suspense-how much time need macbook air to wake up and establish wifi connection?

---

### Post by pbhedlund on 2011-05-15
> **vickoxy said:**
> Hi,
could someone post how long does air work on battery? My Macbook Pro has at least 60-90 min less with 11.10 as under MacOS.

And another question-after hibernation/suspense-how much time need macbook air to wake up and establish wifi connection?

Your observation about battery life is probably correct. I haven't really measured on the Air but I get many hours on battery only.

Since there is no kms video driver for the air waking up from suspend takes up to 10 s. With the new in-kernel wifi driver in 11.04 the Air reconnects almost instantaneously. Much faster than than the previous version.

---

### Post by vickoxy on 2011-05-15
Thanks-well i meant 10.10 on may MBP...

---

### Post by notsalty on 2011-05-21
> **SuperDodge said:**
> I just got one of the new MacBook Airs today and I'm trying to install Ubuntu.  I've installed refit, resized the Mac Partition, created two new partitions, used dd to image a bootable USB to one of the new partitions and I'm able to boot off of it.

When booting into Ubuntu, the screen is off-center with vertical colored bars that roll on the screen.  Has anyone figured out how to get around this yet?
I've seen the same thing. If you press F6 at the beginning of the setup you'll get a few options choose "no mode set" end then Esc. This may fix the problem.

---

### Post by aengle1429 on 2011-05-25
Just successfully triple booted Windows Ultimate 64bit, Ubuntu 11.04 64bit, and Mac OS X... took forever. I'm on the 13" Macbook Air with upgraded RAM and 120GB SSD.

Here's how I did it... hope this proves to be useful to anyone:
First, I had 120GB only running OS X. I partitioned to 3 separate spaces, one 33 GB for Ubuntu (another user on page 25 told this, and I followed his method there), and 44 and 44 for Windows and Mac.

I also had rEFIt installed and ready.

I installed Ubuntu first (if you install Windows first, Ubuntu will hang at the Preparing to Install Ubuntu step). This is very frustating; I CTR+ALT+F1'd into the CLI and ran parted and parted would repeatedly crash with stack trace outputs... unhelpful. If you install Ubuntu FIRST, ubuntu won't complain about the windows + mac os x on there beforehand.

Ubuntu was made into 10GB on root, 15GB on /home, and 8GB swap. That was painless, after I deleted the original 33GB partition made by the disk utility.

Windows installed on the MS-DOS FAT32 (I had to delete this partition too since Windows uses NTFS...)
This was also painless.. except for when rebooting you must choose the proper partition or else the entire partition where Windows was being installed will wipe itself.

Soo that was that.. I had a lot of problems if I went OS X -> Windows -> Ubuntu, and I had a lot of problems if I didn't allocate three separate partitions at the very beginning in OS X rather than waiting until after one of the OS' was installed.

==============================================

So for people installing 11.04, the wikipage for meerkat's post-install instructions work very well, but for some reason whenever I added the extra part to /etc/X11/xorg.conf

Section "InputClass"     MatchIsTouchpad "true"     Identifier "Multitouch Touchpad"     Driver "multitouch" EndSection


This caused my mouse to stop working! So I deleted that and I have the mouse working again... is there some error in this part?

---

### Post by gwillem on 2011-05-31
MBA3,2

Spent about 8 hrs trying to install xUbuntu dual boot with macosx (without superdrive) and finally succeeded. Here are my steps for anyone to reproduce.

Install refit according to wiki.
Install unetbootin under macosx.
Create 2 separate partition using Disk Utility: disk0s3 (smallest, 1.07GB) and disk0s4 (target for ubuntu).
Download Ubuntu Live image (11.04, 64bit)
Use unetbootin to create a usb install stick.
Use unetbootin to write bootable image to disk0s3
Reboot 2 times (power off/on) WITHOUT the usb stick connected
Boot using refit from sda3
Pick "try ubuntu" option
At the desktop, start a shell
umount -r -l -f /cdrom
Insert usb stick
mount /dev/sdb /cdrom (your usb stick)
Double click "install ubuntu" icon
Enter through the installation process, no problems here
 
I couldnt get booting from USB to work and when booting from the SSD partition you will have the problems with unmounting cdrom and unity crashing, so that's why I used unetbootin to copy the installation .iso to both the internal disk and a USB stick.

Outstanding issues: 

Backlight keys not working, always 100% lit. Edit: fixed this problem with: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/743352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/743352) but introduced another problem: after dim/suspend the backlight resets to 50% regardless of the previous setting. Edit2: Fixed this also by following the pm-utils suggestions from the Meerkat wiki page [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat)

Palm detection on touchpad doesnt seem to work.

Two/three finger clicking on touchpad is very sensitive, it takes me a couple of tries most of the time. 

Using the real touchpad button in combination with 2-finger right click (for example, when you have to drag something all over your screen) doesn't work, because keeping the 1st button pressed and then (after long delay) trying to drag, will fire up the 2 finger press event. 

Sometimes after resume, touchpad doesnt work (manual fix by reloading kernel module). Edit: fixed with
> $ sudo echo 'SUSPEND_MODULES="bcm5974"' >>/etc/pm/config.d/unload_modules


Thanks to all who made ubuntu possible on MBA! I love it.

---

### Post by houdodu on 2011-06-25
Just upgraded to 11.04 and my fan is now audible constantly. Anyone else have this problem?

---

### Post by lycoch on 2011-06-30
delete me

---

### Post by lycoch on 2011-07-03
hi everybody,
really need your help:
i do everything from the wiki but i ve got 2 issues:

i can't see divx ( sounds ok but black screen, i tried to remove the nvidia driver and it works after a reboot but i need the nvidia official driver because it s the best for us )

i can't select text with the trackpad ( neither drag and drop ) when i first click, the second finger act as a double touch  ( don t know how to explain it verywell but i m sure i m not the first one with this issue


thanx verymuch for any help

---

### Post by cyberco on 2011-07-07
I've been running 11.04 for a while now but I have a few problems:

1. My touchpad sometimes partly stops working after resuming from suspend mode. Clicking/tapping still works but moving not. So the pointer stays in one place. The only thing I know I can do is restart X, but that's quite rigoureus. Is there a way to 'restart' the touchpad? Or better, is there a solution to this problem?

2. The network driver sometimes totally freezes my Air after resuming from suspend mode. Weird enough this only happens on wifi on specifice wireless routers. On a Netgear WNDR3500 it actually happens quite often.

3. It took about 30 seconds before the Refit menu showed up after booting the Air. Blessing the disk as described here solved this:
[https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat) 
Unfortunately the Refit is skipped all together now. The Air goes straight into the Ubuntu boot process. I cannot boot into OSX anymore.

---

### Post by dfacto on 2011-08-03
(oops! wrong thread sorry!)

---

### Post by wersdaluv on 2011-08-12
@**gwillem**

Thanks for the brightness fix! Trying it now.

As for 

```
sudo echo 'SUSPEND_MODULES="bcm5974"' >>/etc/pm/config.d/unload_modules 

```

I get

```
bash: /etc/pm/config.d/unload_modules: Permission denied

```

Any idea?

---

### Post by dfacto on 2011-08-12
try this:
```

echo 'SUSPEND_MODULES="bcm5974"' | sudo tee -a /etc/pm/config.d/unload_modules

```

or this:
```

sudo tee -a /etc/pm/config.d/unload_modules <<-EOF
    SUSPEND_MODULES="bcm5974"
EOF

```

---

### Post by wersdaluv on 2011-09-03
> **eee.c said:**
> I noticed that as well. It can be improved in the nvidia settings, under "GPU 0 - (GeForce 320M)" -> "DFP-2 - (Apple Color LCD)", enabling dithering and choosing a depth of 6bpc.  Unfortunately, I have to reset that upon each reboot (all other nvidia settings are retained).

Clearly, that is not the ultimate solution, but it makes things a bit more bearable.
he 
It's great that I found this. Useful for Ubuntu Natty. I'll see how it works when I reboot to LightDM. I followed the Narwhal howto part on setting dithering with GDM and haven't found the same solution for LightDM

---

### Post by Raevbur on 2011-12-05
Hi.

I'm currently trying to install 11.10 on my Macbook Air 3,1. Having some difficulties though.

I can successfully enter Grub with 11.10 x64 live .iso on USB, but when booting Ubuntu or trying to install i mostly get kernel panic regarding FS.
The other times i dont get kernel panic, the picture is full of "artifacts", looks alot like broken drivers for GPU.

When i try another version, like x86 or 11.04, i can't even boot into grub. The USB isn't visible in EFI or rEFIt.

The internal SSD is currently running 1 partition of Windows 7 and i want to format and install only Ubuntu.

[http://dl.dropbox.com/u/17111743/B%C3%B6s/IMG_20111205_142631.jpg]("http://dl.dropbox.com/u/17111743/B%C3%B6s/IMG_20111205_142631.jpg")

Edit:
Tried 32-bit version and it seems like it actually booted, except it all looked like [this.]("http://dl.dropbox.com/u/17111743/B%C3%B6s/IMG_20111205_194206.jpg")
The sound was working though.

---

### Post by andrusz on 2011-12-26
> **Raevbur said:**
> I'm currently trying to install 11.10 on my Macbook Air 3,1. Having some difficulties though.
Try this 11.10 adjusted for Macs:

[http://cdimages.ubuntu.com/releases/11.10/release/](http://cdimages.ubuntu.com/releases/11.10/release/)

Desktop works perfectly on my MacBook Air 3,2.

---

### Post by siflake on 2012-01-02
hi i'm new here and completely new to ubuntu, i know nothing about it, was completely lost after reading the first page of this thread.. i'm trying to install 11.10 on a macbook air 3,2. i went on the ubuntu download page and followed the instructions for creating a bootable usb stick, but the usb never shows up whenever i hold alt while booting. currently downloading the image suggested by the post before me, going to try again.

would anyone suggest running it in a VM? pros/cons?

---

### Post by Wolfador on 2012-01-02
You can run it in a VM to test it out if you want. It is probably easier to install rEFIt and use that to select the usb drive to boot from. You can use [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to create the boot drive.

---

### Post by harenber on 2012-02-25
Has anybody got suspend working with 11.10 with a MacBookAir3,2?

11.10 runs rather nicely (and most of the stuff out-of-the-box) on my MBA3,2; the only open issue I have is that after suspend, the machine seems to be able to wake-up again, but the screen stays dark.

I tried to follow all the instructions given in the Wiki [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat) for Meerkat (as far as I could, most of the packages from Mactel are not for 11.10 - and maybe are not needed).

Especially I have copied and edited 

[FONT=Courier New]/etc/pm/config.d/defaults
[/FONT] 
and changed /etc/modules - however, I don't really know if this is needed, as the module mbp-nvidia-bl doesn't show up is lsmod and seems not to exist (maybe came from a Mactel package on older releases):

[FONT=Courier New]harenber@harenber-MacBookAir:~$ sudo modprobe mbp-nvidia-bl
harenber@harenber-MacBookAir:~$ lsmod|grep bl
bluetooth             166112  24 hidp,bnep,rfcomm,btusb
apple_bl               13225  0

[/FONT][FONT=Courier New]harenber@harenber-MacBookAir:/lib/modules/3.0.0-16-generic$ find . -name mbp-nvidia-bl
harenber@harenber-MacBookAir:/lib/modules/3.0.0-16-generic$ [/FONT]

I also changed the grub settings as advised, but I haven't touch xorg.conf (system layout changed to 11.10) neither gdm (I have no nvidia-settings on my system).

Maybe someone who has it running could advise me what I'm missing. Thanks a lot!!!!

---

### Post by attanze on 2012-02-26
Just installed Ubuntu 12.04 (daily build) and unfortunately don't work on Macbook Air 3,2 (2010) :(

I have vertical bars on screen and all the screen is distorted! Very serious bug. Know somebody how to fix this? Is from drivers or from xserver nouveau?

I want to try to replace the nouveau drivers with the ones provided from nVidia but I dont know how to proceed!

P.S. It seems that is the bug reproduced here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784")

---

### Post by C S on 2012-02-29
> **attanze said:**
> Just installed Ubuntu 12.04 (daily build) and unfortunately don't work on Macbook Air 3,2 (2010) :sad:

I have vertical bars on screen and all the screen is distorted! Very  serious bug. Know somebody how to fix this? Is from drivers or from  xserver nouveau? 
[...]
P.S. It seems that is the bug reproduced here:[...]

I am running 12.04 on a MacBook Air 3,2.  It works fine.  If you made any modifications to your system for an earlier Ubuntu version, I would undo them.  A lot of those mods are unnecessary on 12.04.  I did a clean install of 11.10 and upgraded and all the hardware worked without any issues.

---

### Post by C S on 2012-02-29
> **harenber said:**
> Has anybody got suspend working with 11.10 with a MacBookAir3,2?

11.10 runs rather nicely (and most of the stuff out-of-the-box) on my  MBA3,2; the only open issue I have is that after suspend, the machine  seems to be able to wake-up again, but the screen stays dark.

[...]

Maybe someone who has it running could advise me what I'm missing. Thanks a lot!!!!

I have a MacBook Air 3,2 running 12.04.  Resume from suspend will not work until you upgrade the kernel to 3.2.  I found several bug reports about that, so I upgraded to 12.04 and problem gone!  I would not follow any of the instructions to modify your system for the older Ubuntu versions.  A lot of those problems (with backlight etc) are supposed to be fixed in 12.04... and as far as I can see, everything works fine "out of the box".

---

### Post by C S on 2012-02-29
Ok, so I have 12.04 running on my MacBook Air 3,2; everything's great, BUT... there's this one thing nagging me (and sucking life out of my battery!).

When I run powertop, I see two devices called "Display backlight".  One of them seems to correspond to my actual display, e.g. when I turn the display down, the usage of that device seems to go down a correspondingly correct amount.  The other is always at 100% no matter what I do.  It also sucks up a good 1-1.1 watts.  Since I've noticed I could lose a good 20 minutes or more of battery life from that extra power consumption, I'm of course interested in getting rid of it.  

I've installed laptop-mode-tools, and it disables/suspends a lot of things, like the various usb ports.  But I'm not sure it's disabling the mini-display port, which I am considering the prime culprit.  

So I guess my question is, am I right?  Is it that mini-display port?  If so, how do I keep power from going to it?  I never use it at all, so even disabling it (rather than suspending it somehow) would be satisfactory.

---

### Post by derEremit on 2012-03-14
> **attanze said:**
> Just installed Ubuntu 12.04 (daily build) and unfortunately don't work on Macbook Air 3,2 (2010) :(

I have vertical bars on screen and all the screen is distorted! Very serious bug. Know somebody how to fix this? Is from drivers or from xserver nouveau?

I want to try to replace the nouveau drivers with the ones provided from nVidia but I dont know how to proceed!

P.S. It seems that is the bug reproduced here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784)

when you install the kernel mentioned in #9 from this bug report 3.3-rc1 the graphics distortion is fixed. Unfortunately wireless does not work with that kernel.

Does anyone have a fix for the touchpad behaviour?
I mean i can't click and drag.

These are the two main problems i encountered after a fresh install of 12.04 beta1.

---

### Post by derEremit on 2012-03-16
For anyone who's interested.
Touchpad is working as expected as of today. 16.03.2012
Updates in synaptics driver

Does anyone know how to get wireless drivers working with mainline kernel?

---

### Post by C S on 2012-03-29
> **derEremit said:**
> For anyone who's interested.
Touchpad is working as expected as of today. 16.03.2012
Updates in synaptics driver

Does anyone know how to get wireless drivers working with mainline kernel?

Wireless should work.  It's worked with every version of the kernel since I installed 11.10 onward to the current 12.04 beta.  Your wireless problem has to do with your particular configuration.

---

### Post by derEremit on 2012-03-29
> **C S said:**
> Wireless should work.  It's worked with every version of the kernel since I installed 11.10 onward to the current 12.04 beta.  Your wireless problem has to do with your particular configuration.

WLAN with 3.3
Got it working but have not posted since then.

Fix was first answer in this ask-ubuntu post
[http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working](http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working)

seems jockey installed bcm-kernel-source[LEFT][COLOR=#222222][FONT=Ubuntu Mono][/FONT][/COLOR][/LEFT] and added the blacklist for the driver provided by firmware-b43-installer[LEFT][COLOR=#222222][FONT=Ubuntu Mono][/FONT][/COLOR][/LEFT], and the driver installed by jockey was working on 3.2 but bcm-kernel-source can't compile on 3.3 mainline.

So, almost everything working.
Sometimes the MBA does not wake up from hibernate...

---

### Post by razorj7 on 2012-04-16
Hello Everyone,

So I am new to getting Ubuntu on a Mac (not Ubuntu in general) and I have been having a difficult time getting it to work. Here is what I have done so far:

Created 2 partitions on my drive:
[LIST=1]
[*]Mac partitions
[*]Ubuntu FAT32 (8G)
[*]Swap FAT32 (2G)
[/LIST]

Used Unetbootin to create a bootable USB with the 12.04 beta 2 64+mac

Used "dd" to place the USB stuff to the Ubuntu partition.

rebooted a few times

booted into the Ubuntu partition (I have refit) and was able to get started.

Here is my issue:

I have the infamous graphics issue which I have read is fixed using the "nomodeset." Where is this option so I can activate it? I have read you must press F6 at the SPLASH screen, however I have pressed F6 during the entire start up and can not get to this option. I get to the Unetbootin boot menu, then select "Try Ubuntu without installing" then the Ubuntu SPLASH screen comes on with the dots in the middle and that's it. Pressing F6 the entire time (holding it, or pressing several times) gets me nothing. Please help!

My second issue:

When attempting to Install Ubuntu onto the partition, I get an error that it cannot install on the partition I created. I have read that Ubuntu has an issue with installing onto the same partition as the installation CD image, how do I fix this?

Thank you for reading and please help!

Jesse

---

### Post by C S on 2012-04-18
> **razorj7 said:**
> 
I have the infamous graphics issue which I have read is fixed using the "nomodeset." Where is this option so I can activate it? I have read you must press F6 at the SPLASH screen, however I have pressed F6 during the entire start up and can not get to this option. I get to the Unetbootin boot menu, then select "Try Ubuntu without installing" then the Ubuntu SPLASH screen comes on with the dots in the middle and that's it. Pressing F6 the entire time (holding it, or pressing several times) gets me nothing. Please help!


Well, might as well eliminate the obvious first.  When you press F6, are you really pressing F6?  I mean, remember you have to hold down 'fn' first otherwise the MBA thinks you're pushing the "previous track" button.

> **razorj7 said:**
> 
When attempting to Install Ubuntu onto the partition, I get an error  that it cannot install on the partition I created. I have read that  Ubuntu has an issue with installing onto the same partition as the  installation CD image, how do I fix this?


I don't know where you got your instructions about 'dd'-ing to a partition and booting off it, but those instructions *should* (but maybe didn't) have said to create an extra partition for this very purpose.  In other words, partition your drive for Ubuntu installation, but make a extra, tiny partition big enough to hold the CD image (and maybe a bit bigger if you're going to use it as a LiveCD).  Then you install onto a regular partition (say you made one for root & home, and a second for swap, then you would install onto the first root & home partition).  After successful installation, you would then get rid of the extra one. 

Let me mention a couple things here.  1) Did you download the Mac iso?  It should have "mac" in the name.  2)  Are you using Lion?  I think there are extra problems installing Ubuntu alongside Lion since Lion boots differently and has a recovery partition too.

---

### Post by razorj7 on 2012-04-23
> **C S said:**
> I don't know where you got your instructions about 'dd'-ing to a partition and booting off it, but those instructions *should* (but maybe didn't) have said to create an extra partition for this very purpose.  In other words, partition your drive for Ubuntu installation, but make a extra, tiny partition big enough to hold the CD image (and maybe a bit bigger if you're going to use it as a LiveCD).  Then you install onto a regular partition (say you made one for root & home, and a second for swap, then you would install onto the first root & home partition).  After successful installation, you would then get rid of the extra one.

Thank you for your help! I finally was able to boot and install the Ubuntu 12.04 Beta 2 (the +mac one) onto my Air 3,2. However, I am now experiencing more issues within Ubuntu itself. Here is what's going on:

First off, I have no idea to actually fix the nomodeset graphics issue, please help? I used the infamous post-install script for the Air 4,2 that has been going around, but that was probably a terrible idea. Now when I boot into Ubuntu my mouse doesn't work and it won't detect my nVidia card even after I search for the restricted driver. So since I may have messed things up with the post-install script should I just do a fresh reinstall? Btw, it was the 11.10 Oneiric Ocelot post-install script for the Air 4,2. I have the Air 3,2 with 12.04 beta 2 mac version, and I have Lion on my Air.

Please Help!

Thank you everyone!

Jesse

---

### Post by Myon87 on 2012-06-09
Hi!
 
Running Ubuntu 12.04 on my MBA 3.2. Installation was a breeze and almost everything is mint! I want to thank everyone who makes ubuntu work so well on macs!
 
I have one annoying problem though. After a fresh boot, I can adjust brightness with the function keys and in the settings. After the lid is closed, however, I can not. Also the brightness is set at max, which burns my eyes :P
 
I have been looking through ask ubuntu and in the wiki. The only lead I got was that it might have something to do with /etc/acpi/lid.sh not working. But it is beyond my programing skills to figure out what might cause the problem.
 
Edit: Forgot to ask for help with this problem. Please help :P Does anyone else have the same problem as me, btw?

---

### Post by Dreamsorcerer on 2012-06-09
> **Myon87 said:**
> I have one annoying problem though. After a fresh boot, I can adjust brightness with the function keys and in the settings. After the lid is closed, however, I can not. Also the brightness is set at max, which burns my eyes :P

It's not the lid, it happens when you suspend. I have mine set to just switch off the backlight when the lid is closed, and it's fine then. It only has that problem when resuming from suspend. I think this is probably a bug in the Nouveau driver, I think they are still working on getting suspend to work perfectly with it.

You could try using the proprietary driver, but in my experience you can't change the brightness at all out-of-the-box. You can install it with ```
sudo apt-get install nvidia-current -y
``` and remove it again with ```
sudo apt-get remove nvidia-current
```

The only other problem I've seen with this release is that 3-finger click doesn't work for middle click.

---

### Post by Ptitphilou on 2012-06-19
Hi everyone,

I've installed Ubuntu 12.04 on my macbook air (model middle-2011), and I have my first issue. Yes, it is my first time on Linux, and everything is a little bit difficult... It concerns the keyboard : I've set it to "french (macintosh)", and I've got almost every touch working, but some not, including the at sign, the exclamation mark and some others... it's very incomfortable, does anyone knows a solution? I'm even ready to map it myself, but I've no idea how to do it.

My config :
MBA middle-2011
running Ubuntu 12.04 on VMWare Fusion 4

Thanks to anyone who could help

---

