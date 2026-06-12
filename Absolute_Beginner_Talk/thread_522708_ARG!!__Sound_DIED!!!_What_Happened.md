---
title: "ARG!!  Sound DIED!!! What Happened??"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by morequarky on 2007-08-10
I am in Dapper 6.06...I tried installing an HP package off of sourceforge and MY SOUND DIED!!!   How do I get it back!!! PLEASE!!!

THANK YOU GREATLY....It says some gstreamer is missing???  Why would HP mess with SOUND!!!   I am frantic.  How do I get this working again!!

---

### Post by tdrusk on 2007-08-10
why not take what the gstreamer is missing, search for it in synaptic, and install it?

---

### Post by morequarky on 2007-08-10
Nice idea!  I went to synaptic and reinstalled a bunch of stuff, rebooted even, though it shouldn't need it and it still doesn't work.  It is vague, it doesn't state exactly what is missing.  Needs some plug in??? Do you know the exact name of the Gstreamer gnome plugin???   It isn't just a browser issue.  Mplayer won't work either.


THanks for your suggestion.

---

### Post by morequarky on 2007-08-10
It's like the onboard sound section of my motherboard DIED!!!  How's that possible?  35C isn't THAT HOT!!

---

### Post by DeHorde on 2007-08-11
Okay, first but formost: take a chill pill. Walk away for 30 minutes or go:
 I must not fear.
    Fear is the mind-killer.
    Fear is the little-death that brings total obliteration.
    I will face my fear.
    I will permit it to pass over me and through me.
    And when it has gone past I will turn the inner eye to see its path.
    Where the fear has gone there will be nothing.
    Only I will remain.
;)

I'm running feisty, so some things might be different, but after that, try something like ```
aplay /usr/share/sounds/login.wav
``` on the command line. 
Next,  is esd running, are your modules loaded, are you still in the right group (audio)? 
```
ps aux |grep esd
lsmod |less 
groups

```
There could be a lot of things wrong, but if these things don't turn up anything, I suggest looking at your hardware (everything connected? does an mp3-player work on your boxes?).  Seriously, I once kept myself busy a whole evening, until finally I checked the cable going  into my stereo.... :D

Also, what kinda software were you trying to install? Maybe someone knows something when you're more precise

---

### Post by morequarky on 2007-08-11
> **DeHorde said:**
> Okay, first but formost: take a chill pill. Walk away for 30 minutes or go:
 I must not fear.
    Fear is the mind-killer.
    Fear is the little-death that brings total obliteration.
    I will face my fear.
    I will permit it to pass over me and through me.
    And when it has gone past I will turn the inner eye to see its path.
    Where the fear has gone there will be nothing.
    Only I will remain.

I'm running feisty, so some things might be different, but after that, try something like ```
aplay /usr/share/sounds/login.wav
``` on the command line. 
Next,  is esd running, are your modules loaded, are you still in the right group (audio)? 
```
ps aux |grep esd
lsmod |less 
groups

