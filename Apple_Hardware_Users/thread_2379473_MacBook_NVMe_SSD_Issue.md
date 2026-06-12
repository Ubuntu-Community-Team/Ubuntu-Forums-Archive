---
title: "MacBook NVMe SSD Issue"
date: 2017-12-05
forum: Apple Hardware Users
---

### Post by penguinemac on 2017-12-05
I have a 2015 Macbook with an integrated 256gig SSD that has stopped working apparently due to the failing SSD. I've been able to boot into a live USB thumb drive in an attempt to try to get the failed drive to mount and hopefully recover some data using tools such as testdisk or ddrescue etc. 

The MacBook seems to work fine within the Ubuntu live environment with the exception of the SSD not being properly detected or mounted. The output for dmesg shows the following:

```

[14329.580522] nvme nvme0: pci function 0000:03:00.0
[14329.580672] nvme nvme0: detected Apple NVMe controller, set queue depth=2 to work around controller resets
[14345.130062] nvme nvme0: Device not ready; aborting initialisation
[14345.130072] nvme nvme0: Removing after probe failure status: -19

```

Strangely however lspci seems to show the device being detected properly:

```

03:00.0 Mass storage controller [0180]: Apple Inc. PCI Express SSD [106b:2001] (rev 01)

```

lshw also seems to list the device however shows storage as "UNCLAIMED"

```

        *-pci:3
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:c1500000-c15fffff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: PCI Express SSD
                vendor: Apple Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:c1500000-c1501fff

```

I've tried assigning the device with "echo 106b 2001 > /sys/bus/pci/drivers/nvme/new_id" however get the following error:

```

bash: echo: write error: File exists

```

Below is also the output for this device using lshw --short:

```

H/W path                     Device     Class          Description
==================================================================
/0/100/1c.4/0                           storage        PCI Express SSD

```

Below is the output for lspci -vvxxxs 03:00.0:

```

03:00.0 Mass storage controller: Apple Inc. PCI Express SSD (rev 01) (prog-if 02)
    Subsystem: Apple Inc. PCI Express SSD
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 16
    NUMA node: 0
    Region 0: Memory at c1500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
        Address: 00000000fee00378  Data: 0000
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <32us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 25.000W
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x4, ASPM L0s L1, Exit Latency L0s <1us, L1 <2us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp+
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Not Supported
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [100 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [148 v1] Latency Tolerance Reporting
        Max snoop latency: 3145728ns
        Max no snoop latency: 3145728ns
    Kernel modules: nvme
00: 6b 10 01 20 02 00 10 00 01 02 80 01 40 00 00 00
10: 04 00 50 c1 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 6b 10 01 20
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 01 00 00
40: 01 50 03 00 08 00 00 00 00 00 00 00 00 00 00 00
50: 05 70 86 00 78 03 e0 fe 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 10 00 02 00 82 8b e8 07 10 28 19 00 42 cc 44 00
80: 42 01 42 10 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 10 08 00 00 00 04 00 00 06 00 00 00
a0: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

```

At this point I'm not sure if the device is truly not functioning properly (since it was not detected by macOS, or if there was some other kind of issue such as a corrupt partition etc. The device seems to be recongized by Ubuntu however I cannot get it to be detected properly or to mount.

I have some critical data on this device that I really need to try to access. Are there any additional steps I can take to troubleshoot this issue or try to get the device assigned and mounted? Any help would be greatly appreciated.

Thanks!

---

### Post by QIII on 2017-12-05
Moved to Apple Hardware Users for a better fit.

---

### Post by oldfred on 2017-12-05
What version of Ubuntu? Some older kernels did not have NVMe drivers.
[https://ubuntuforums.org/showthread.php?t=2274095](https://ubuntuforums.org/showthread.php?t=2274095)

And many PC users have had to have both vendors' UEFI and SSD's firmware updated to make it work.

---

### Post by penguinemac on 2017-12-06
Thanks for the quick reply. I'm currently using a 17.10 live USB with the following kernel:

4.13.0-17-generic

---

### Post by penguinemac on 2017-12-07
Bump

---

### Post by penguinemac on 2017-12-08
I've been trying to use smartctl to query items in the /dev folder however I don't believe there is a device listed that is associated with PCI device 03:00.0:


03:00.0 Mass storage controller [0180]: Apple Inc. PCI Express SSD [106b:2001] (rev 01)


I'm trying to figure out if the device is possible listed under the wrong device type. Is there anyway to force an identified piece of hardware to associated with an entry within /dev?

---

### Post by oldfred on 2017-12-08
Did you check to see if there was a firmware update for your SSD?

---

