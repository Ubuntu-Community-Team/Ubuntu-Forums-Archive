---
title: "ALSA sound problems"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by gwethir on 2007-12-09
EDIT: Solved. I followed this guide: [http://ubuntuforums.org/showpost.php...6&postcount=28](http://ubuntuforums.org/showpost.php...6&postcount=28)


When I first installed Ubuntu 7.10 there were sound, but using OSS which skype doesn't support (right?). I have now tried to install alsa, but with no luck. I have been through some guides. Downloaded tar-balls, and done everything right. And it should be installed, and looking in Synaptic I find that alsa-bas, alsa-utils and some additional alsa-stuff (alsa-tools etc) is installed. But now I'm stuck. Volume bar says "No volume control GStreamer plugins and/or devices found.", Alsamixer says: "alsamixer: function snd_ctl_open failed for default: No such device" 

Looking in the alsa dir, and reading through some of the files it asks me to do "asoundconf set-default-card". And to find a list of my cards I do "asoundconf list" but nothing shows up.

If I go to System-Preferences-sounds and I set any of the sound-devices to ALSA and presses "Test" I get this error:```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.
```

I've seen some other people with problems providing this stuff so I'll do it aswell:

Result from lsmod:
```

Module                  Size  Used by
binfmt_misc            12936  1 
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vmix                   14132  1 
ossusb                 56200  1 
sbxfi                  26100  1 
ich                    20336  1 
osscore               565812  6 vmix,ossusb,sbxfi,ich
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
button                  8976  0 
sbs                    19592  0 
container               5504  0 
video                  18060  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14080  2 
fat                    54300  1 vfat
lp                     12580  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
rt61pci                24576  0 
rt2x00pci              11520  1 rt61pci
rt2x00lib              19584  2 rt61pci,rt2x00pci
rfkill                  8208  1 rt2x00lib
mac80211              171016  4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
cfg80211                7304  1 mac80211
usbhid                 29536  0 
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
nvidia               6221648  36 
xpad                    9988  0 
hid                    28928  1 usbhid
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
i2c_core               26112  1 nvidia
pcspkr                  4224  0 
eeprom_93cx6            3200  1 rt61pci
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
usb_storage            73024  1 
ide_core              116804  1 usb_storage
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  7 
ata_generic             8452  0 
libusual               18448  1 usb_storage
floppy                 60004  0 
r8169                  32260  0 
ata_piix               17540  4 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 ossusb,usbhid,xpad,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

```


Result from strace -eopen alsamixer:

```

open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/home/andreas/.asoundrc", O_RDONLY) = 3
open("/home/andreas/.asoundrc.asoundconf", O_RDONLY) = 4
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENXIO (No such device or address)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC1", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC1", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC2", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC2", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC3", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC3", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC4", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC4", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC5", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC5", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC6", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC7", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC7", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC8", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC8", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC9", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC9", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC10", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC10", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC11", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC11", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC12", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC12", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC13", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC13", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC14", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC14", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC15", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC15", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC16", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC16", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC17", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC17", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC18", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC18", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC19", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC19", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC20", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC20", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC21", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC21", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC22", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC22", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC23", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC23", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC24", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC24", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC25", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC25", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC26", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC26", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC27", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC27", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC28", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC28", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC29", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC29", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC30", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC30", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC31", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/dev/aloadC31", O_RDONLY)         = -1 ENOENT (No such file or directory)

```



Included in my /etc/modules.conf:
```

fuse
lp
snd-hwdep
snd-hda-intel


```


Not sure if this is suposed to be in the total newbie forum or general help or something, but as I'm rather new to Ubuntu, I posted it here. I know it was a lot of info, but I hope that makes it easier to help me with

Thanks in advance!

---

### Post by meborc on 2007-12-09
you can try lspci to see if your soundcard/chip shows on the list

---

### Post by gwethir on 2007-12-09
yes it does:

```

00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)

```

Also has another soundcard, but if I'm correct the only ubuntu driver for it is a BETA 64 bit version, and I'm using 32bit.
```

02:01.0 Multimedia audio controller: Creative Labs SB X-Fi


```

---

### Post by McGriff on 2007-12-09
I know how you feel man i have the same problem and i have tried every guild posted on the forums and i have the same sound card/chip set as you and if you do a search on the forums you will find hundreds of the same treads all with the same sound issue's its the AC'97 Intel hardware and i have NO idea why this wasn't sorted out with 7.10 as its a huge problem , Anyway man good luck I hope you get there i will keep checking your tread and if i find out something I'll let you know don't  lose heart with reply's either as alot of ppl dont know how to fix it but anyway GOOD LUCK:guitar:

---

### Post by gwethir on 2007-12-10
I hope someone have a good answer ;P Kinda annoying, as I'm used to always talk to people at skype. Anyone?


-aka- BUMP

---

### Post by philinux on 2007-12-10
As a last resort seen as you had sound initially I'd move home to a separate partition and reinstall.

Somewhere along the line something's got messed up. It's difficult to retrace one's steps too.

---

### Post by gwethir on 2007-12-10
Well, problem is, I had sound with OOS which skype doesn't support, and what I need sound for is mostly skype... So if I reinstall I'll have to mess it up all again and try to get ALSA...   I've probably just missed a step in the installation of ALSA?

---

### Post by philinux on 2007-12-10
In that case uninstall ALSA everything , completely remove it and start again.

Did you install from repo's?

---

### Post by gwethir on 2007-12-10
Finally fixed it! Followed these steps:

[http://ubuntuforums.org/showpost.php?p=1897576&postcount=28](http://ubuntuforums.org/showpost.php?p=1897576&postcount=28)


But now I have another problem.... When I use skype there is only sound in one of the headset-cups. But if I for instance play music in amarok, I get sound from both.... Gets kinda annoying

---

