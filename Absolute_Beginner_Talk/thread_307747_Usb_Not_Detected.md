---
title: "Usb Not Detected"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by tribeone on 2006-11-27
Does anyone know how to get the usb reader ( ECS K7VTA3 rev 8) for this MB to work with ubuntu? This is what I have done so far:

lsmod returns this
```

:~$ lsmod
Module Size Used by
rfcomm 40216 0
l2cap 26244 5 rfcomm
bluetooth 50020 4 rfcomm,l2cap
ppdev 9220 0
cpufreq_userspace 4696 0
cpufreq_stats 5636 0
freq_table 4740 1 cpufreq_stats
cpufreq_powersave 1920 0
cpufreq_ondemand 6428 0
cpufreq_conservative 7332 0
video 16260 0
tc1100_wmi 6916 0
sony_acpi 5644 0
pcc_acpi 12416 0
hotkey 11556 0
dev_acpi 11140 0
container 4608 0
button 6672 0
acpi_sbs 19980 0
battery 9988 1 acpi_sbs
ac 5252 1 acpi_sbs
i2c_acpi_ec 5120 1 acpi_sbs
ipv6 265728 6
dm_mod 58936 1
md_mod 72532 0
af_packet 22920 2
lp 11844 0
snd_seq_dummy 3844 0
snd_seq_oss 33536 0
snd_seq_midi 9376 0
snd_seq_midi_event 7552 2 snd_seq_oss,snd_seq_midi
snd_seq 51984 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx 28824 2
gameport 15496 1 snd_via82xx
snd_ac97_codec 93216 1 snd_via82xx
snd_ac97_bus 2304 1 snd_ac97_codec
snd_pcm_oss 53664 0
snd_mixer_oss 18688 2 snd_pcm_oss
snd_pcm 89864 3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer 25220 2 snd_seq,snd_pcm
snd_page_alloc 10632 2 snd_via82xx,snd_pcm
snd_mpu401_uart 7808 1 snd_via82xx
snd_rawmidi 25504 2 snd_seq_midi,snd_mpu401_uart
snd_seq_device 8716 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
floppy 62148 0
snd 55268 13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu40 1_uart,snd_rawmidi,snd_seq_device
soundcore 10208 2 snd
tsdev 8000 0
nvidia 4551028 0
parport_pc 35780 1
i2c_viapro 8980 0
psmouse 36100 0
i2c_core 21904 3 i2c_acpi_ec,nvidia,i2c_viapro
parport 36296 3 ppdev,lp,parport_pc
via_ircc 26900 0
via_rhine 23940 0
serio_raw 7300 0
mii 5888 1 via_rhine
shpchp 45632 0
pci_hotplug 29236 1 shpchp
pcspkr 2180 0
irda 187068 1 via_ircc
crc_ccitt 2304 1 irda
rtc 13492 0
via_agp 9856 1
agpgart 34888 2 nvidia,via_agp
evdev 9856 1
ext3 135816 1
jbd 58772 1 ext3
ide_generic 1536 0
ide_cd 33028 0
cdrom 38560 1 ide_cd
ide_disk 17664 3
via82cxxx 9988 0 [permanent]
generic 5124 0
thermal 13576 0
processor 23360 1 thermal
fan 4868 0
capability 5000 0
commoncap 7296 1 capability
vga16fb 13704 1
vgastate 10368 1 vga16fb
fbcon 42784 72
tileblit 2816 1 fbcon
font 8320 1 fbcon
bitblit 6272 1 fbcon
softcursor 2304 1 bitblit

lsusb returns
nothing except command line

dmesg | tail returns this

~$ dmesg | tail
[17179608.268000] NET: Registered protocol family 31
[17179608.268000] Bluetooth: HCI device and connection manager initialized
[17179608.268000] Bluetooth: HCI socket layer initialized
[17179608.344000] Bluetooth: L2CAP ver 2.8
[17179608.344000] Bluetooth: L2CAP socket layer initialized
[17179608.344000] Bluetooth: RFCOMM socket layer initialized
[17179608.344000] Bluetooth: RFCOMM TTY layer initialized
[17179608.344000] Bluetooth: RFCOMM ver 1.7
[17179624.704000] eth0: no IPv6 routers present
[17179913.732000] ibm_acpi: ec object not found

$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:09.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

~$ sudo modprobe uhci
FATAL: Module uhci not found.

sudo modprobe usbcore return command line only

~$ dmesg | tail
[17179608.344000] Bluetooth: L2CAP socket layer initialized
[17179608.344000] Bluetooth: RFCOMM socket layer initialized
[17179608.344000] Bluetooth: RFCOMM TTY layer initialized
[17179608.344000] Bluetooth: RFCOMM ver 1.7
[17179624.704000] eth0: no IPv6 routers present
[17179913.732000] ibm_acpi: ec object not found
[17210164.108000] cdrom: This disc doesn't have any tracks I recognize!
[17210696.652000] scsi: unknown opcode 0x01
[17211257.148000] usbcore: registered new driver usbfs
[17211257.148000] usbcore: registered new driver hub
```

---

### Post by klayn on 2006-11-28
Not exactly, but maybe this can help diagnose your problem a little better. First, unplug your device completely. In terminal, type

```
ls /dev/ > /tmp/before
```

Then, plug your device in and type

```
ls /dev/ > /tmp/after
```

Then type

```
diff /tmp/before /tmp/after
```

This will give you the difference between your devices before you plugged it in and after. If it lists something, then you know your device is detected (and even what name it's assigned). If nothing is listed, then you know it's not detected at all. I'm not really sure where to go from there, except maybe trying to mount the disk if it's detected?

Hope this helps...

---

### Post by tribeone on 2006-11-28
YAHHOOOOOOO!!!  I went into BIOS and found that my usb and onboard modem was not enabled they were both disabled. All I had to do was enable them restart pc and viola now I have 2 working ethernet cards and get this

```
[CODE]~$ lshw
WARNING: you should run this program as super-user.
tribeone
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1850MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: d0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:d0000000-d7ffffff
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
```

---

