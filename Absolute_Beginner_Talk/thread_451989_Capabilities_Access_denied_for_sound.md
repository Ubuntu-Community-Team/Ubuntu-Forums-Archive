---
title: "Capabilities: Access denied for sound"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by lunaticHIGH on 2007-05-22
- I installed 7.04 a couple days ago. 1st live session played sound. 
Installed the system. no sound. 
Just booted from LIVE CD(ready to reinstall), and theres no sound on the LIVE version. 

Heres a list of hardware: 

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: [COLOR="DarkOrange"]Elitegroup Computer Systems Unknown device 0a14[/COLOR]
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at d800 [size=256]
        I/O ports at d400 [size=64]
        Capabilities: <access denied>

00:0b.0 Multimedia audio controller: [COLOR="DarkOrange"]Creative Labs SB Live! EMU10k1 (rev 07)[/COLOR]
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 64, IRQ 12
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:0b.1 Input device controller: [COLOR="DarkOrange"]Creative Labs SB Live! Game Port (rev 07)[/COLOR]
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dc00 [size=8]
        Capabilities: <access denied>

Im consfused as to why the 1st LIVE session would work with sound, but the 2nd wouldn't. (btw, i just booted into XP before this, and all sound was working). 

Thanks for any help.

---

### Post by icechen1 on 2007-05-22
what you get when you do:
> lsmod
```
 /etc/init.d/alsasound status
```
```
lspci
```

---

### Post by lunaticHIGH on 2007-05-22
when i type 'lsmod' = 

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
lp                     12452  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
fuse                   46612  1 
ipv6                  268704  8 
snd_mpu401              9256  0 
snd_mpu401_uart         9472  1 snd_mpu401
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  1 snd_emu10k1_synth
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  3 snd_seq_oss,snd_seq_virmidi,snd_seq_midi
snd_rawmidi            25472  4 snd_mpu401_uart,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
analog                 12832  0 
snd_seq                52592  9 snd_seq_dummy,snd_seq_oss,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_intel8x0           34204  1 
snd_ac97_codec         98336  2 snd_emu10k1,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23684  3 snd_emu10k1,snd_seq,snd_pcm
snd_seq_device          9100  8 snd_seq_dummy,snd_seq_oss,snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  18 snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_rawmidi,snd_seq,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_emu10k1,snd_intel8x0,snd_pcm
i2c_sis96x              6532  0 
emu10k1_gp              4736  0 
i2c_sis630              8588  0 
gameport               16520  3 analog,emu10k1_gp
i2c_core               22784  3 i2c_ec,i2c_sis96x,i2c_sis630
shpchp                 34324  0 
sis_agp                 9604  1 
pci_hotplug            32576  1 shpchp
agpgart                35400  1 sis_agp
af_packet              23816  6 
evdev                  11008  3 
tsdev                   8768  0 
squashfs               49028  1 
loop                   17800  2 
unionfs                74020  1 
nls_cp437               6784  1 
isofs                  36284  1 
ext3                  133128  0 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  2 
8139too                27648  0 
pata_sis               14220  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  1 libata
usbhid                 26592  0 
hid                    27392  1 usbhid
sis5513                14856  0 [permanent]
floppy                 59524  0 
8139cp                 25088  0 
sis900                 24704  0 
mii                     6528  3 8139too,8139cp,sis900
generic                 5124  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  3 usbhid,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


When i type 'lspci"

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by icechen1 on 2007-05-22
Did you check the sound volume and it is not muted and
the output of:
```
 /etc/init.d/alsasound status
```

---

### Post by icechen1 on 2007-05-22
Oh also
you will get
> Capabilities: <access denied>
but if you add sudo in front of the command where you got
> 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
Subsystem: Elitegroup Computer Systems Unknown device 0a14
Flags: bus master, medium devsel, latency 64, IRQ 11
I/O ports at d800 [size=256]
I/O ports at d400 [size=64]
Capabilities: <access denied>

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
Subsystem: Creative Labs SBLive! 5.1 Model SB0100
Flags: bus master, medium devsel, latency 64, IRQ 12
I/O ports at cc00 [size=32]
Capabilities: <access denied>

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
Subsystem: Creative Labs Gameport Joystick
Flags: bus master, medium devsel, latency 64
I/O ports at dc00 [size=8]
Capabilities: <access denied>,what it says?

---

### Post by lunaticHIGH on 2007-05-22
ubuntu@ubuntu:~$  /etc/init.d/alsasound status
bash: /etc/init.d/alsasound: No such file or directory

As a reminder: im in the Live Session right now.

---

### Post by lunaticHIGH on 2007-05-22
sudo lspci -v  

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 64, IRQ 12
        I/O ports at cc00 [size=32]
        Capabilities: [dc] Power Management version 1

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dc00 [size=8]
        Capabilities: [dc] Power Management version 1

---

### Post by Nikron on 2007-05-22
Check if your in the audio group, if your not, add yourself to it.(command to check groups is 'id')

---

### Post by lunaticHIGH on 2007-05-22
ubuntu@ubuntu:~$ id
uid=999(ubuntu) gid=999(ubuntu) groups=4(adm),20(dialout),24(cdrom),25(floppy)[COLOR="DarkOrange"],29(audio),[/COLOR]30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),999(ubuntu)
ubuntu@ubuntu:~$ 

looks like i am

---

### Post by lunaticHIGH on 2007-05-22
What could possibly cuase sound to immediately work in 1 live session, then not in the next?

---

### Post by merkki on 2007-10-29
I have exactly the same problem. Sometimes it works sometimes it doesn't. Have u found a solution? 

Note, with me it never works straight off. When I type lspci -v and sudo lspvi -v and alsamixer randomly then I notice at some point that the some channels on alsamixer are muted that weren't earlier muted during the session, and when I unmute the sound starts working. Really weird!

---

### Post by disarmm on 2008-05-30
I ended up going into the Volume control, go to edit at the top and go into preferences. Then scroll down and select everything in that list.

close out and go into the switches tab in the volume control and turn off external amplifier and anything else thats in that list. Sometimes the microphone capture wont let you de-select it but dont worry, once you unmute and deselect everything else it'll uncheck itself. Then go to playback and unmute everything. Then it should work and you can go back and mute what you want and it will still work.

This worked in both the live boot and after i installed it.


This is the device is use:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Rioworks Unknown device 203a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

