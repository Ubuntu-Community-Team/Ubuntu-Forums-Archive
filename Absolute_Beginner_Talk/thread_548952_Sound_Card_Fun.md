---
title: "Sound Card Fun"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by bla687 on 2007-09-11
EDIT: I fixed the problem. Ubuntu was just screwing with my defaults. I just defined them in the alsa-base and it woks fine now.

Alright, here's my problem. A little while ago I couldn't get any sound out of my computer in Ubuntu (64-bit, dual boot, creative labs sound card), but all I had to do was unmute the surround sound channels in alsamixer, so that wasn't too bad. Everything was going great for about a day, but just recently while I was working, all programs immediately shut down and I was logged out (edit: I've found this is done with the shortcut shift+backspace, which is really annoying. Does anyone know how to disable this?). When I logged back in, I had no sound, so I checked alsamixer to see if the channels were re-muted for some reason, only to discover that alsamixer now thinks I'm using a realtek card instead of my creative labs card. Here's the contents of my /etc/modprobe.d/alsa-base file, just in case it helps:

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

Does anyone know how to get it to use the sound card that exists again?

Thanks!

---

### Post by ryanVickers on 2007-10-03
> EDIT: I fixed the problem. Ubuntu was just screwing with my defaults. I just defined them in the alsa-base and it woks fine now.
Then mark this as "solved" (click on thread tool and pick it)

---

