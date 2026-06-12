---
title: "how to view shutdown log file"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by xpan on 2007-01-07
hi,

I would like to know if there is any way for me to view the messages thrown out during shutdown. 

I tried recovery mode and saw that there are errors but I couldn't find the log file these errors are saved.

---

### Post by bapoumba on 2007-01-07
Hi,
you may want to try :
```
shutdown -h now > shutdown.log
```
and look what's logged in the file.

---

### Post by xpan on 2007-01-07
thanks a lot. 

The problem is that the errors appear just sometimes. So I will have to shutdown that way every time. I thought that there should be a way for capturing shutdown messages automatically. 

for now I will keep shutting down the way you suggested :)

---

### Post by bapoumba on 2007-01-07
Well, may be have a look in **/var/log/**, in particular syslog.0 file.

---

### Post by xpan on 2007-01-08
I am sorry but shutdown -h now > shutdown.log does not work. Well, it might work but the shutdown.log is an empty file.

I also tried to browse through the syslog.0 file but didn't find any errors...

the problem is that most of the times when I shut-down my computer stops responding after displaying a screen full of garbage and I have to hold the power-button for 5 seconds...

So I need to find out what is wrong. I think the problem is caused while trying to stop the X server, but I am not sure.

---

### Post by bapoumba on 2007-01-08
I'm not an expert in x-server :/
You may want to post your video card type, if you are running proprietary drivers, beryl & Co ... So that others can help you.
What do you call garbage ? Is it error messages ?

---

### Post by shanepardue on 2007-01-08
I have the same problem! I have an integrated intel video card on my hp nx6310 laptop. I'm running the i810 driver and it's an intel 915.

---

### Post by Bachstelze on 2007-01-08
Those messages are called the "kernel ring buffer", they can be viewed with *dmesg*.

---

### Post by xpan on 2007-01-08
I did view the dmesg... and here it goes...

> 
[17179594.576000] EXT3 FS on hda2, internal journal
[17179594.760000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179594.764000] NTFS-fs warning (device hda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17179594.812000] NTFS volume version 3.1.
[17179594.952000] r8169: eth0: link up
[17179596.172000] NET: Registered protocol family 17
[17179597.448000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179599.404000] ACPI: AC Adapter [ADP1] (on-line)
[17179599.628000] ACPI: Battery Slot [BAT0] (battery present)
[17179599.644000] ACPI: Power Button (FF) [PWRF]
[17179599.644000] ACPI: Lid Switch [LID0]
[17179599.644000] ACPI: Sleep Button (CM) [SLPB]
[17179599.704000] ACPI: ACPI Dock Station Driver 
[17179599.780000] ibm_acpi: ec object not found
[17179599.808000] pcc_acpi: loading...
[17179599.912000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179599.912000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179600.180000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179600.180000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[17179600.180000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
[17179600.180000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
[17179600.180000] cpu_init done, current fid 0xa, vid 0xa
[17179601.592000] NET: Registered protocol family 10
[17179601.592000] lo: Disabled Privacy Extensions
[17179601.592000] IPv6 over IPv4 tunneling driver
[17179602.132000] [fglrx] Maximum main memory to use for locked dma buffers: 1171 MBytes.
[17179602.132000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179602.160000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 66
[17179603.976000] [fglrx] total      GART = 134217728
[17179603.976000] [fglrx] free       GART = 118226944
[17179603.976000] [fglrx] max single GART = 118226944
[17179603.976000] [fglrx] total      LFB  = 127889408
[17179603.976000] [fglrx] free       LFB  = 119697408
[17179603.976000] [fglrx] max single LFB  = 119697408
[17179603.976000] [fglrx] total      Inv  = 0
[17179603.976000] [fglrx] free       Inv  = 0
[17179603.976000] [fglrx] max single Inv  = 0
[17179603.976000] [fglrx] total      TIM  = 0
[17179604.640000] apm: BIOS not found.
[17179608.208000] ttyS1: LSR safety check engaged!
[17179610.508000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179611.764000] Bluetooth: Core ver 2.8
[17179611.764000] NET: Registered protocol family 31
[17179611.764000] Bluetooth: HCI device and connection manager initialized
[17179611.764000] Bluetooth: HCI socket layer initialized
[17179611.848000] Bluetooth: L2CAP ver 2.8
[17179611.848000] Bluetooth: L2CAP socket layer initialized
[17179611.900000] Bluetooth: RFCOMM socket layer initialized
[17179611.900000] Bluetooth: RFCOMM TTY layer initialized
[17179611.900000] Bluetooth: RFCOMM ver 1.7
[17179612.320000] eth0: no IPv6 routers present
[17179660.852000] input: AT Translated Set 2 keyboard as /class/input/input3
[17179677.440000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179969.356000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17180375.860000] APIC error on CPU0: 00(40)
[17183226.712000] APIC error on CPU0: 40(40)
[17183449.644000] APIC error on CPU0: 40(40)
[17184988.000000] atkbd.c: Unknown key pressed (translated set 2, code 0xb3 on isa0060/serio0).
[17184988.000000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[17184988.040000] atkbd.c: Unknown key released (translated set 2, code 0xb3 on isa0060/serio0).
[17184988.040000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[17184988.176000] atkbd.c: Unknown key pressed (translated set 2, code 0xb3 on isa0060/serio0).
[17184988.176000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[17184988.220000] atkbd.c: Unknown key released (translated set 2, code 0xb3 on isa0060/serio0).
[17184988.220000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[17185560.048000] APIC error on CPU0: 40(40)


so i guess the problem is with the APIC. I am going to try to shut the service during startup... any consequences if I disable it?

---

### Post by shanepardue on 2007-01-08
I'm not sure on that service, but let me know if you find out anything about this. Are you using Kubuntu?

---

### Post by xpan on 2007-01-09
No, I am using Ubuntu Edgy. I just had my Phoenix Bios updated to the newest version (dl-ed from Acer's Support site).

I 'll see what can I do. It seems that a lot of people have the same problems caused by faulty bios (maybe adjusted to work with windows... i really don't know)

---

