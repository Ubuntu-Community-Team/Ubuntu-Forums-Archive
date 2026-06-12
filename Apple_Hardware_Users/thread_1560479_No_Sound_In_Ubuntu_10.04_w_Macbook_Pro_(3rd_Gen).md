---
title: "No Sound In Ubuntu 10.04 w/ Macbook Pro (3rd Gen)"
date: 2010-08-24
forum: Apple Hardware Users
---

### Post by ZamatoElite on 2010-08-24
I have a Macbook Pro (3rd Gen), and the sound will not work in Ubuntu 10.04 LTS. No sound at all!!! 

I have tried everything! Please help. :cry:

---

### Post by furok23 on 2010-08-25
what specifically have you tried?

also, not that your question isnt valid, but there are multiple threads regarding this topic.

---

### Post by linuxopjemac on 2010-08-26
Did you unmute the channels?
```
alsamixer
```
you can toggle between muted and unmuted with "m"

---

### Post by ZamatoElite on 2010-08-28
Thanks for the replies.

I have unmuted everything in alsamixer, but there is still no sound.

By the way, here are the settings I have my sound on:
Hardware: Internal Audio 1 Output/1 Input Analog Stereo Duplex
Output: Internal Audio Analog Stereo
Connector: Analog Output

These are the default settings, but I thought i'd post them to make sure they are all correct.

But as it stands now, I still have ZERO sound. Any more suggestions?

---

### Post by linuxopjemac on 2010-08-29
You might have a look [here]("http://mac.linux.be/content/sound-problems").

---

### Post by ZamatoElite on 2010-08-29
> **linuxopjemac said:**
> You might have a look [here]("http://mac.linux.be/content/sound-problems").

Thanks for the link, but none of the guides pertain to my model. I have a Macbook Pro 3.1 running Lucid Lynx.

Do you guys have any more suggestions or should I give up hope? Is there something I need to do with the ALSA drivers? I'm growing desperate. :(

Thanks.

---

### Post by limotux on 2010-08-29
mm.. my 2 cents..

do you have restricted formats codecs installed? (win32 codecs)
check the mixer settings, sometimes the sound level is reduced on it's own.

---

### Post by linuxopjemac on 2010-08-29
This was the trick for Karmic Koala for your model, let us know if it works in Lucid too:

> A little hack has to be edited to hear something. 

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

scroll down to search snd-hda-intel, add model=mbp3 like this: 
```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp3
```

and save and reboot. 

Update: It looks like this change is no longer needed on Karmic which is up to date (2010-04-03).

You might have to unmute the channels again after reboot...

---

### Post by ZamatoElite on 2010-08-29
> **linuxopjemac said:**
> This was the trick for Karmic Koala for your model, let us know if it works in Lucid too:



You might have to unmute the channels again after reboot...
[B]
I think something is wrong. This is what the text file looks like:[/B]

autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

---

### Post by linuxopjemac on 2010-08-29
Just add that line I gave you at the end of the alsa-base.conf file. You have to scroll down until the very end.

---

### Post by linuxopjemac on 2010-08-29
These are my last lines of that same file:

```
...............
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

---

### Post by ZamatoElite on 2010-08-29
> **linuxopjemac said:**
> These are my last lines of that same file:

```
...............
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

Still no sound. I pasted this to the end of the file, saved, and rebooted:

**options snd-hda-intel power_save=10 power_save_controller=N model=mbp3**

But still nothing. I've even checked my alsamixer to make sure everything was unmuted. Do you have any other ideas?

---

### Post by linuxopjemac on 2010-08-30
yeah, switch to another kernel. I know that in Karmic Koala for some reason only 2.6.31-19 worked at some point. You may have to try a few kernels in Lucid. This is trial and error though.

---

### Post by scorp123 on 2011-07-26
> **linuxopjemac said:**
> Did you unmute the channels?
```
alsamixer
```
you can toggle between muted and unmuted with "m"

Bump.

I found your posting via Google. Thanks a lot!*It helped.*My front speakers were muted (MacBook Pro 5,4) and with "alsamixer" I was able to unmute them.

Thank you very much.

---

### Post by Crossle Song on 2013-04-26
I set MM via  alsamixer, but it's no work.....

---

