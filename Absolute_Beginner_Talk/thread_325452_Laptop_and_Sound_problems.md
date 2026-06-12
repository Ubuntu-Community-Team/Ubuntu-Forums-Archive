---
title: "Laptop and Sound problems"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by eamonn on 2006-12-25
Hi,

I've been running Ubuntu for a while but since I'm a full time student and I have a full time job I seldom have the time to work on my computer. But I'm on break so now I have the time. I haven't had sound on my laptop since I put ubuntu on. I installed Automatix and the multimedia codecs it recommended ant still nothing. I went to the Ubuntu Guide to look for help and I found out how to figure out what sound card I'm running. My available soundcard is " I82801DBICH4 "

What do I do?

---

### Post by Sef on 2006-12-25
Open the terminal and type these commands:

```
sudo /proc/asound/cards
```

```
gksudo gedit /etc/modprobe.d/alsa-base
```

Then copy and paste them here.

---

### Post by eamonn on 2006-12-25
```
sudo /proc/asound/cards
```

it said command not found.

```
gksudo gedit /etc/modprobe.d/alsa-base
```

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

### Post by eamonn on 2006-12-25
anyone?

---

### Post by Azakus on 2006-12-25
Sef meant "cat /proc/asound/cards".
Anyway try this: [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by SoloSalsa on 2006-12-25
> **Azakus said:**
> Sef meant "cat /proc/asound/cards".
Anyway try this: [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")
I was just going to give the same link!  Definitely go there, it is, accurately, *comprehensive*.

---

### Post by eamonn on 2006-12-26
Well, I went through that comprehensive sound problem thing. I ended up reinstalling the alsa drivers from a fresh kernal and it still didn't work. Iwent through the general help section again. I *think* ubuntu is detecting my soundcard and I *think* I found the driver listed on [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) 

Step number four is confusing: >  Now go back to the shell and type sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]. For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx. 

What exactly do I type in for my soundcard? I think it's "ICH4- Intel 82801DB-ICH4 or
Intel 82801DB-ICH4 with AD1981B at 0xe0100c00, irq 10" but I don't type in all of that do I?

---

### Post by eamonn on 2006-12-26
.

---

### Post by SoloSalsa on 2006-12-26
Sorry, I do not know anything beyond that guide.  Surely someone else in the community will assist you, though.
Oh, but I do suggest you move this thread to the [hardware ]("http://ubuntuforums.org/forumdisplay.php?f=135")section or the [multimedia ]("http://ubuntuforums.org/forumdisplay.php?f=138")section.

---

