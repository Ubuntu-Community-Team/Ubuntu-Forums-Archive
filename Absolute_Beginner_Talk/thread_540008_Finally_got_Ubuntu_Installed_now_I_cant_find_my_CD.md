---
title: "Finally got Ubuntu Installed now I cant find my CD Drive"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Azerial on 2007-09-01
Okay I cannot FInd my CD Drive,  went to computer, clicked CD-ROM 1 say it doesnt exist

I have a Lite-On CD/DVD burner combo drive, and I backed up some pictures and media files as well as my firefox bookmarks from my old windows xp system, Im wanting to open this CD to get these files.  Why Cant I can find it, 

What am I doing wrong... Its my first time using LInux and so far Its been user friendly... but this... I dunno I want the security of Linux but I dont want to be unable to use my effin hardware

It does not auto run cds or DVDs

It does not recongize Audio Cds

I can not Open files from Data CD or data DVDs

I can not use it peroid!!!

---

### Post by voodooKobra on 2007-09-01
I'm not sure, but I think it might show up as a directory in /

Like you have /home and /etc, maybe one will show up for your CD?

---

### Post by Azerial on 2007-09-01
> **voodooKobra said:**
> I'm not sure, but I think it might show up as a directory in /

Like you have /home and /etc, maybe one will show up for your CD?

/ ? 

explain

Its my FIRST day using linux for more than a couple minutes Im still at the bottom of the learning curve here buddy, what you just said confused me

---

### Post by southernman on 2007-09-01
odd, you should be able to just plop the cd in the tray and it should automagically open for you.

If you look in /media you'll see two entries /cdrom0 and /cdrom, normally to mount the drive with a cd in the tray do this on the command line:

sudo mount /media/cdrom

---

### Post by southernman on 2007-09-01
After reading your last post... allow me. :p

To see the cdrom0 and cdrom go to Places > Computer > Filesystem > Media

To run the command I specified above go to Applications > Accessories > Terminal and if you can't be bothered to type the command, you could always c&p it (that's copy and paste).

---

### Post by Azerial on 2007-09-01
> **southernman said:**
> After reading your last post... allow me. :p

To see the cdrom0 and cdrom go to Places > Computer > Filesystem > Media

To run the command I specified above go to Applications > Accessories > Terminal and if you can't be bothered to type the command, you could always c&p it (that's copy and paste).

mike@Azerial:~$ sudo mount /media/cdrom
Password:
mount: special device /dev/scd0 does not exist
mike@Azerial:~$ 


gave me that

Also when I found the cdrom0 and cdrom they displayed empty, there was nothing there

---

### Post by southernman on 2007-09-01
Ummm there just mount points. Not suppose to have files in them.

Post your /etc/fstab file

---

### Post by Azerial on 2007-09-01
> **southernman said:**
> Ummm there just mount points. Not suppose to have files in them.

Post your /etc/fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=df989f16-c74c-448e-9d0f-cdf591517c20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=6CBC70FABC70BFDE /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=9fd52e66-4158-4f1e-abfb-01f96a74bcc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by southernman on 2007-09-01
I don't aim to try and reinvent the wheel here, there are a heap of documents out there for you to find and read. But I am willing to try and help you, help yourself... ok.

Everything that is installed on your system is installed into / - aka the root partition. Same thing as Places > Computer > Filesystem

If someone ask you to look in /etc/fstab that would be the exact same thing as to Places > Computer > Filesystem > etc

You certainly don't have to learn how to use the command line well enough that you could do it blind folded, facing away from the keyboard, and being stung by 1000's of killer bee's at the same time... but you are going to find when asking for help most of the instructions will request you to interact with it. [http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php") is a great place to start for that.

[This link]("https://help.ubuntu.com/community/CategoryDocumentation") is a great listing of more howto's than you'll be able to read over the week-end. So bookmark it and refer to it if you are looking for help with something... as a first resort that is. Still need help and can't find the solution on your own, stop by here. ;)

One final word of advice. You don't need to keep anouncing the fact that your a new linux user. It's irrelevant and doesn't make people want to help you any more or less because of it. OK.

If you'll post that file "/etc/fstab" I'll have a look see.

In the meantime, run a test to see if it may be the disk your trying to use. Insert the Ubuntu Installation disk (since we know it worked in your drive already) and see if it auto mounts and opens a nautilus window with the contents of the disk.

Thanks... and Welcome to Ubuntu! ;)

---

### Post by Azerial on 2007-09-01
I put the Ubuntu CD in and NOTHING happened, just as I supected, I tried not just it, but other data cds, and an audio cd

