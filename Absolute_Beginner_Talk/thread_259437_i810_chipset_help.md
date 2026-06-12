---
title: "i810 chipset help"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-09-17
So, my new Compaq Presario 410 (V5000Z) has an Intel graphics chipset. For some reason, I can't get the screen resolution to be 1280x800, it can only be 1024x768, 800x600, or 640x480. I tried editing the xorg.conf file, but no luck. I even tried crashing xserver so I could reconfigure it, but again, no luck. I see there are drivers online for this chipset, so maybe that could help? But I don't know how I would go about installing the drivers. There is a choice of Windows or Linux drivers. Could I use wine with the Windows driver, or is that just pointless? And, the linux drivers are .rpm type, with a choice of binary or agpgart.o, which do I use and how do I install and activate them? I have ndiswrapper, could that help?

Thanks

---

### Post by jan1024188 on 2006-09-17
no you cant use wine for drivers....

---

### Post by elettronicha on 2006-09-17
First open a terminal and type
```
lsmod|grep i810
```

If you see "i810", it means the driver is loaded correctly. Then you can install the package "915resolution" with synaptic or typing

```
sudo apt-get update
sudo apt-get install 915resolution
```

Tell me if it works.

---

### Post by kbsuperstar on 2006-09-17
It doesn't say i810 after I execute the first command. But what do I do after the second command? I successfully got the program or whatever, ```
Patch mode 5c to resolution 1280x800 complete
915resolution.
```

What do I do now?

---

### Post by elettronicha on 2006-09-17
> **kbsuperstar said:**
> It doesn't say i810 after I execute the first command. 
I don't remember if the correct driver is i810, since I haven't got that kind of chipset on my laptop. Just post the result of the command "lsmod".

> But what do I do after the second command? I successfully got the program or whatever, ```
Patch mode 5c to resolution 1280x800 complete
915resolution.
```

What do I do now?
Reboot.

---

### Post by kbsuperstar on 2006-09-17
lsmod output:

```
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
ipv6                  265728  6
ndiswrapper           170512  0
af_packet              22920  2
dm_mod                 58936  1
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
joydev                 10048  0
tsdev                   8000  0
e100                   40580  0
mii                     5888  1 e100
rtc                    13492  0
hw_random               5652  0
psmouse                36100  0
serio_raw               7300  0
snd_hda_intel          18964  3
snd_hda_codec         157616  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
sg                     37920  0
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  4 ndiswrapper,ehci_hcd,uhci_hcd
sd_mod                 19984  3
ahci                   17284  4
libata                 78992  1 ahci
scsi_mod              139496  4 sg,sd_mod,ahci,libata
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

---

### Post by jordanmthomas on 2006-09-17
You have the i915 module loaded.  If you have an i915 then that's good.  What card do you have exactly?  I have an i915 and the i915 module is loaded.  

Could you post this?
```
cat /etc/X11/xorg.conf
```

nevermind, you seem to have got it working

---

### Post by kbsuperstar on 2006-09-17
It worked! THANKS!!!

I don't know if it was just the command you gave me, but I also downloaded i810switch in synaptic.

THANK YOU THANK YOU THANK YOU

---

### Post by elettronicha on 2006-09-17
I think the driver is that 'i915'. Please tell me if rebooting something happens. That trick worked for an ACER 500x (x maybe 3 or 5 or 6? don't remember) of a friend of mine.

---

### Post by elettronicha on 2006-09-17
> **kbsuperstar said:**
> It worked! THANKS!!!

I don't know if it was just the command you gave me, but I also downloaded i810switch in synaptic.

THANK YOU THANK YOU THANK YOU
They both work.

---

