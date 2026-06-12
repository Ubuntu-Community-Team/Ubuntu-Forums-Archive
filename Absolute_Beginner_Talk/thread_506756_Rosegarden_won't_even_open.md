---
title: "Rosegarden won't even open"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-07-22
Hi,
I've installed Rosegarden via Synaptic Package Manager, which created a menu item under Applications -> Sound & Video for Rosegarden. However, it won't open at all... nothing happens - the program simply doesn't run. Is there any way of figuring out what's going on?
Thanks to all who respond...
Cheers,
Robyn

---

### Post by Robynsveil on 2007-07-22
As usual, I left half of what I've got working out... sorry about that. I have managed to install qsynth and JACK and have them running. I've also installed Timidity, and can play back MIDIs (what an unusual interface!) but can't figure out how to do any sequencing in this program.

All I want to do is what I did in Cakewalk Pro Audio 8. I was able to write music in a staff and notation format, and associate sound fonts so I can hear what it's sound like... was told Rosegarden was the way to go in Linux. If anyone can suggest another program, I'm flexible.

---

### Post by Robynsveil on 2007-07-22
Oh *AND* I figured out I have a second sound card - the one on the motherboard, which I disabled in the BIOS - which ALSA sets up as the default card... might have something to do with it. Any way to definitively disable this sound card in Ubuntu? Like in the /etc/modprobe.d/alsa-base file? Not sure what to put in there, AlsaMixer (run from Terminal) sees the my AudigyZS soundcard as a card, and the Sigmatel STAC9721,23 as a chip. Like I said before, even though it's disabled in the BIOS, the Sigmatel still shows up in Ubuntu.

By the way, my alsa-base file has:
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
mpu_port=0x330

Thanks everyone.

---

### Post by Robynsveil on 2007-07-22
This problem seems deeper than I first thought. Apparently others have experienced the problem where the onboard sound is selected by Ubuntu as the default sound, regardless of whether it's been disabled in the BIOS or not. In Launchpad this problem was rewarded with a Bug Number 66210 - I followed one of the suggestions:
> robyn@Flight:~$ asoundconf list
Names of available sound cards:
Audigy2
robyn@Flight:~$ asoundconf set-default-card Audigy2

which made nil difference to GnomeALSAMixer - it *still* has the Sigmatel inboard sound as default after reboot.

The thread on the Launchpad site seems to end with the issue unresolved. Anyone know if this has been fixed, or if a workaround exists until they get the kernel fixed?

Cheers,
Robyn

---

