---
title: "UT 2k4 sound- and accessproblem"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by Basfriends on 2006-05-11
Hello,

i have the nvidia drivers proper installed and i have the ut2k4 game proper installed, but i am having difficulties. 

The first difficulty is that i have to use sudo in order to run the game (the problem is that the .ut2004 directory in the home directory is owned by "root". In order to solve this problem i assume i just have to change the ownership of the directory. But i have no single clue how to do this).

My second problem is one that many of you may have encountered already. Everytime i run in a console "sudo ut2004" the game starts. When I quit it (because i have no sound), the terminal gives the following output:

open /dev/[sound/]dsp: No such device
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

please note that it reads no such device and not device busy or used or something. 

I have tried googeling up for results, and I also have tried this forum, but with little success. I hope someone can help me with this problem. Thanks on forehand, Bas
If you need more information about my system please ask.

PS: here is my lsmod

bas@getafix:~$ lsmod
Module                  Size  Used by
nls_cp437               5760  1
isofs                  36664  1
udf                    92356  0
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_userspace       4380  0
cpufreq_stats           5316  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252544  6
af_packet              22088  2
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
rt2500                179684  1
emu10k1_gp              3712  0
gameport               14920  2 emu10k1_gp
snd_emu10k1_synth       7616  0
snd_emux_synth         36096  1 snd_emu10k1_synth
snd_seq_virmidi         7232  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_seq_dummy           3716  0
snd_seq_oss            33664  0
snd_seq_midi            9184  0
snd_seq_midi_event      7040  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51024  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           118404  2 snd_emu10k1_synth
snd_rawmidi            25056  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8524  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         84028  1 snd_emu10k1
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10696  2 snd_emu10k1,snd_pcm
snd_util_mem            4544  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8992  2 snd_emux_synth,snd_emu10k1
snd                    55172  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
em8300                 57280  0
i2c_algo_bit            9480  1 em8300
soundcore               9696  2 snd,em8300
i2c_viapro              8016  0
via686a                19864  0
i2c_sensor              3456  1 via686a
i2c_core               21328  5 i2c_acpi_ec,i2c_algo_bit,i2c_viapro,via686a,i2c_sensor
pci_hotplug            27636  0
via_agp                 9728  1
dm_mod                 58044  1
evdev                   9728  0
tsdev                   7872  0
nvidia               3922812  12
agpgart                34888  2 via_agp,nvidia
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  1
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  1 thermal
fan                     4548  0
ide_disk               18560  3
pdc202xx_old           11456  1
uhci_hcd               31376  0
usbcore               118396  2 uhci_hcd
ide_cd                 41732  1
cdrom                  39904  1 ide_cd
ide_generic             1472  0
via82cxxx              13532  1
ide_core              139028  5 ide_disk,pdc202xx_old,ide_cd,ide_generic,via82cxxx
unix                   27248  599
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

---

### Post by Basfriends on 2006-05-11
Can someone please help me?

---

