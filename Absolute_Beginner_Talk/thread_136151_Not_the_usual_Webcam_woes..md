---
title: "Not the usual Webcam woes."
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Archaios on 2006-02-25
Just got ubuntu the other day, loving it so far.

Anyway, I have an intel cs330 webcam, I ran easycam2 and got the driver installed just fine.  My computer also seems to have no problem locating the webcam.  Opening the webcam doesn't freeze my computer like most of the threads I've read involving webcam issues.  I just have a black screen.  I've tried fiddling with the contrast/brightness to no avail, still black.  Plugged the webcam into my other PC using windows xp home, and it worked fine, so it's not the hardware.

Anyone know how to fix this problem?

*edit* I've done some research online and it seems to be that I need to adjust the gamma setting on the driver.  The places I've read recommend doing it like so

sudo modprobe spca5xx gamma=3 *or any number 1-7

However when I do that I get this error message.

FATAL: Error inserting spca5xx (/lib/modules/2.6.12-9-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

Any help would be appreciated

**

---

### Post by az on 2006-02-25
Are you sure that is the webcam's chipset?


With the camera plugged in, type
lsmod

---

### Post by Archaios on 2006-02-25
After typing in lsmod

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
tsdev                   7616  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
videodev                9344  0
snd_cs46xx             78664  1
gameport               14472  2 snd_cs46xx
snd_rawmidi            22816  1 snd_cs46xx
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_cs46xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_cs46xx,snd_pcm
rt2500                150372  1
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
hw_random               5268  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  1 intel_agp
nls_utf8                2176  1
ntfs                   92016  1
dm_mod                 50364  1
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  651
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

Was printed out on the screen, I'm not really sure what I'm supposed to be looking for...  Complete linux noob, sorry.

---

