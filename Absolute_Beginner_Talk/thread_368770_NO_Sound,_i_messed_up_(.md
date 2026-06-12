---
title: "NO Sound, i messed up :("
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-02-23
alrighty, so i used to have the problem of only having one application using the sound card. no i've got nothing. when i type in command    alsamixer. its says
alsamixer: function snd_ctl_open failed for default: No such device
if i could have some help i would appericate it 
also my sound card is :
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
thanks a million if you can help!

---

### Post by netkid91 on 2007-02-23
List the items in /dev/snd please.
Edit: Also please post the results from lsmod.

---

### Post by tcebak on 2007-02-23
just wanted to say thanks
tony@tony-laptop:/dev/snd$ ls
controlC0  pcmC0D0c  pcmC0D0p  timer 
 
so those are the files in there and then the other is pretty long:
tony@tony-laptop:/dev/snd$ lsmod
Module                  Size  Used by
nls_cp437               6912  1 
isofs                  38076  1 
udf                    89348  0 
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nfsd                  234276  13 
exportfs                7296  1 nfsd
lockd                  67976  2 nfsd
sunrpc                165948  8 nfsd,lockd
i915                   21632  2 
drm                    74644  3 i915
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  6 
ndiswrapper           208656  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
b44                    26764  0 
mii                     6912  1 b44
snd_hda_intel          20116  0 
snd_hda_codec         164608  1 snd_hda_intel
joydev                 11200  0 
tsdev                   9152  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
pcspkr                  4352  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
serio_raw               8452  0 
psmouse                41352  0 
evdev                  11392  2 
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  1 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
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

hope this helps

---

### Post by netkid91 on 2007-02-23
It seems to me that the kernel is loading the wrong module for your sound card, try running these commands in a terminal:
sudo rmmod  snd_hda_intel
sudo modprobe snd_intel8x0
And see if that works.

---

### Post by tcebak on 2007-02-23
alright, so i typed both in and nothing happened. so i assumed that it worked. then i opened a media player and it said no sound card deteced. then i typed them in again and i got this message:
tony@tony-laptop:~$ sudo rmmod snd_hda_intel
ERROR: Module snd_hda_intel does not exist in /proc/modules

---

### Post by netkid91 on 2007-02-23
Restart and Run System->Preferences->Sound
Open up the "Sounds" tab and look for "Default Sound Card" and tell me what it says.

---

### Post by tcebak on 2007-02-23
alrighty i restarted and i went to sound and it does not have a default sound card. i used to have one there but i forget. i accident changed it somehow. i know this is hard to help me with but i appericate.   also my alsamixer does not work. maybe reinstall it?(help how to :)
also all devices are on asla

---

### Post by netkid91 on 2007-02-23
Ahh the infamous duplexing bug on that card, if you can, try and undo the changes you made and check the files for errors, if you can't you might just want to reinstall Ubuntu if it's not too much trouble.

---

### Post by tcebak on 2007-02-24
ouch. that sucks. i think i am going to hold off. becasue i had a lot of trouble with resulotion and wireless card. but if you find anything. let me know. thanks

---

### Post by netkid91 on 2007-02-26
You might just want to double check and make sure all of the config files that you changed don't have errors in them.

---

