---
title: "Weird Dev names"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Foxmike on 2007-07-01
Okay, that's really weird.  I've reinstalled the whole system (Ubuntu Feisty) and it is not the first time I'm doing it.

I did reinstalled because I played with a lot of things and the system became to be unstable so I decided just to do a clean install.

Here is the weird thing: All my drives are IDE.  I have no SCSI of any kind on my machine.  All the times I used Ubuntu until now, the drives were identified as '/dev/hd[a-z][0-9]'.  Now, they are identified as '/dev/sd[a-z][0-9]' for the hard drives and '/dev/scd[0-9]' for the optical drives.

I have rebooted the whole machine to make sure it booted well.

Any clue what is happening here?

Here the results of lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```

And the result of lsmod:

```
Module                  Size  Used by
vmnet                  39076  13 
vmmon                 113836  0 
isofs                  36284  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
video                  16388  0 
container               5248  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
battery                10756  0 
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
button                  8720  0 
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usblp                  14848  0 
serio_raw               7940  0 
analog                 12832  0 
nvidia               4713780  22 
gameport               16520  1 analog
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
pcspkr                  4224  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
sis_agp                 9604  1 
agpgart                35400  2 nvidia,sis_agp
i2c_sis96x              6532  0 
i2c_core               22656  3 i2c_ec,nvidia,i2c_sis96x
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  5 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  8 
sis5513                14856  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0 
floppy                 59524  0 
ehci_hcd               34188  0 
sis900                 24704  0 
mii                     6528  1 sis900
ohci_hcd               22532  0 
usbcore               134280  4 usblp,ehci_hcd,ohci_hcd
pata_sis               14732  6 
libata                125720  2 ata_generic,pata_sis
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
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
```

And my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=e3f4c7a2-3bd8-4870-b5be-a487cfb95c44 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=e3e112d8-65b0-41bd-96c2-63361a5e9fb8 /home           ext3    defaults        0       2
# /dev/hdb1
UUID=ac50a4d5-920e-4d5b-ad61-de0e76b097db /media/data     ext3    defaults        0       2
# /dev/hdb3
UUID=5bdb901b-de15-4545-8d84-6c82ac82c13c /media/hdb3     ext3    defaults        0       2
# /dev/hda3
UUID=88d2813c-1d60-441a-b4eb-913828c893e0 /media/multimedia ext3    defaults        0       2
# /dev/hdb2
UUID=baca98c1-cfa7-47cd-85ce-2b0f60f42a3f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Thanks!

---

### Post by Pragmatist on 2007-07-01
I don't see the sd* or scd* in your fstab file.  Please post the output of:
```
mount
```

---

### Post by cogadh on 2007-07-01
The current Linux kernel treats all drives as if they were SCSI, so even though you are using IDE/PATA, they will appear as sda, sdb, etc. instead of hda, hdb, etc. It doesn't affect the operation of the drives, however.

---

### Post by Pragmatist on 2007-07-01
> **cogadh said:**
> The current Linux kernel treats all drives as if they were SCSI...
Which kernel is that?  I'm using Feisty and my drives are all /dev/hd[a-z]  If it is an upgraded kernal, what is the exact version numbers?

---

### Post by cogadh on 2007-07-01
The 2.6 kernel IDE module detects and labels all drives as SCSI. It may mount the device under /dev/hd* (it shouldn't), but the device itself will be labelled sd*. For example, I only have IDE drives in my system, but this is what is output by mount:
```
/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
```
I'm running the 2.6.20-16 kernel from the repositories, but I first noticed it with the default Feisty 2.6.20-15 kernel.

---

### Post by steve.horsley on 2007-07-01
As for why, I read that the SCSI module was found to give better performance than the IDE module when handking IDE drives, so now they're using the SCSI module for both. 

As for version, Feisty has actually wavered between using hd* and sd* names between updates, but is currently using sd*. My current version is Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007

---

### Post by Pragmatist on 2007-07-01
> **cogadh said:**
> The 2.6 kernel IDE module detects and labels all drives as SCSI. It may mount the device under /dev/hd* (it shouldn't), but the device itself will be labelled sd*. For example, I only have IDE drives in my system, but this is what is output by mount:
```
/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
```I'm running the 2.6.20-16 kernel from the repositories, but I first noticed it with the default Feisty 2.6.20-15 kernel.

I've been using the 2.6 kernels for 3 years and I've never had my drives labeled as sd[a-z]  I have three computers and this is true of all of them.  It cannot just be the 2.6 series that is the problem.

Also, I am using the 2.6.20-15-386 kernel right now and my drives are all hd[a-z] except removable USB drives.

Are you using SATA drives?

---

### Post by Pragmatist on 2007-07-01
According to this thread:
[http://www.linuxquestions.org/questions/showthread.php?t=552872](http://www.linuxquestions.org/questions/showthread.php?t=552872)

the change started with 2.6.20  This doesn't explain why my drives are all hd[a-z] since I am using 2.6.20-15  Perhaps Ubuntu hadn't switched over yet.

---

### Post by cogadh on 2007-07-01
Did you do a clean install of Feisty or upgrade from a previous version? I did a clean install, which may explain the naming convention. In my previous install of Edgy, it still did /dev/hd*.

---

### Post by Foxmike on 2007-07-02
Sorry if it took so long...

I did a clean install of Feisty, from a CD sent by ShipIt.  This is the first clean install I'm doing for Feisty (the last one was an install from the alpha version that have been upgraded to the stable version.)

However, I always got /dev/hd[a-z] to refer to my IDE drives, this is the first time I get sd[a-z].

I'm now using kernel 2.6.20-16-generic (as per uname -r)

Here's the output of mount:
> /dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw)
/dev/sdb1 on /media/data type ext3 (rw)
/dev/sdb3 on /media/hdb3 type ext3 (rw)
/dev/sda3 on /media/multimedia type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
@ Pragmatist: I've followed the link you sent and I noticed (correct me if I am wrong) that this would apply on PATA discs.  I'm using true IDE drives, so it shouldn't apply, then, no?

As well, here's a screenshot if the "Computer" folder in Nautilus.  You will notice that it refers to "CD-ROM 1", "CD-ROM 2", "Lecteur CD-RW" (CD-RW Reader), and "Lecteur CD-RW/DVD±RW" (CD-RW/DVD±RW Reader).  Since I have 2 optical drives, it seems to refer to each twice, wich is another difference from the ancient installation that refered to optical drives onsly once using names as "CD-RW/DVD±RW Reader" instead of "CD-ROM 1".  This is only a detail but I look at it as a symptom of something going wrong or at least weird.

---

### Post by Pragmatist on 2007-07-02
> **Foxmike said:**
> ...this would apply on PATA discs.  I'm using true IDE drives, so it shouldn't apply, then, no?
No. IDE is PATA  

From Wikipedia: 
> **PATA** can refer to:[LIST]
[*](Parallel) [AT Attachment]("http://en.wikipedia.org/wiki/AT_Attachment"), a hard disk interface also known as IDE, ATA, ATAPI, UDMA and PATA."[/LIST]Here is the link:
[http://en.wikipedia.org/wiki/Pata](http://en.wikipedia.org/wiki/Pata)

---

### Post by Inxsible on 2007-07-02
You can get rid of the phantom drives (CD-ROM 1 & CD-ROM 2) by removing their corresponding entries from fstab. Since they are CD Drives, they are supposed to mount automatically when you put in any CD.

You see the phantom drives because the kernel 2.6.20-16 names the CD drives differently than the -15 kernel.

---

### Post by Foxmike on 2007-07-02
@ Pragmatist & Inxsible: Thanks for the infos!  I guess I still have a lot to learn!:)

Regards,

-Foxmike

---

