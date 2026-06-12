---
title: "Memory speed and type from command line"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by fluzao on 2007-10-23
Hi,

Is there a way to check memory speed and type **from the command line** (i.e. whether it is DDR 400/333/266/200)?

Thanks in advance.

---

### Post by Vansinnesvisan on 2007-10-23
Try lshw. You will likely need to install it from Synaptic, I doubt it comes installed by default. 

More info on it [here]("http://ezix.org/project/wiki/HardwareLiSter").

---

### Post by fluzao on 2007-10-23
> **Vansinnesvisan said:**
> Try lshw. You will likely need to install it from Synaptic, I doubt it comes installed by default. 

More info on it [here]("http://ezix.org/project/wiki/HardwareLiSter").

Thanks. It turned out that lshw was already installed. It is probably a default on Gutsy, as I just did a clean install and I got the following message:

```
Reading state information... Done
lshw is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But I still don't manage to get the info I needed i.e. speed/type of RAM.

```
$ sudo lshw -C MEMORY
  *-firmware
       description: BIOS
       vendor: Phoenix Technologies, LTD
       physical id: 0
       version: 6.00 PG (11/16/2004)
       size: 128KB
       capacity: 448KB
       capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 8
       slot: Internal Cache
       size: 128KB
       capacity: 128KB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: 9
       slot: External Cache
       size: 256KB
       capacity: 256KB
       capabilities: synchronous external write-back
  *-memory
       description: System Memory
       physical id: 1a
       slot: System board or motherboard
       size: 512MB
       capacity: 2GB
     *-bank:0
          description: DIMM
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 512MB
     *-bank:1
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1

```

Removing the -C MEMORY option does not help either.

Nice to learn about this lshw package, though. Thanks a lot, Vansinnesvisan.

---

### Post by dca on 2007-10-23
Only thing to do is consult the manufacturer's website on the internet and track pieces installed...

---

### Post by NJC on 2007-10-23
what about running the memory test off of the Live CD? I know it gives xfer speed for L1/2 cache and I'm sure it does it for ram too.

---

### Post by bapoumba on 2007-10-23
```
sudo dmidecode
```
Then find the relevant info.

---

### Post by fluzao on 2007-10-23
> **bapoumba said:**
> ```
sudo dmidecode
```
Then find the relevant info.

Thanks, bapoumba. Turns out that both type and speed are unknown:

```
Handle 0x001B, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001A
        Error Information Handle: Not Provided
        Total Width: Unknown
        Data Width: Unknown
        Size: 512 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

```

In case you are wondering, I have no physical access to the machine. I am trying to figure out this information through a SSH terminal connection.

---

### Post by bapoumba on 2007-10-23
```
Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM 1
        Bank Connections: 0 1
        Current Speed: 60 ns
        Type: DIMM SDRAM
        Installed Size: 256 MB (Double-bank Connection)
        Enabled Size: 256 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM 2
        Bank Connections: 2 3
        Current Speed: 60 ns
        Type: DIMM SDRAM
        Installed Size: 256 MB (Double-bank Connection)
        Enabled Size: 256 MB (Double-bank Connection)
        Error Status: OK
```
I have the speeds show up in Memory Module Information.
I do not know enough about the ssh protocol, and why it would not work..

---

### Post by nutz on 2008-01-30
That command indicates that my shiznitz is running at 2048mhz?

Handle 0x001B, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 2 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001B
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: DDR2
        Type Detail: None
       ** Speed: 2048 MHz** (0.5 ns)
        Manufacturer: 7F7F7F7F7F020000
        Serial Number: 00000000
        Asset Tag: None
        Part Number: PDC24G6400ELK

Handle 0x001D, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001B
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A1
        Bank Locator: Bank2/3
        Type: DDR2
        Type Detail: None
        **Speed: 2048 MHz** (0.5 ns)
        Manufacturer: 7F7F7F7F7F020000
        Serial Number: 00000000
        Asset Tag: None
        Part Number: PDC24G6400ELK

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001B
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A2
        Bank Locator: Bank4/5
        Type: DDR2
        Type Detail: None
        **Speed: 2048 MHz (0.5 ns)**
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x001F, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001B
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A3
        Bank Locator: Bank6/7
        Type: DDR2
        Type Detail: None
        **Speed: 2048 MHz (0.5 ns)**
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

---