here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=df989f16-c74c-448e-9d0f-cdf591517c20 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=6CBC70FABC70BFDE /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3
UUID=9fd52e66-4158-4f1e-abfb-01f96a74bcc5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

and on a friends recommendation heres what I got when I typed mount into the terminal

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
tmpfs on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw,mode=0755)


Im off to bed for now though gotta be at work in about 7 hours, bed time, hopefully someone will post me a good fix.

Kinda figures after all the hell Id go though getting LInux to install Id have hell getting it to work

---

### Post by southernman on 2007-09-01
ok... a little deeper we go then. 

post the output of "lspci" and "lsmod"

I'll run a test of my own but I don't think that running mount will show the cd drive unless it's actually mounted with a disk.

brb and edit this post with the result.

edited results found:
without a disk in the drive...
```

/dev/hda6 / ext3 rw,noatime,errors=remount-ro,data=writeback 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda5 /boot ext3 rw,noatime 0 0
/dev/hda2 /home ext3 rw,noatime,data=writeback 0 0
/dev/hda3 /media/multimedia ext3 rw,noatime,data=writeback 0 0
/dev/hda7 /media/storage ext3 rw,noatime,data=writeback 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```
with a disk in the drive...
```

/dev/hda6 / ext3 rw,noatime,errors=remount-ro,data=writeback 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda5 /boot ext3 rw,noatime 0 0
/dev/hda2 /home ext3 rw,noatime,data=writeback 0 0
/dev/hda3 /media/multimedia ext3 rw,noatime,data=writeback 0 0
/dev/hda7 /media/storage ext3 rw,noatime,data=writeback 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
**/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=username 0 0**

```

Thought so, the mount command stores it's data in /etc/mtab and only shows the partitions (mount points) that are mounted at the time you look at the file or run the "mount" command just as you did.

---

### Post by Azerial on 2007-09-01
> **southernman said:**
> ok... a little deeper we go then. 

post the output of "lspci" and "lsmod"

I'll run a test of my own but I don't think that running mount will show the cd drive unless it's actually mounted with a disk.

brb and edit this post with the result.

edited results found:
without a disk in the drive...
```

/dev/hda6 / ext3 rw,noatime,errors=remount-ro,data=writeback 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda5 /boot ext3 rw,noatime 0 0
/dev/hda2 /home ext3 rw,noatime,data=writeback 0 0
/dev/hda3 /media/multimedia ext3 rw,noatime,data=writeback 0 0
/dev/hda7 /media/storage ext3 rw,noatime,data=writeback 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```
with a disk in the drive...
```

/dev/hda6 / ext3 rw,noatime,errors=remount-ro,data=writeback 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda5 /boot ext3 rw,noatime 0 0
/dev/hda2 /home ext3 rw,noatime,data=writeback 0 0
/dev/hda3 /media/multimedia ext3 rw,noatime,data=writeback 0 0
/dev/hda7 /media/storage ext3 rw,noatime,data=writeback 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
**/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=username 0 0**

```

Thought so, the mount command stores it's data in /etc/mtab and only shows the partitions (mount points) that are mounted at the time you look at the file or run the "mount" command just as you did.


Im confused now what am I supposed to do?

Also do you think Reinstalling LInux would help any at all?

---

### Post by southernman on 2007-09-01
> **Azerial said:**
> Im confused now what am I supposed to do?

*shrugs* ummm... post the output I've asked you for already. Yeah, that's a good place to start. :p

lspci and lsmod - post the output of those two commands.

Being a fresh install, have you run all the updates for a new installation? 

Don't forget the output you've been asked for... to try and help *you.*

---

### Post by Azerial on 2007-09-01
> **southernman said:**
> *shrugs* ummm... post the output I've asked you for already. Yeah, that's a good place to start. :p

lspci and lsmod - post the output of those two commands.

Being a fresh install, have you run all the updates for a new installation? 

Don't forget the output you've been asked for... to try and help *you.*

mike@Azerial:~$ ispci
bash: ispci: command not found
mike@Azerial:~$ ismod
bash: ismod: command not found
mike@Azerial:~$ 


apparently those commands dont exist

sorry misread, your L's look like i's to me
mike@Azerial:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Ethernet (rev 10)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

