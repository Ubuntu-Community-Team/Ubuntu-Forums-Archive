---
title: "Just installed and no sound! Can't find a fix that works"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by hysteresis62 on 2007-01-02
I installed Ubuntu a couple days ago, and I can't get sound up and running.  I had sound before on this computer through Redhat, so I know the hardware's ok.  I read the comprehensive sound troubleshooting post and that helped me discover that:

Ubuntu seems to be picking up my soundcard.  aplay -l gives:

```

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm confused as to why the card is listed twice, though, and I don't know what's up with the subdevices, too.

I've tried fiddling with alsamixer and I have had no luck!  Please help.

The sound card is on-board, and the board is ASUS A7V8X-X

Thanks!
Joe

---

### Post by Sef on 2007-01-02
What do get from this:  ```
cat /proc/asound/cards
``` and post what you get here, please.

---

### Post by hysteresis62 on 2007-01-02
From cat /proc/asound/cards, I get:

```

0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with AD1980 at 0xe000, irq 177

```

Does that mean anything to you?

Thanks very much!
Joe

---

### Post by Sef on 2007-01-02
From the Terminal type this and post here:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by hysteresis62 on 2007-01-02
/etc/modprobe.d/alsa-base reads:

```

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
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

```

---

### Post by Sef on 2007-01-02
This is what I did to get my sound working:

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

In the next to last line, I commented it out.  (To comment out a line, put a # before the beginning of it.  It tells the machine to ignore that line.)

Next in the last line, I changed the 2 to a 0.

So now it looks like this:

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0

---

### Post by hysteresis62 on 2007-01-02
No good.  It didn't work.  The relevant portion of /etc/modprobe.d/alsa-base now reads

```

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0

```

as desired, but on restart I still have no sound.  Any other ideas? Or are there any symptoms of what might be wrong from the files I've posted?

Thanks very much,
Joe

---

### Post by Sef on 2007-01-02
Sorry it didn't work.  I don't have any other ideas now.   Will let you know, if i get another idea.

---

### Post by carlosfocker on 2007-01-05
when your in alsamixer what is PCM set to?

---

### Post by hysteresis62 on 2007-01-07
PCM is unmuted at 81.  Is it supposed to be something else?

Thanks!
Joe

---

### Post by ekka on 2007-01-07
I had the same problem with my Edgy, which i recently installed. Being new to Linux (still learning how to pronounce it!) after ](*,) came to know that there's something called alsamixer. What I did is opened alsamixer and unmuted all of them including system speaker, left, right....i don’t know which one did the trick but its working now! :-D

---

### Post by hysteresis62 on 2007-01-07
Yeah,  I tried that too.  In fact, I even installed the latest version of alsamixer from their website, which says it supports my card, and I tried again, but still no luck.  I feel much like you did, at this point ( ](*,) ).  I wish there was someone out there who could help me.  I'm all for personal research--I've been doing that for this problem for a while, and I'll do it more, but I'm starting to lose hope. 

Joe

---

### Post by hysteresis62 on 2007-01-07
Problem solved!  

I just had to plug the speakers into a different one of the three sound jacks coming off the motherboard!

I feel both dumb and very happy.

At least I now have the latest, greatest version of alsamixer.

It does seem that this is a common problem with my particular onboard soundcard (ATI VT8237).  I think I'm going to suggest an update to the comprehensive sound troubleshooting post.

Cheers,
Joe

---

### Post by Maxcribbin on 2007-01-07
LOL its always the simpilist things we overlook!

oh well... i bet u learned alot about sound drivers?

Carl.

---

### Post by hysteresis62 on 2007-01-07
I was just so used to it coming from the other jack, as it did under redhat, I never expected it to be different under Ubuntu. 

I did pick up some information about drivers, and about the alsa project, which is very cool, btw...those guys work hard.

---

### Post by carlosfocker on 2007-01-08
No thats where it should be.   I would say a reload is in order (Lazy mans answer).

---

### Post by carlosfocker on 2007-01-09
Sorry that last post was a little late.  Figures it was plugged in wrong.  Time to go back and take troubleshooting 101.

---

