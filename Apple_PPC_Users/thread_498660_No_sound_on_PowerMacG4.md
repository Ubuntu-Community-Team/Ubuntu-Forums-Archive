---
title: "No sound on PowerMacG4"
date: 2007-07-11
forum: Apple PPC Users
---

### Post by schmod on 2007-07-11
Hi,

I'm having trouble making my PowerMac G4 make any sound whatsoever.   VLC is silent, and programs like Totem just crash.

/proc/cpuinfo
```
processor       : 0
cpu             : 7450, altivec supported
clock           : 733.333331MHz
revision        : 0.0 (pvr 8000 0200)
bogomips        : 66.30
timebase        : 33290001
platform        : PowerMac
machine         : PowerMac3,4
motherboard     : PowerMac3,4 MacRISC2 MacRISC Power Macintosh
detected as     : 69 (PowerMac G4 Silver)
pmac flags      : 00000010
L2 cache        : 256K unified
pmac-generation : NewWorld
```

lsmod
```
Module                  Size  Used by
binfmt_misc            13672  1 
rfcomm                 46076  0 
l2cap                  26020  5 rfcomm
bluetooth              65420  4 rfcomm,l2cap
uinput                 11264  2 
ppdev                  11268  0 
lp                     13580  0 
parport                44304  2 ppdev,lp
radeon                144776  2 
drm                    96920  3 radeon
cpufreq_conservative     8096  0 
cpufreq_stats           6436  0 
cpufreq_userspace       5332  0 
cpufreq_powersave       2048  0 
cpufreq_ondemand        9160  0 
ipv6                  307884  14 
sbp2                   25188  0 
scsi_mod              181324  1 sbp2
apm_emu                 8012  1 
snd_powermac           49984  3 
fuse                   52820  1 
snd_aoa_i2sbus         24292  0 
snd_pcm_oss            53984  0 
snd_mixer_oss          20960  2 snd_pcm_oss
snd_pcm                95812  4 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11368  1 snd_pcm
snd_seq_dummy           4004  0 
snd_seq_oss            40660  0 
snd_seq_midi           10016  0 
snd_rawmidi            29632  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
snd_seq                61888  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26404  3 snd_pcm,snd_seq
snd_seq_device          9388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69812  12 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  2 snd
snd_aoa_soundbus        7812  1 snd_aoa_i2sbus
pmac_zilog             21140  0 
serial_core            24384  1 pmac_zilog
uninorth_agp           12012  1 
agpgart                41308  2 drm,uninorth_agp
af_packet              24936  2 
tsdev                   9056  0 
evdev                  12800  14 
ext3                  159048  1 
jbd                    68488  1 ext3
mbcache                 9572  1 ext3
usbhid                 28996  0 
hid                    43968  1 usbhid
ide_disk               18880  3 
ide_floppy             22144  0 
ide_cd                 36900  0 
cdrom                  47580  1 ide_cd
sungem                 35460  0 
sungem_phy             12128  1 sungem
ohci1394               43152  0 
ieee1394              430800  2 sbp2,ohci1394
ohci_hcd               36100  0 
usbcore               158260  3 usbhid,ohci_hcd
capability              5256  0 
commoncap               7968  1 capability
```


Any suggestions?

---

### Post by shawnhcorey on 2007-07-11
I'm having the same problem.  I have a PowerBook G4 and I'm running 7.04.  But this is not the first time I had problems with the sound. See [http://ubuntuforums.org/showthread.php?t=281100](http://ubuntuforums.org/showthread.php?t=281100)

No-one had an answer then.  I expect that the sound driver is not loaded but I have no idea where to get the correct one.

---

### Post by stmiller on 2007-07-11
Could be related to this horrible bug seen in older G4 powerbooks and emacs:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

---

### Post by schmod on 2007-07-12
Well, it's a 733mhz G4 tower ("Digital Audio" generation)....

Sigh... guess I'll be soundless for the time being.

---

### Post by shawnhcorey on 2007-07-12
In other words, not acceptable.

I have already been looking at alternatives.  Ubuntu is dead.

---

### Post by stmiller on 2007-07-12
> **schmod said:**
> Well, it's a 733mhz G4 tower ("Digital Audio" generation)....

Sigh... guess I'll be soundless for the time being.

You can simply fetch an Edgy kernel deb and boot into that kernel and sound will work. I'm running a pre-2.6.20 kernel with Feisty. Read the end of the 'Tibook Feisty' thread on this forum.

shawnhcorey:

What powerbook model do you have? Have you read the PowerPC FAQs?

---

### Post by shawnhcorey on 2007-07-13
> **stmiller said:**
> You can simply fetch an Edgy kernel deb and boot into that kernel and sound will work. I'm running a pre-2.6.20 kernel with Feisty. Read the end of the 'Tibook Feisty' thread on this forum.

That would mean having the Update Manager constantly telling me there's an update.  Of course, I could download the latest version and the drivers I need and compile it myself.  But if I'm going to do that much work, I'll switch to a distro that supports PowerPCs.

> What powerbook model do you have? Have you read the PowerPC FAQs?

It's a Powerbook G4 Aluminum.  I've read some of it.  Is there something specific that you're thinking of?

---

### Post by ajmctaggart on 2007-07-13
Just Try This...

sudo nano /etc/modules

& add this line to end

snd-powermac

save and reboot

Let us know if this solves it...

---

### Post by stmiller on 2007-07-13
> **shawnhcorey said:**
> That would mean having the Update Manager constantly telling me there's an update.  Of course, I could download the latest version and the drivers I need and compile it myself.  But if I'm going to do that much work, I'll switch to a distro that supports PowerPCs.



It's a Powerbook G4 Aluminum.  I've read some of it.  Is there something specific that you're thinking of?

I was replying to the author of this thread RE: getting the Edgy kernel. 

And yes, the PowerPCFAQs has the answer to your question about getting sound going (**Enable sound with my Powerbook**), or looks like ajmctaggart spelled it out for you here.

There is plenty of support for PowerPC with users here. Just ask. Feel free to add me to your yahoo IM. Adios!

---

