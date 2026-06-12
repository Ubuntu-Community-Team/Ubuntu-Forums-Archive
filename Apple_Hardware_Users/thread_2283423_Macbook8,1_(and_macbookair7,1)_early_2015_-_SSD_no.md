---
title: "Macbook8,1 (and macbookair7,1) early 2015 - SSD not detected / NVMExpress issue?"
date: 2015-06-21
forum: Apple Hardware Users
---

### Post by eric78 on 2015-06-21
I'm attempting to install ubuntu on my macbook8,1 but SSD isn't detected. Could it be due to Apple's migration from SATA for NVMExpress for both the macbook (macbook8,1) and macbookair-11in (macbookair7,1)? or could this be an issue with the efi / uefi? Regardless, any ideas how to get the SSD working? 

Thread pertaining to macbookair7,1 (11in) having the same sort of problem:
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)

Assuming it has to do with nvmexpress, this page seems to indicate that either ubuntu already has support for nvmexpress or that it can be done with additional manual steps. The things that it instructs though i have no familiarity with - compiling kernels, and/or modifing a loader.conf file which appears to not be an ubuntu thing / possibly a freebsd thing? although this page is on ubuntu's documentation for 14.04, 14.10 and 15.04. So it's not clear to me if nvme support is already there in ubuntu but simply not working.
[http://manpages.ubuntu.com/manpages/trusty/man4/nvme.4freebsd.html](http://manpages.ubuntu.com/manpages/trusty/man4/nvme.4freebsd.html)
[http://manpages.ubuntu.com/manpages/trusty/man4/nvd.4freebsd.html](http://manpages.ubuntu.com/manpages/trusty/man4/nvd.4freebsd.html)

Separately this page indicates that Kernel 3.3 has support for nvme natively (or at least, the work has been done and is available?), with various back ports enabling it in older versions including to 2.6. Although it's not clear to me if ubuntu incorporated any of this. Ubuntu 14.04 and 14.10 are using Kernel 3.16, whereas ubuntu 14.04 uses Kernel 3.19.
[https://communities.intel.com/community/itpeernetwork/blog/2014/10/03/upgrade-a-nvme-capable-linux-kernel](https://communities.intel.com/community/itpeernetwork/blog/2014/10/03/upgrade-a-nvme-capable-linux-kernel)

Also, I had removed the CoreStorage partition to allow for more than two partitions on my ssd. This was in preparation for allowing Ubuntu to have a main and swap partitions alongside the original osx partition (3 in total). OSX continues to function fine after all of this. I only mention this in case it is relevant but I suspect it is not.
[http://apple.stackexchange.com/questions/167868/cant-make-more-than-two-partitions](http://apple.stackexchange.com/questions/167868/cant-make-more-than-two-partitions)

My system:
- Macbook (Retina, 12-in, Early 2015)
- 1.3GHz, 512GB
- A1534
- Macbook8,1

Overall Ubuntu macbook status on my system:
I tried ubuntu 14.04, and briefly 15.04 which seemed to have the same results. Notes below apply to 14.04 specifically though.

Things that work:
- Boot up / the os itself works fine.
- USB ethernet 

Things that don't work:
- SSD doesn't show up at all.
- keyboard doesn't work.
- touchpad doesn't work.
- sound doesn't work.
- wifi unconfirmed at the moment.

Note: I used a usb hub for external keyboard, mouse, usb-ethernet and bootstick.

I noticed a couple other macbook8,1 threads which i'll link here for reference, but there doesnt seem to be much activity on them at this time:
[http://ubuntuforums.org/showthread.php?t=2280212](http://ubuntuforums.org/showthread.php?t=2280212)
[http://askubuntu.com/questions/633237/macbook8-1-macbook-early-2015-keyboard-and-trackpad-dont-work-at-all](http://askubuntu.com/questions/633237/macbook8-1-macbook-early-2015-keyboard-and-trackpad-dont-work-at-all)

---

### Post by eric78 on 2015-06-28
Another thread I found for reference for anyone else debugging this issue:
[https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook](https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook)

---

### Post by JGrossholtz on 2015-07-22
Hello,

Have you been able to make some progress since you posted here ?

I posted on the openSuze Forum a "Test" to try to force linux to recognize the SSD. It did not worked for me but could you try and post here if it worked ?
[https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook/page2](https://forums.opensuse.org/showthread.php/507933-openSUSE-on-the-2015-Apple-12-Inch-Retina-MacBook/page2)

If I'm able to find a Linux 4.1 livecd anywhere soon I will try with it.

You said it could be related with the  UEFI, why do you think this ?

---

### Post by eric78 on 2015-07-26
No progress here. I did try the suggestion you made over on opensuse overriding the id to force linux to recognize it, didn't work. It also didn't corrupt my installations (osx on the ssd, nor mess up my usb-full-installed ubuntu disk) or cause any errors, which sort of leads me to believe i did it wrong?


Reference debug info copied below.

```

uname -a
Linux eric-sd 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

sudo lspci -vvxxxs 03:00.0
03:00.0 Mass storage controller: Apple Inc. Device 2001 (rev 01) (prog-if 02)
        Subsystem: Apple Inc. Device 2001
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 0
        Region 0: Memory at c1500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <32us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x4, ASPM L0s L1, Exit Latency L0s <1us, L1 <2us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Not Supported
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                         EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
        Capabilities: [100 v2] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [148 v1] Latency Tolerance Reporting
                Max snoop latency: 3145728ns
                Max no snoop latency: 3145728ns
00: 6b 10 01 20 06 00 10 00 01 02 80 01 40 00 00 00
10: 04 00 50 c1 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 6b 10 01 20
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 01 00 00
40: 01 50 03 00 08 00 00 00 00 00 00 00 00 00 00 00
50: 05 70 86 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 10 00 02 00 82 8b e8 07 10 28 19 00 42 cc 44 00
80: 43 01 42 10 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 10 08 00 00 00 04 00 00 06 00 00 00
a0: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

```
Command i tried:
echo "106b 2001" | sudo tee /sys/bus/pci/drivers/nvme/new_id

FYI this command took a minute or so to complete for whatever reason. But i didn't get any of the errors that you mention, and no system freezing but i also didn't try to do a heck of a lot before rebooting it.

Rebooted in the following ways and observed no difference:
- osx on ssd - still working.
- ubuntu installation usb stick - still doesnt detect the nvme ssd.
- ubuntu fully installed usb stick - looks the same as it did before.


I only mentioned UEFI because i had issues with efi/uefi recognizing my various usb boot disks, for example, a fully-installed ubuntu usb stick wasn't working. Eventually i got it working, forgot specifically what it was now though. Nothing specifically pointing to uefi as a cause of non-recognition of the ssd. It may very well not be relevant.

---

### Post by JGrossholtz on 2015-07-27
Hello Eric,

Thank you for you reply. It's interesting to see that you did not had the same behaviour than me. For me it did not took 1 minute, it freezed immediately so maybe there is something to work with what you did.

Did you had any message from the system after the echo command ?

Could you do a little   "$sudo dmesg -C" before the "echo". Then after you can try "dmesg" and "sudo lspci -vvxxxs 03:00.0" to get some feedback and paste it here.

It's also interesting to see that Apple did a patch last week for the Macbook pro SSD controler because of a bug. Maybe there will be an update for us too.

Thank you !

Julien

---

### Post by eric78 on 2015-08-01
Commands / output below, also again i observed the echo command taking approx 45 seconds to complete.

Also, where did you see the patch information on the pro's ssd?
```

$ sudo modprobe nvme
[sudo] password for eric: 
$ ls /sys/bus/pci/drivers/nvme/
bind  module  new_id  remove_id  uevent  unbind
$ sudo lspci -vvxxxs 03:00.0
03:00.0 Mass storage controller: Apple Inc. Device 2001 (rev 01) (prog-if 02)
        Subsystem: Apple Inc. Device 2001
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 0
        Region 0: Memory at c1500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <32us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x4, ASPM L0s L1, Exit Latency L0s <1us, L1 <2us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Not Supported
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                         EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
        Capabilities: [100 v2] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [148 v1] Latency Tolerance Reporting
                Max snoop latency: 3145728ns
                Max no snoop latency: 3145728ns
00: 6b 10 01 20 06 00 10 00 01 02 80 01 40 00 00 00
10: 04 00 50 c1 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 6b 10 01 20
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 01 00 00
40: 01 50 03 00 08 00 00 00 00 00 00 00 00 00 00 00
50: 05 70 86 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 10 00 02 00 82 8b e8 07 10 28 19 00 42 cc 44 00
80: 43 01 42 10 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 10 08 00 00 00 04 00 00 06 00 00 00
a0: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

$ sudo dmesg -C
$ echo "106b 2001" | sudo tee /sys/bus/pci/drivers/nvme/new_id
106b 2001
$ dmesg
[  136.279863] irq 16: nobody cared (try booting with the "irqpoll" option)
[  136.279872] CPU: 2 PID: 0 Comm: swapper/2 Not tainted 3.16.0-30-generic #40~14.04.1-Ubuntu
[  136.279875] Hardware name: Apple Inc. MacBook8,1/Mac-BE0E8AC46FE800CC, BIOS MB81.88Z.0164.B02.1503241252 03/24/2015
[  136.279877]  ffff880262992ca4 ffff88026ec83e58 ffffffff81762590 ffff880262992c00
[  136.279882]  ffff88026ec83e80 ffffffff810cd672 ffff880262992c00 0000000000000010
[  136.279886]  0000000000000000 ffff88026ec83ec0 ffffffff810cdbac 0000000000000000
[  136.279890] Call Trace:
[  136.279893]  <IRQ>  [<ffffffff81762590>] dump_stack+0x45/0x56
[  136.279906]  [<ffffffff810cd672>] __report_bad_irq+0x32/0xd0
[  136.279910]  [<ffffffff810cdbac>] note_interrupt+0x24c/0x2a0
[  136.279914]  [<ffffffff810cb29e>] handle_irq_event_percpu+0xae/0x1a0
[  136.279917]  [<ffffffff810cb3cd>] handle_irq_event+0x3d/0x60
[  136.279921]  [<ffffffff810ce771>] handle_fasteoi_irq+0x81/0x150
[  136.279927]  [<ffffffff810155ee>] handle_irq+0x1e/0x30
[  136.279931]  [<ffffffff8176dabf>] do_IRQ+0x4f/0xf0
[  136.279936]  [<ffffffff8176b96d>] common_interrupt+0x6d/0x6d
[  136.279937]  <EOI>  [<ffffffff815fb8a2>] ? cpuidle_enter_state+0x52/0xc0
[  136.279947]  [<ffffffff815fb898>] ? cpuidle_enter_state+0x48/0xc0
[  136.279952]  [<ffffffff815fb9c7>] cpuidle_enter+0x17/0x20
[  136.279957]  [<ffffffff810b528d>] cpu_startup_entry+0x31d/0x450
[  136.279961]  [<ffffffff8104526d>] start_secondary+0x21d/0x2e0
[  136.279963] handlers:
[  136.279969] [<ffffffffc048b5f0>] nvme_irq [nvme]
[  136.279972] Disabling IRQ #16
[  195.662642] nvme: probe of 0000:03:00.0 failed with error -4


$ sudo lspci -vvxxxs 03:00.0
03:00.0 Mass storage controller: Apple Inc. Device 2001 (rev 01) (prog-if 02)
        Subsystem: Apple Inc. Device 2001
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx+
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at c1500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <32us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x4, ASPM L0s L1, Exit Latency L0s <1us, L1 <2us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR+, OBFF Not Supported
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                         EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
        Capabilities: [100 v2] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt+ UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 0f, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [148 v1] Latency Tolerance Reporting
                Max snoop latency: 3145728ns
                Max no snoop latency: 3145728ns
00: 6b 10 01 20 02 00 18 08 01 02 80 01 40 00 00 00
10: 04 00 50 c1 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 6b 10 01 20
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 01 00 00
40: 01 50 03 00 08 00 00 00 00 00 00 00 00 00 00 00
50: 05 70 86 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 10 00 02 00 82 8b e8 07 10 28 1b 00 42 cc 44 00
80: 43 01 42 10 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 10 08 00 00 00 04 00 00 06 00 00 00
a0: 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

$

```

---

### Post by PaulW2U on 2015-08-02
eric78, please use code tags for terminal output as they will improve the readability of your posts.

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by Lance_Zhou on 2015-08-13
Same problem here, glad I'm not the only one. I have the lowest spec version of the 11" mba7,1. I think nvme is supposed to be on /dev/nvme* instead of /dev/sd*, and no distro has recognised those partitions so far.

---

### Post by craic on 2016-02-03
I also have the same problem with an 11" Macbook Air 7,1. Has anyone found a solution yet? It looks like kernel 4.4 will have more support for these drives.

---

### Post by Vinodh Moodley on 2016-03-27
> **craic said:**
> I also have the same problem with an 11" Macbook Air 7,1. Has anyone found a solution yet? It looks like kernel 4.4 will have more support for these drives.

I tried Ubuntu 16.04 LTS Beta 2 on my 12" MacBook and the keyboard and trackpad still doesn't work. Seems like kernel 4.4 doesn't help much. 

Anyone here have any ideas on what to do to fix this?

---

