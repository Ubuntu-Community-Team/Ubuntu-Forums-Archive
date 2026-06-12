---
title: "Sound Prob."
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ercanbozi on 2007-04-11
Hi Everybody,
Ive A Sound Problem On My Laptop.
Problem Is:
My Audio And Video Files R Playing But No Sound.
Thanks For Help To E.body

---

### Post by LaurelLynn on 2007-04-11
Dear ercanbozi,

Sound can be tricky to get working, because it can be blocked in several places.

Lets assume for the moment your driver is working. (it might not be)

First your laptop has a dial for volume.

Then the operating system has volume settings.  Look for a little icon that looks like a speaker on one of the bars at the top or bottom of your desktop.  Click once on it to get a volume slider and adjust the volume.

Last the sound and video programs that run will have a similar volume control.

If any one of these is turned down, it can kill all the volume.

Only after checking these do I start to look at the sound card and it´s drivers.

---

### Post by ercanbozi on 2007-04-11
thank u but,
&#305;ve done them before,
nothings changed,
anything else!

---

### Post by Sef on 2007-04-11
From the terminal do the following:

gksudo gedit /etc/modprobe.d/alsa-base

and post the results here.

---

### Post by ercanbozi on 2007-04-11
result is below:

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

---

### Post by ercanbozi on 2007-04-11
also first result is:

ercanbozi@ercanbozi-laptop:~$ gksudo gedit /etc/modprobe.d/alsa-base
(gedit:6694): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

