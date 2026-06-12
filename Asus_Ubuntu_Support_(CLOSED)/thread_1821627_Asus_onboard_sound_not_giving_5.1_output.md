---
title: "Asus onboard sound not giving 5.1 output"
date: 2011-08-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by solouko on 2011-08-09
Hi, just installed Ubuntu for the first time on my main PC and I can only get stereo (2.0) sound output.

The audio is the on-board audio on from [P5G41C-M LX]("http://uk.asus.com/Motherboards/Intel_Socket_775/P5G41CM_LX/") motherboard 

I've been running this board for the last year under windows XP and it's given great surround sound.  I've switched it over now and it's as if it's not designed for surround sound.

Now, I know it's not a normal surround sound set-up because it expands the other channels to the headphones and microphone jacks, Is this function currently unavailable under Ubuntu? 

Current Ubuntu version is 10.4 64bit

Ok, I'll continue to work on this and update my findings, I did forget to mention that I've tried installing a creative X-Fi card as well, but that doesn't work either, but I didn't work under windows so I'm going to ignore it.
    
I ran this to find specifics of the on-board sound:

      
```
aplay -l | grep card
```This is what if returned:
     ```

     card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
card 3: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
card 3: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
```I'm assuming that the on-board audio is devices 0 and 1 (VT1708S) currently, that's no help to me, but it may be to you.

I've found this link
[http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html](http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html)

I entered this line:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```And this was the contents of my alsa-base.conf file

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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```The link then suggested adding the following line:
```
options snd-hda-intel model=generic
```Don't worry I backed up the old file first, just in case.

Ok. that didn't work so I'll change the conf file back.

---

### Post by riveravaldez on 2012-11-07
Have you tried this? » Open the mixer » "Select controls" » Activate "Channel Mode" » Go to the appropriate tab and choose "6ch"

I'm right now on UbuntuStudio12.04 (with Xfce) and some details could be a little different, but I remember doing that on Debian Squeeze with Gnome2.

Regards!

---

