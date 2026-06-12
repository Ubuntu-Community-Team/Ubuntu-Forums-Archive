---
title: "Help! What Does Error Message Mean?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Ambimom on 2006-08-21
HELP! :???: In my never-ending struggle to get Ubuntu to boot to the correct sound card, I once again jumped into the breach and followed the instructions provided in the Comprehensive Sound Guide.  First I installed fresh sound kernel; and then step-by-step followed the advice. 

After I rebooted, voila! the correct sound card was in my preferences....however, I noted the following error message:
> ambimom@Ambimom-Linux:~$  sudo nano /etc/modules
ambimom@Ambimom-Linux:~$ sudo modprobe snd-
WARNING: /etc/modprobe.d/alsa-base.save.2 line 28: ignoring bad line starting with '"options'
FATAL: Module snd_ not found.
ambimom@Ambimom-Linux:~$ sudo modprobe snd-
WARNING: /etc/modprobe.d/alsa-base.save.2 line 28: ignoring bad line starting with '"options'

Should I worry?

The offending passage to which this refers was according to the advice offered in the "Sound Guide" 

> ambimom@Ambimom-Linux:~$ cat /proc/asound/modules
0 snd_intel8x0
1 snd_usb_audio
ambimom@Ambimom-Linux:~$
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-i$install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -$install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modpro$install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { mo$install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { mo$
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { mo$
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -$# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-intel8x10 index=0


HELP!

---

