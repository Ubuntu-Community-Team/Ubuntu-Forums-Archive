---
title: "No sound from headphones on iMac 14,1"
date: 2014-04-16
forum: Apple Hardware Users
---

### Post by vincebs on 2014-04-16
Hello everyone,

I can't seem to get sound to come out of the headphone jack on my iMac. What can I do?
There have been previous threads about sound not working in iMacs since 2009 that suggested that I add the line: "options snd-hda-intel model=imac27_122" to alsa-base.conf but it didn't work for me.

Here's my alsa-base.conf:
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=imac27_122
```

Thanks for your help!

---

### Post by Dreamer Fithp Apprentice on 2014-04-16
You may have already tried this, but if not, you might want to use something like pavucontrol to make sure all the sound settings are what you think they are on the system as opposed to the application - that you aren't muted, that the volume isn't turned all the way down, that the sound output is being routed to the right device. Probably won't be that easy, but it might be.

---

### Post by vincebs on 2014-04-19
pavucontrol says that the volume is fine and routing to the headphones. When I "play" audio, there's a bar in pavucontrol that lights up which matches the sound levels in the audio but no actual sound is coming out. I thought iMacs used a Cirrus Logic audio controller but I don't see that listed in pavucontrol, only HDMI/Displayport.

---

### Post by Dreamer Fithp Apprentice on 2014-04-23
> **vincebs said:**
> I thought iMacs used a Cirrus Logic audio controller but I don't see that listed in pavucontrol, only HDMI/Displayport. I'm not sure what to make of that but it sounds suspicious to me.
Your headphones (which I assume you have checked on some other device to make sure they haven't died on you) are plugged into a round hole, right? I think HDMI means the signal is being sent to a rectangular female (i.e., a hole) connecter that is intended to be used when you want to send both audio and video down the same cable.

If you don't get some useful suggestions here soon, you might start a new thread with a title along the lines of:
"pavucontrol doesn't recognise headphone jack in iMac 14,1". I gather there is no sound card but if I've misunderstood and there is you could append "with WHATEVER-MAKE-MODEL soundcard".  If that IS the problem (and I'm by no means certain) I believe something like that will be more likely to draw the attention of someone who might be able to help.

Or if you want to try something in the meantime you might try searching synaptic or whatever you use to browse the repositories for "audio driver iMac" or "Cirrus Logic" to see if there is another driver you might want to try. I know nothing about Macs. Good luck.

---

### Post by psignosis2 on 2014-07-13
I finally got this working and thought I would share here for anyone else who followed. In my case I have 14.04 on an iMac 13,2. 

I have two displays - the second was connected via thunderbolt cable and dvi adapter. After installing pavucontrol I too saw only HDMI/Displayport - fortunately, I had a thunderbolt to HDMI adapter. I connected the second display using that rather than DVI, then I connected my external speakers which had never been working to the headphones jack on the back of the second display now connected via HDMI. Voila, external speakers working! Then when I connected headphones to the external speakers headphones port, and of course those worked too. Now the volume up/down keys indicate HDMI/Displayport when pressed. Big thanks to vincebs for asking his question here and Dreamer Fithp Apprentice for suggesting pavucontrol which made some connections. So those of you with a second HDMI display might be in luck.

---

### Post by vincebs on 2014-09-10
> **psignosis2 said:**
> I finally got this working and thought I would share here for anyone else who followed. In my case I have 14.04 on an iMac 13,2. 

I have two displays - the second was connected via thunderbolt cable and dvi adapter. After installing pavucontrol I too saw only HDMI/Displayport - fortunately, I had a thunderbolt to HDMI adapter. I connected the second display using that rather than DVI, then I connected my external speakers which had never been working to the headphones jack on the back of the second display now connected via HDMI. Voila, external speakers working! Then when I connected headphones to the external speakers headphones port, and of course those worked too. Now the volume up/down keys indicate HDMI/Displayport when pressed. Big thanks to vincebs for asking his question here and Dreamer Fithp Apprentice for suggesting pavucontrol which made some connections. So those of you with a second HDMI display might be in luck.

Hi psignosis,

Were you able to get the headphones to work from the headphones jack on the back of the iMac itself?

Unfortunately the monitor I have is over 6 years old and only has VGA and DVI, therefore your solution doesn't work for me. What monitor are you using?

---