```
There could be a lot of things wrong, but if these things don't turn up anything, I suggest looking at your hardware (everything connected? does an mp3-player work on your boxes?).  Seriously, I once kept myself busy a whole evening, until finally I checked the cable going  into my stereo.... 

Also, what kinda software were you trying to install? Maybe someone knows something when you're more precise

command: aplay /usr/share/sound/login.wav
ALSA lib confmisc.c:672: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3493: ( _snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072: (snd_func_refer) error evaluating name
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device

Command: ps aux | grep esd
wes       6181  0.0  0.1   3956   912 pts/0    R+   06:52   0:00 grep esd

Module                  Size  Used by
binfmt_misc            15248  1
rfcomm                 45600  0
l2cap                  30464  5 rfcomm
bluetooth              59396  4 rfcomm,l2cap
ppdev                  11400  0
cpufreq_userspace       9184  0
cpufreq_stats           8264  0
freq_table              6464  1 cpufreq_stats
cpufreq_powersave       3328  0
cpufreq_ondemand        9768  0
cpufreq_conservative    10984  0
video                  18824  0
tc1100_wmi              9096  0
sony_acpi               7188  0
pcc_acpi               16128  0
hotkey                 13768  0
dev_acpi               15364  0
container               6272  0
button                  8864  0
acpi_sbs               24600  0
battery                12296  1 acpi_sbs
ac                      7176  1 acpi_sbs
i2c_acpi_ec             7040  1 acpi_sbs
nls_iso8859_1           6656  1
nls_cp437               8320  1
vfat                   16768  1
fat                    58032  1 vfat
ipv6                  300416  14
dm_mod                 63176  1
md_mod                 76792  0
af_packet              28172  2
lp                     15040  0
snd_seq_dummy           5508  0
snd_seq_oss            38372  0
snd_seq_midi           11456  0
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                64088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                  10240  0
usblp                  16128  0
parport_pc             40816  1
parport                44172  3 ppdev,lp,parport_pc
floppy                 74120  0
snd_via82xx            32936  0
gameport               19216  1 snd_via82xx
snd_ac97_codec        110396  1 snd_via82xx
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
shpchp                 51360  0
pci_hotplug            33168  1 shpchp
snd_pcm               104584  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              29064  2 snd_seq,snd_pcm
snd_page_alloc         13968  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10368  1 snd_via82xx
snd_rawmidi            31648  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device         11280  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
via_rhine              28164  0
mii                     7680  1 via_rhine
psmouse                40324  0
serio_raw               9732  0
snd                    68576  11 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
pcspkr                  3592  0
soundcore              13216  1 snd
i2c_viapro             11416  0
i2c_core               26624  2 i2c_acpi_ec,i2c_viapro
sg                     43696  0
sd_mod                 21504  0
evdev                  14464  1
usb_storage            82240  0
ext3                  146448  3
jbd                    70952  1 ext3
ide_generic             2816  0
ehci_hcd               36232  0
uhci_hcd               36640  0
usbcore               147132  5 usblp,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 35744  0
cdrom                  41144  1 ide_cd
ide_disk               19456  6
via82cxxx              10884  0 [permanent]
generic                 7300  0
sata_via               12036  0
libata                 85536  1 sata_via
scsi_mod              160632  4 sg,sd_mod,usb_storage,libata
thermal                16524  0
processor              29736  1 thermal
fan                     6408  0
capability              7176  0
commoncap               9728  1 capability
vga16fb                15120  1
cfbcopyarea             5120  1 vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4224  1 vga16fb
cfbfillrect             5760  1 vga16fb
fbcon                  43136  72
tileblit                4096  1 fbcon
font                    9984  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit


command: groups
wes lp admin

I have no idea if this is a hardware problem or driver problem or what.  Like I said originally there was some software I tried to install and after rebooting my sound didn't work.  So perhaps the software caused the problem.  The software I tried to install was hplip-2.7.7.run It is an installer for some HP printer drivers I got it off of sourseforge.

One other note that shouldn't matter.  I have three OS's on this computer.  I have xp professional(english) and xp home(korean) installed on their own partitions.  Well, I nuked the Xp professional partition at the same time I was installing the HP software using gparted.  This is another huge problem for me because now I can't boot the remaining xphome partition.  But I can't see how nuking a Fat32 windows partition should effect Ubuntu.  Ubuntu shouldn't have anything on that partition.

Ok. So that's the whole story.  Thanks for your help.

---

### Post by morequarky on 2007-08-11
When Ubuntu boots, it brings me to the login screen.  When the login screen appears it makes some beeps through my speakers.  THat is the last sound it makes.  I can't get a peep out of it otherwise

---

### Post by DeHorde on 2007-08-11
okay, there's one thing sticking out like a sore thumb: you are not in the audio group.. that would make your soundcard inaccesible, which would in turn give you the errors you see when you run aplay /path/to/sound.wav.

But thats not all the groups you are missing. An admin should have something like:

users adm dialout fax cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner fuse admin

I'm using fuse, but thats not default. Not sure about the other groups like these in feisty compared to dapper either. 
Add yourself to these groups (you are still admin, luckily, and that group is the one that allows you to sudo) like so (I take it from your groups output your username is wes):
```
sudo adduser wes audio
```
keep repeating this for all the other groups you need to be in. You can see the groups on your systems through 
```
cat /et/group 
```
You have to log out and back in for these to groupsettings to take effect, I think. 

There is ofcourse an easier way with  "usermod -a -G", but you might want to fiddle with that on a testaccount before you try that one out on your main admin account ;)

Good luck, and let us know if it worked! 
By the way, for a desktop, feisty is way better than dapper.. why not try that one? It also has hplip build in, even though it only is 1.7.3 according to apt-get...

---

### Post by morequarky on 2007-08-12
Great...I'll get to work on that.  Your awesome.  I don't know how the HP installer took me out of the groups I needed to be in.  Anyways.  Great.  I'll try this and get back to ya.

---

### Post by morequarky on 2007-08-12
Ok here is what I did to fix it.  Your info told me I was not in the correct groups so I went to the user menu in system settings and sure enough the GUI told me I was not in but a few groups...I added myself to all the groups on the list and should have relogged but rebooted...it worked.  I am back up and running again.  THANKS.  

(I firmly believe that the people on this board know basically everything in the world about computers; makes me think of the borg.)

---

### Post by DeHorde on 2007-08-12
Resistance is futile... You will be ubuntufied :P

Anyway, of course there's a gui method to this, I tend to overlook those. Good to hear everything is working again and have fun!

---

