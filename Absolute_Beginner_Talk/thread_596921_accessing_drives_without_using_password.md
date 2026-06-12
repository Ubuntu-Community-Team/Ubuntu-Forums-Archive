---
title: "accessing drives without using password"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by katch22 on 2007-10-30
Quick question, should be easy answer for someone, at least I hope.  When I reboot I have to enter my password before I can access my other hard drive. It's a little inconvenient because I have some links on my desktop to directories on that drive. The links don't work until I open up "computer" and click the drive there and enter my password. Is there any way to not have to do this? It is an NTFS drive by the way and I haven't had any trouble accessing it after entering the password, I just don't want to have to enter the password every time! I'm running a fresh install of 7.10 by the way. Thanks for any help or insight anyone can give me on this issue.

---

### Post by MrFSL on 2007-10-30
Hum...

I have never been prompted for a password when accessing ntfs drives.

Try this reboot and before you access the drive post the results of:
```
sudo lsmod
```

Then after entering the password and accessing the drive again post the results of:
> sudo lsmod

I'm guessing you are being asked for sudo privileges to load ntfs related modules.

---

### Post by katch22 on 2007-10-30
I there is a better way to format this let me know

output of 'sudo lsmod' after reboot, before accessing drive:

me@dungh34p:~$ sudo lsmod
[sudo] password for me:
Module                  Size  Used by
wlan_wep                8064  2 
ipv6                  273892  8 
af_packet              24840  4 
binfmt_misc            12936  1 
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
dock                   10656  0 
sbs                    19592  0 
button                  8976  0 
ac                      6148  0 
container               5504  0 
video                  18060  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
wlan_scan_sta          15104  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_rate_sample        14208  1 
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
ath_pci                98336  0 
wlan                  206660  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
ath_hal               192720  3 ath_rate_sample,ath_pci
iTCO_wdt               11940  0 
nvidia               4716468  22 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_core               26112  1 nvidia
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
8139cp                 25088  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_piix               17540  2 
floppy                 60004  0 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
me@dungh34p:~$ 


After accessing drive:

me@dungh34p:~$ sudo lsmod
Module                  Size  Used by
wlan_wep                8064  2 
ipv6                  273892  8 
af_packet              24840  4 
binfmt_misc            12936  1 
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
dock                   10656  0 
sbs                    19592  0 
button                  8976  0 
ac                      6148  0 
container               5504  0 
video                  18060  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
wlan_scan_sta          15104  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_rate_sample        14208  1 
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
ath_pci                98336  0 
wlan                  206660  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
serio_raw               8068  0 
ath_hal               192720  3 ath_rate_sample,ath_pci
iTCO_wdt               11940  0 
nvidia               4716468  22 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_core               26112  1 nvidia
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
8139cp                 25088  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_piix               17540  3 
floppy                 60004  0 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
me@dungh34p:~$

---

### Post by katch22 on 2007-10-30
Hrmm.. I see the line "ata_piix 17540 2" changes to "ata_piix 17540 3" what exactly does the "used by" value tell me?

---

### Post by MrFSL on 2007-10-30
Huh - doesn't seem to be a module loading issue so I'm not sure. 

I see from google that you aren't the only one with this problem so perhaps that is the place to go next.

---

### Post by steve.horsley on 2007-10-30
Can you post the contents of your /etc/fstab file? This is the file that dictates what drives should be mounted at boot and what options should be used.

---

### Post by katch22 on 2007-10-30
me@dungh34p:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=478e483d-7e02-4554-8934-8bb0d9e95e65 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=40a76526-13bc-4f13-b25f-fff205c3bcec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
me@dungh34p:~$

---

### Post by coelho on 2007-10-30
this page worked for me with a FAT drive. also has instructions for NTFS

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by steve.horsley on 2007-10-30
That psychocats article looks good except that I would use a umask of 0 which means everyone has read/write permission. This is a line from my fstab:
/dev/sda2       /mnt/windows     ntfs     umask=000,gid=46     0       0

Only on gutsy can you write NTFS drives by default - earlier versions needed different drivers installing.

---

### Post by katch22 on 2007-10-31
To everyone who replied to my questions: Thanks for getting me pointed in the right direction, it was a great help! 

To make a long story short my problem is solved by adding a line to /etc/fstab 

If anyone else has a similar problem please see one or both of the following threads, they had all the info I needed to solve the problem, I just didn't search well enough to find them before I posted my question:

[http://ubuntuforums.org/showthread.php?t=411966&page=2](http://ubuntuforums.org/showthread.php?t=411966&page=2)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

