---
title: "no sound...after doing a dual boot"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by famleon on 2008-02-01
I installed vista and Ubuntu 7.10, in a dual boot, the Ubuntu is the Ultimate edition 1.6, but the sound card works fine in Vista, but not in ubuntu, any Idea or solution? I tried to search a solution and google it, but no answers founded, is a compaq 568LA, any idea someone? any help will be welcome.buntu.com andrsion, i  had sound, but after I installed the other ultimate version, then the issued began

Thanks

---

### Post by famleon on 2008-02-01
also these are the results

tavo@laptop:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at 1800 [size=8]
        Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: 50000000-500fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 4: I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 4: I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 17
        Region 4: I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at 1890 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 4: I/O ports at 18a0 [size=32]

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1364
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at 50000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at 2000 [size=256]
        Region 1: Memory at d0100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by deadgobby on 2008-02-01
Please open up the terminal and input this command

aplay --list-devices 



Gobby

---

### Post by famleon on 2008-02-01
Also, I reinstalled the alsa package

---

### Post by famleon on 2008-02-01
> **deadgobby said:**
> Please open up the terminal and input this command

aplay --list-devices 



Gobby

tavo@laptop:~$ aplay --list-devices 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by famleon on 2008-02-04
OK, I got tired...I reinstalled Ubuntu...I guess that was the easiest solution....I know...dummy, but fix the issue

---

### Post by Blutack on 2008-02-04
Next time, make sure it isn't muted first ;)

---

### Post by famleon on 2008-02-06
I check it, how do you know was muted? because I double check it

---

### Post by famleon on 2008-02-19
OK, here we go again, I used to have sound and now no sound at all, why? they answer me to be sure is not muted, and it is not muted, how do I know is this is muted? any other solution?
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: Conexant Digital [Conexant Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

---

### Post by GregA on 2008-02-19
A couple suggestions to try:

1.   Open in a text editor:   /etc/modprobe.d/snd-hda-intel . . . . and put #'s at the start of one or both lines.

Then save, restart your system and see if you have sound.

2.   Put "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base".

(note, what I mean by "put" is add a new line with the above text in the file "alsa-base") 

Then save, restart your system and see if you have sound.

Please report back, so other options can be tried if the above don't work.

---

### Post by famleon on 2008-02-19
OK, I am really sorry but can you give a more detailed answer, because I am new on this and  am quite lost regarding the instructions. I really appreciate more detail on this,  thanks

---

### Post by whiteowl on 2008-02-19
What is meant, is that in Linux, you can update your system (ubuntu) by editing (changing) certain "text" files.

These text files are located all over the file system, but you need to enter a command in a terminal such as:

"sudo kate /etc/next directory/next directory/name_of_file".   Of course, the next directory and name of file should be the actual names of where the text file is located.   This is called the file "path".   Like a roadmap.

Anyway, the editor, in this case, "kate", will open the file you specified.    Then you make the specific changes as listed by the forum members.   For example, by adding a pound symbol "#" - this is telling ubuntu to "ignore" (not process) that line.   This is also called "commenting out" a line - because many developers have comments in programs, that start with a #.

Hope this is a little clearer, but if not, you may also want to look at Linux's that use more graphical tools than ubuntu does such as Suse or Mandriva, in order to run "wizards" to fix video or sound issues.

---

### Post by Acglaphotis on 2008-02-19
Hey, if you are on a HP laptop (or have a MCP51 nvidia - or something alike, just try shutting off your laptop, unplug the power jack and let it boot to ubuntu without it.

---

### Post by famleon on 2008-02-19
did it and still no sound, BTW this is a compaq system so is HP, the funny thing is that the sound was working and still in vista works, so I am getting tired of this...

---

### Post by famleon on 2008-02-19
> **whiteowl said:**
> What is meant, is that in Linux, you can update your system (ubuntu) by editing (changing) certain "text" files.

These text files are located all over the file system, but you need to enter a command in a terminal such as:

"sudo kate /etc/next directory/next directory/name_of_file".   Of course, the next directory and name of file should be the actual names of where the text file is located.   This is called the file "path".   Like a roadmap.

Anyway, the editor, in this case, "kate", will open the file you specified.    Then you make the specific changes as listed by the forum members.   For example, by adding a pound symbol "#" - this is telling ubuntu to "ignore" (not process) that line.   This is also called "commenting out" a line - because many developers have comments in programs, that start with a #.

Hope this is a little clearer, but if not, you may also want to look at Linux's that use more graphical tools than ubuntu does such as Suse or Mandriva, in order to run "wizards" to fix video or sound issues.

thanks for the data, but still I am not sure where to add the info, I mean, which is the file that i need to correct....thanks

---

### Post by Acglaphotis on 2008-02-19
Just go to Applications>Accesories>Terminal, and enter the commands. It's not too hard when you get the hang of it : ).

---

### Post by famleon on 2008-02-19
> **Acglaphotis said:**
> Hey, if you are on a HP laptop (or have a MCP51 nvidia - or something alike, just try shutting off your laptop, unplug the power jack and let it boot to ubuntu without it.

OK, OK, OK you were right...funny, I did it again (without oopss...) but the only difference is that I get into windows vista and then restart the computer and now I have sound...OK, that is weird...but worked out, Thanks

---

### Post by famleon on 2008-02-19
> **Acglaphotis said:**
> Just go to Applications>Accesories>Terminal, and enter the commands. It's not too hard when you get the hang of it : ).

actually I know how to do it, but I was not able to find the file that was mentioned that need to be changed..anyway I have sound..cool

---

