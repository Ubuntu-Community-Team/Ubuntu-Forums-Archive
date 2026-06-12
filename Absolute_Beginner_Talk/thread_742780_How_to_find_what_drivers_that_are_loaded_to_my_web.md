---
title: "How to find what drivers that are loaded to my webcam"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by MockY on 2008-04-02
I want to know what drivers thats in use for my webcam. How do I go about to find that?

---

### Post by spiderbatdad on 2008-04-02
is it a usb webcam?

```
lsusb
```should give you a cam name, like quickcam...
```
lsmod
```will show you modules currently loaded.
then try```
sudo updatdb
locate quickcam | grep drivers
```that should point you to a folder of several usbcam drivers...anyway its something like /lib/modules/2.6.24-12-generic/kernel/drivers/media/video/usbvideo/

---

### Post by MockY on 2008-04-02
What should I do with lsmod? It does not list the drivers currently used...or does it?

```
mocky@Mapex:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. 
Bus 002 Device 004: ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
Bus 002 Device 001: ID 0000:0000 
```

```

mocky@Mapex:~$ lsmod
Module                  Size  Used by
vmnet                  44596  13 
vmblock                16288  3 
vmmon                 945260  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
video                  18060  0 
ac                      6148  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
reiserfs              248704  1 
sbp2                   24072  0 
lp                     12580  0 
gspca                 608336  0 
snd_cmipci             37024  3 
gameport               16776  1 snd_cmipci
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep              10244  1 snd_opl3_lib
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
zc0301                 49156  0 
compat_ioctl32          2304  1 zc0301
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
videodev               29312  2 gspca,zc0301
v4l1_compat            15364  1 videodev
v4l2_common            18432  2 zc0301,videodev
snd_mpu401              9640  0 
snd_mpu401_uart         9600  2 snd_cmipci,snd_mpu401
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_opl3_lib,snd_seq
snd_rawmidi            25728  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
nvidia               6221648  34 
snd                    54660  18 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
psmouse                39952  0 
ati_agp                10124  0 
i2c_ali15x3             9092  0 
i2c_ali1535             8196  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  2 nvidia,ati_agp
i2c_core               26112  3 nvidia,i2c_ali15x3,i2c_ali1535
k8temp                  6656  0 
ipv6                  273892  12 
joydev                 11328  0 
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
ahci                   23300  3 
alim15x3               12556  0 [permanent]
ide_core              116804  1 alim15x3
floppy                 60004  0 
ata_generic             8452  0 
libata                125168  2 ahci,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
skge                   43152  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ohci_hcd               22916  0 
usbcore               138632  6 gspca,zc0301,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

### Post by spiderbatdad on 2008-04-02
shows modules loaded. I believe linux only uses v4l drivers, so unless the manufacturer provides support...that's what your stuck with. There are programs, surely, to make use of your webcam, and most webcams are readily detected in ubuntu...what app are you trying to put to use? Maybe someone could help you with that.

---

### Post by MockY on 2008-04-02
The webcam works just fine, no problems at all. I just want to know what drivers that it uses.

---

### Post by ryanhaigh on 2008-04-02
Google seems to indicate that gspca is the driver for the webcam.

---

### Post by MockY on 2008-04-02
I want to know for sure though. spca5xx was used in Breezy.

---

### Post by ryanhaigh on 2008-04-02
Unload the module and see if your camera still works then.
```
sudo rmmod gspca
```
The modules are dependant on each other for example it won't work without v4l which is higher level but it probably won't work without gspca or zc0301 either.

---

### Post by MockY on 2008-04-02
Nothing happened. That means that it uses gspca?

---

