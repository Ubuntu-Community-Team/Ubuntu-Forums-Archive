---
title: "Flash Drive not Detected"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-02-07
I just bought a Kingston Data Traveler Flash Drive and it says there "Windows/Mac Compatible," but I took it home anyway.

I plugged it on my laptop and Kubuntu Edgy didn't respond. 

I went to /media and the only folders I saw where "cdrom0" and "windows."

How can I use my flash drive?

---

### Post by taurus on 2007-02-07
What's the output of this command from a terminal?

```
dmesg | tail
```

---

### Post by wersdaluv on 2007-02-07
[17179615.072000] Bluetooth: RFCOMM ver 1.7
[17181043.780000] usb 4-4: new high speed USB device using ehci_hcd and address 2
[17181044.780000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17181055.324000] usb 4-4: device not accepting address 2, error -110
[17181055.436000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[17181066.980000] usb 4-4: device not accepting address 3, error -110
[17181067.092000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[17181077.516000] usb 4-4: device not accepting address 4, error -110
[17181077.628000] usb 4-4: new high speed USB device using ehci_hcd and address 5
[17181088.052000] usb 4-4: device not accepting address 5, error -110

---

### Post by taurus on 2007-02-07
Is there a filesystem on that new thumbdrive?  What does this command look?

```
sudo fdisk -l
```

---

### Post by wersdaluv on 2007-02-07
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5737    46082421   83  Linux
/dev/hda2   *        5738        7132    11205337+   7  HPFS/NTFS
/dev/hda3            7133        7296     1317330    5  Extended
/dev/hda5            7133        7296     1317298+  82  Linux swap / Solaris

---

### Post by sstakes1 on 2007-02-07
I had some wierdness with Hi-Speed USB on edgy. Try the following IF NO OTHER USB DEVICES are plugged in.

1. Remove thumbdrive
2. [FONT="Courier New"]sudo modprobe - r ehci_hcd [/FONT]
3. Plug the drive in again. 

You should have it as a low-speed device at this point.
if not, try [FONT="Courier New"]sudo modprobe echi_hcd[/FONT]. to load the module again

HTH

---

### Post by wersdaluv on 2007-02-08
> **sstakes1 said:**
> I had some wierdness with Hi-Speed USB on edgy. Try the following IF NO OTHER USB DEVICES are plugged in.

1. Remove thumbdrive
2. [FONT="Courier New"]sudo modprobe - r ehci_hcd [/FONT]
3. Plug the drive in again. 

You should have it as a low-speed device at this point.
if not, try [FONT="Courier New"]sudo modprobe echi_hcd[/FONT]. to load the module again

HTH

This is what happened...
```
sudo modprobe - r ehci_hcd user@Laptop:~$ sudo modprobe - r ehci_hcd
Password:
FATAL: Module _ not found.
user@Laptop:~$ sudo modprobe echi_hcd
FATAL: Module echi_hcd not found.

```

Note: I tried the codes both with the drive plugged and unplugged.

---

### Post by sstakes1 on 2007-02-09
Can you post the output of running ```
lsmod
``` command on a console

---

### Post by wersdaluv on 2007-02-10
```

Module                  Size  Used by
binfmt_misc            13448  1
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
ipv6                  272288  8
bluetooth              53476  4 rfcomm,l2cap
via                    48224  2
drm                    74644  3 via
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sony_acpi               6412  0
sbs                    16804  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
container               5632  0
button                  7952  0
battery                11652  0
asus_acpi              17688  0
ac                      6788  0
ndiswrapper           208656  0
parport_pc             37796  0
lp                     12964  0
parport                39496  2 parport_pc,lp
joydev                 11200  0
tsdev                   9152  0
snd_via82xx            30360  3
af_packet              24584  4
gameport               17160  1 snd_via82xx
snd_mpu401_uart        10240  1 snd_via82xx
snd_via82xx_modem      16648  0
snd_ac97_codec         97696  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            3456  1 snd_ac97_codec
i2c_viapro              9876  0
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
snd_rawmidi            27264  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
i2c_core               23424  2 i2c_ec,i2c_viapro
via_ircc               28948  0
pcmcia                 40380  0
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  214332  1 via_ircc
crc_ccitt               3200  1 irda
snd_pcm                84612  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
rt2500                188004  1
yenta_socket           28812  1
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                41352  0
serio_raw               8452  0
evdev                  11392  1
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
pcspkr                  4352  0
via_agp                11264  1
agpgart                34888  2 drm,via_agp
via_rhine              26116  0
mii                     6912  1 via_rhine
snd                    58372  17 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_seq_oss,snd_rawmidi,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_seq_device,snd_pcm,snd_timer
soundcore              11232  1 snd
ext3                  142728  1
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  3
via82cxxx              10500  0 [permanent]
generic                 6276  0
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

```

---

### Post by sstakes1 on 2007-02-11
Sorry for the delay. Noticed a few typos in my previous post and some you made as well.

remove all usb devices
Type the following
```
sudo modprobe -r ehci_hcd
```
Plug your device. See if it works. If not type the following
```
sudo modprobe ehci_hcd
```

In my previous post, in the first command, I mistakenly had a space between the - and r.
Also in your second command you had misspelled ehci_hcd as echi_hcd.

HTH

---

### Post by wersdaluv on 2007-02-12
> **sstakes1 said:**
> Sorry for the delay. Noticed a few typos in my previous post and some you made as well.

remove all usb devices
Type the following
```
sudo modprobe -r ehci_hcd
```
Plug your device. See if it works. If not type the following
```
sudo modprobe ehci_hcd
```

In my previous post, in the first command, I mistakenly had a space between the - and r.
Also in your second command you had misspelled ehci_hcd as echi_hcd.

HTH

After trying the codes, I went to see /media but it still was not there

---

### Post by dpatrickryan on 2007-02-17
FWIW, I'm getting exactly the same behaviour with my Kingston Data Traveller 1GB.  Tried unloading and reloading ehci_hcd, no joy.  Same error messages.

---