mike@Azerial:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
powernow_k8            16064  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
button                  8720  0 
asus_acpi              17308  0 
sbs                    15652  0 
battery                10756  0 
dock                   10268  0 
backlight               7040  1 asus_acpi
container               5248  0 
i2c_ec                  6016  1 sbs
ac                      6020  0 
video                  16388  0 
ipv6                  268960  10 
nls_utf8                3072  1 
ntfs                  107764  1 
lp                     12452  0 
fuse                   46612  0 
snd_usb_audio          79744  0 
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
af_packet              23816  2 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbhid                 26592  0 
agpgart                35400  0 
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hid                    27392  1 usbhid
i2c_core               22656  1 i2c_ec
pcspkr                  4224  0 
gspca                 607824  0 
k8temp                  6656  0 
videodev               28160  1 gspca
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
parport_pc             36388  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
snd                    54020  14 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
parport                36936  3 ppdev,lp,parport_pc
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  4 
amd74xx                15260  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0 
ahci                   22020  0 
r8169                  32392  0 
floppy                 59524  0 
sata_nv                20868  3 
libata                125720  3 ata_generic,ahci,sata_nv
scsi_mod              142348  3 sg,sd_mod,libata
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  7 snd_usb_audio,snd_usb_lib,usbhid,gspca,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by southernman on 2007-09-01
> **Azerial said:**
> mike@Azerial:~$ ispci
bash: ispci: command not found
mike@Azerial:~$ ismod
bash: ismod: command not found
mike@Azerial:~$ 


apparently those commands dont exist
the commnds start with an "l" not an "i" - a lower case L to be precise.

---

### Post by Azerial on 2007-09-01
> **southernman said:**
> the commnds start with an "l" not an "i" - a lower case L to be precise.

I noticed that mistake and edited my previous post with the answer

But anyway I'll repost

mike@Azerial:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Ethernet (rev 10)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

mike@Azerial:~$ lsmod
Module Size Used by
binfmt_misc 12680 1
rfcomm 40856 0
l2cap 25856 5 rfcomm
bluetooth 55908 4 rfcomm,l2cap
ppdev 10116 0
powernow_k8 16064 1
cpufreq_powersave 2688 0
cpufreq_conservative 8200 0
cpufreq_stats 7360 0
cpufreq_ondemand 9228 1
freq_table 5792 3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace 5408 0
sony_acpi 6284 0
dev_acpi 12292 0
pcc_acpi 13184 0
tc1100_wmi 8068 0
button 8720 0
asus_acpi 17308 0
sbs 15652 0
battery 10756 0
dock 10268 0
backlight 7040 1 asus_acpi
container 5248 0
i2c_ec 6016 1 sbs
ac 6020 0
video 16388 0
ipv6 268960 10
nls_utf8 3072 1
ntfs 107764 1
lp 12452 0
fuse 46612 0
snd_usb_audio 79744 0
snd_usb_lib 17280 1 snd_usb_audio
snd_hwdep 9988 1 snd_usb_audio
snd_hda_intel 21912 1
snd_hda_codec 205056 1 snd_hda_intel
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_ oss
snd_seq_dummy 4740 0
snd_seq_oss 32896 0
snd_seq_midi 9600 0
snd_rawmidi 25472 2 snd_usb_lib,snd_seq_midi
af_packet 23816 2
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
usbhid 26592 0
agpgart 35400 0
snd_timer 23684 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
hid 27392 1 usbhid
i2c_core 22656 1 i2c_ec
pcspkr 4224 0
gspca 607824 0
k8temp 6656 0
videodev 28160 1 gspca
v4l2_common 25216 1 videodev
v4l1_compat 15236 1 videodev
parport_pc 36388 1
shpchp 34324 0
pci_hotplug 32576 1 shpchp
snd 54020 14 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_hda_code c,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,sn d_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8672 1 snd
snd_page_alloc 10888 2 snd_hda_intel,snd_pcm
parport 36936 3 ppdev,lp,parport_pc
tsdev 8768 0
evdev 11008 4
ext3 133128 1
jbd 59816 1 ext3
mbcache 9604 1 ext3
sg 36252 0
sd_mod 23428 4
amd74xx 15260 0 [permanent]
generic 5124 0 [permanent]
ata_generic 9092 0
ahci 22020 0
r8169 32392 0
floppy 59524 0
sata_nv 20868 3
libata 125720 3 ata_generic,ahci,sata_nv
scsi_mod 142348 3 sg,sd_mod,libata
ehci_hcd 34188 0
ohci_hcd 22532 0
usbcore 134280 7 snd_usb_audio,snd_usb_lib,usbhid,gspca,ehci_hcd,oh ci_hcd
thermal 14856 0
processor 31048 2 powernow_k8,thermal
fan 5636 0
fbcon 42656 0
tileblit 3584 1 fbcon
font 9216 1 fbcon
bitblit 6912 1 fbcon
softcursor 3200 1 bitblit
vesafb 9220 0
capability 5896 0
commoncap 8192 1 capability

---

