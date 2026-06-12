---
title: "Sound stops working, have to reboot!"
date: 2008-09-03
forum: Apple Hardware Users
---

### Post by biella on 2008-09-03
Hi everyone,

I've got Hardy Heron installed on my Intel MacBook, its great. I love it. Except that I have this one annoying problem.... my sound works fine when I boot up, but then it stops working and the only way I can get it back is by restarting. This typically happens when some sound is done in firefox, after that... it doesn't work anymore.

 I've tried restarting alsa that doesn't work. I close firefox, that doesn't work. I've gone over the install instructions and wiki pages and forum posts for the MacBook, but I am not finding what I am missing.

My /etc/modules has:
fuse
lp
sbp2
applesmc
acpi_cpufreq

My /etc/modprobe.d/alsa-base has:
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

I've tried to manually unload all my sound modules, but I can't unload them all. Specifically, snd_hda_intel says its in use, but I can't tell by what. If I kill every application having everything to do with sound (gnome volume manager, pulseaudio, firefox, etc.) then I can unload the modules, but then I dont know how to get them back. 


I'd love some help, or any ideas!

---

### Post by cyberdork33 on 2008-09-03
From your initial description, I think the problem lies with pulseaudio, not your driver. There are various issues with pulseaudio reported all over ubuntuforums. I can't really help more than that as I haven't had to deal with these issues yet, but that might get you a lead.

---

### Post by h00pla on 2008-09-03
I just installed Hardy on an older eMac (with a PPC CPU) and I have the same problem. It was previously running Ubuntu Gutsy and sound was working fine. 

I have seen the comment about pulseaudio. As for that, one of the first things I did was to disable it and am now using just Alsa. 



I also added the following to /etc/modules:

'snd-powermac'

and I added to /etc/modprobe.d/alsa-base:

'options snd-hda-intel model=auto'

This got the sound to run for about 10 seconds longer before it quits.

I am beginning to think that this may be a kernel issue.

'lspci' won't show a sound card, so I don't know exactly what this beast is running.

---

### Post by SpicyPanda on 2008-09-04
I had this same problem with my laptop, I was using Ubuntu 7.10 then when i upgraded to 8.04 the sound came back and was stable.

---

### Post by Dave_Connor on 2008-09-04
Try using Alsa instead of Pulse.

---

### Post by cyberdork33 on 2008-09-04
> **h00pla said:**
> I just installed Hardy on an older eMac (with a PPC CPU) and I have the same problem. It was previously running Ubuntu Gutsy and sound was working fine. 

I have seen the comment about pulseaudio. As for that, one of the first things I did was to disable it and am now using just Alsa. 
Although it could be related to pulseaudio still, since you are on PPC hardware, you could be in a different boat entirely.

---

### Post by biella on 2008-09-04
> **Dave_Connor said:**
> Try using Alsa instead of Pulse.

How do I get rid of pulse and switch to alsa?

---

### Post by h00pla on 2008-09-04
to disable pulseaudio, go to System --> Preferences --> Sessions and uncheck it in the startup programs tab

---

### Post by h00pla on 2008-09-06
I have **solved** this problem for my old eMac.

Apparently, there is a a problem with kernels higher than 2.6.17-11, so the solution is to downgrade to kernel 2.6.17-11. You can find it here:

[https://launchpad.net/ubuntu/edgy/powerpc/linux-image-2.6.17-11-powerpc-smp/2.6.17.1-11.38](https://launchpad.net/ubuntu/edgy/powerpc/linux-image-2.6.17-11-powerpc-smp/2.6.17.1-11.38)

Just download and install the deb package. It will advise you to install the meta kernel package, but just ignore that and go ahead. It will move your existing kernel to vmlinuz.old and replace it with the older kernel. After this, sound (at least in my case) works fine.

---