### Post by Azerial on 2007-09-01
Bump, I still need a fix desperately

---

### Post by Azerial on 2007-09-01
Bump... sorry if Im bumping too much BUT I JUST CANT GET IT TO WORK

I just reinstalled LInux hopeing that would fix it.

IT still does not work Please help me!!!! I Dont want to give up on Linux but I'll have to if I cant use my CD/DVD Drive at all!

---

### Post by Azerial on 2007-09-02
Bump, PLease someone tell me how to fix this and make my drive exist to Linux!!!!

---

### Post by southernman on 2007-09-02
[http://ubuntuforums.org/showthread.php?t=540556]("http://ubuntuforums.org/showthread.php?t=540556")

Have a look at ^^^ that thread. At this point it's all I can offer for help. Good luck.

---

### Post by Azerial on 2007-09-02
> **southernman said:**
> [http://ubuntuforums.org/showthread.php?t=540556]("http://ubuntuforums.org/showthread.php?t=540556")

Have a look at ^^^ that thread. At this point it's all I can offer for help. Good luck.

that dosent help me at all :(

---

### Post by al108 on 2007-09-03
You know I have a similar problem, let me see if it's something easy to fix.

---

### Post by Azerial on 2007-09-03
> **al108 said:**
> You know I have a similar problem, let me see if it's something easy to fix.

I hope its easy to fix, Its killing me not having a CD Drive

---

### Post by al108 on 2007-09-04
Alright, the fix I used for myself was pretty easy, but you may or may not like it.

I dug for a little bit into the problem with CD-ROM drives being not recognized and found that a lot of people were able to fix it by changing setting in their BIOS setup. You may want to try that first. Look for settings for you CD-ROM on the main page - if it says AUTO try changing it to something else (CD-ROM) and see what happens. Sometimes under different sections you may also find setting for you IDE and SATA - try playing with that.

After I looked at the output of dmesg, lspci, lshw on my laptop I concluded that perhaps I would need either change in BIOS setup or a driver. And since my BIOS setup only allows me to change AHCI on/off I've decided to keep it ON.

So playing with BIOS setup was not an option for me, because on my laptop I couldn't change much at all. I've downloaded Gutsy CD and it worked. Installation was a breeze too. With the release being around the corner most of everything works just fine in Gutsy.

I hope it works for you too.

---

### Post by Tavathlon on 2007-09-25
Hm, I'm bumping this thread a little bit..what it would have looked like in Feisty, since it was not possible to install Feisty at all on this machine. So I'm sorry, but this problem is not automatically solved by installing Gutsy...  =/

I have not yet tried to play around in bios, I'll wait with that until my home-exam is done and handed in, but I will try it within a week at least.

When I first got the error message about /dev/scd0 does not exist, I went to /dev and took a look around -and quite correctly, there where no such file. Anyone who knows if there is an easy way to come around this problem?

Peace..

/ Patrik

---

### Post by Bob Burd on 2007-09-26
I'm having the same problem. Far as I can tell, ubuntu Feisty install is setting all my drives to scsi even though they are all IDE, including my CDROM. The Hard Drive seems to work ok with this setting, but the CDROM does not. It can play audio CDs, but it cannot view data CDs. Guess it's time to try playing with the BIOS settings... My system hardware is about 5 years old. I suspect that has something to do with it as well...

---

### Post by Bob Burd on 2007-09-26
Dang it, I can't find anything in the BIOS settings to tweak with. If anybody's got a clue how to force the install to recognize the IDE drives as ide rather than scsi, it would be most appreciated...
thanks in advance.

---

### Post by Tavathlon on 2007-09-26
I'm sorry, Bob Burd, but I'm not really the right person to ask about that kind of things... >.<

I managed to solve the problem now anyway, by following the advice about fiddling on BIOS - I changed the cdrom setting from 'auto' to 'user', and then it worked. Seems to be the way to solve the problem, at least when the problem is that the disc drive is not accessible at all.

Good luck Bob Burd, I hope there will be a solution for you...

---

### Post by leomelo on 2008-02-20
I 'm gonna tell you how i solved this problem. I turn off my pc.Then i disconnected the IDE cable and the power cable of the cdrom drive. Then turn on the pc without the cdrom drive. After it loaded the session. i turn it off and i connected the cdrom drive again. And when i turn it on : Eureka! : the dvd within the cdrom drive was detected!
    I have an Intel pentium D (dual core), Intel desktop board D945GTP,  a cdrom drive Sang Sung and two hdd sata.
    Let me say this : Richard Stallman, love and gratitude for you and for all the other free and  open source developers. God bless all of you!

---

