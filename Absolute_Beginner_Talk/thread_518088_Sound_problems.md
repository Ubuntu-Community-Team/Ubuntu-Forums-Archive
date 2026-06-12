---
title: "Sound problems"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by khm123 on 2007-08-05
Did some searching on HK SoundSticks and didn't really find anything much too valuable to me...

anyways, here is my problem:
I have recently installed Feisty and with a bit of playing around, finally got sound to come out of my SoundSticks.  The only place I have been able to produce sound is using the Rhythmbox audioplayer.  Nothing from amarok or from internet radio and such.  Also, when I do have sound working, the Volume Control will see the device as 'SoundSticks' and will adjust the volume correctly, but the volume hotkeys on my keyboard do not work.  They pop up the little display showing the volume level bar changing, but this does not seem to change any of the levels for any of the devices in the volume control.

Any ideas?

Thanks all!

---

### Post by apswartz on 2007-08-05
Are these speakers you plug into a sound card? usb device?

what does the dmesg command output?

---

### Post by khm123 on 2007-08-05
sorry, soundsticks are usb audio devices.

---

### Post by apswartz on 2007-08-05
what does your rhythmbox use for sound output? how is your amarok set up for output?

---

### Post by happyhamster on 2007-08-05
Could you show us the output of the following commands:

cat /proc/asound/cards

cat /proc/asound/modules

cat /etc/modprobe.d/alsa-base

Just copy & paste them into a terminal (Applications-->Accessories-->Terminal), each time followed by enter.

---

### Post by khm123 on 2007-08-07
[COLOR="Red"]*******@*****-desktop:~$ cat /proc/asound/cards**[/COLOR]
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC655 at 0xdc00, irq 19
 1 [SoundSticks    ]: USB-Audio - SoundSticks
                      harman/kardon SoundSticks at usb-0000:00:10.1-1, full speed


[COLOR="Red"]*******@*****-desktop:~$ cat /proc/asound/modules**[/COLOR]
 0 snd_via82xx
 1 snd_usb_audio

**[COLOR="Red"]*****@*****-desktop:~$ cat /etc/modprobe.d/alsa-base[/COLOR]**
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

---

### Post by anewguy on 2007-08-07
I have the same sound "chip"  in my laptop  (via 8237).  If you haven't already, I would suggest trying the following to see if it helps with any of your problems or not:

-double-click the volume control on the top bar

- the volume control should open.  See if it says Volume Control:  Via 8237 (ALSA Mixer).  If not, go to file and change device type, then change to the via 8237.  You'll be back on the main volume control now.  Click "Edit" and "Preferences", then search through the list until you find "External Amplifier".  If it is not checked, click on the box.  Return to the main volume control window.

- click "Switches", find the "External Amplifier" and UNCHECK it.  It seems counter-intuitive but it works for my laptop with the 8237.

Hope this helps on a few of your problems - I know it won't solve them all.:)

---

### Post by happyhamster on 2007-08-12
- You have to set the sound-sticks as the default sound card, by assigning them "index=0" in alsa-base (the current "index=-2" makes sure they are *not* the default card):

sudo nano /etc/modprobe.d/alsa-base

- Add the following lines:


# Added by user.
options snd-usb-audio index=0
options snd-via82xx index=1


- And remove the "options snd-usb-audio index=-2" line by putting a # character before it. So, make it look like:

# options snd-usb-audio index=-2


- Save & exit. (save = ctrl-o, exit= ctrl-x). Reboot.

- If you still have no sound, check Preferences --> Sound if the correct sound devices have been selected.

---

### Post by phactor on 2007-08-24
hello all, I'm **really** new to Ubuntu / Linux (about a week) and I too was having the same problems with my Z-10 USB speakers so I found this thread and followed it.:

[COLOR="RoyalBlue"]- You have to set the sound-sticks as the default sound card, by assigning them "index=0" in alsa-base (the current "index=-2" makes sure they are *not* the default card):

sudo nano /etc/modprobe.d/alsa-base

- Add the following lines:


# Added by user.
options snd-usb-audio index=0
options snd-via82xx index=1


- And remove the "options snd-usb-audio index=-2" line by putting a # character before it. So, make it look like:

# options snd-usb-audio index=-2[/COLOR]

 Some how I deleted/removed the "USB sound card". but now my SB Live! card is working. Is there any way I can get the "USB sound card" back.. So I can make it the default sound card??

[COLOR="Red"]Here[/COLOR] is what I did, I know it's messed up, Can someone tell me where and what to do to fix it?

[COLOR="RoyalBlue"][I]# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe $

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
options snd-via82xx-modem index=-1
[COLOR="Red"]# options snd-usb-audio index=-0[/COLOR]
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
[COLOR="Red"]# Added by user.
options snd-usb-audio index=0
options snd-via82xx index=1
# options snd-usb-audio index=-2
[/COLOR][/I][/COLOR]

---

### Post by Zubzub on 2007-08-25
I remember having sound issues for quite some time now with my kensington laptop dockingstation (usb soundcard) and my build-in laptop soundcard. I´m not new to Linux (I ran ubuntu for 4 months and gentoo for nearly 2 years now) .I remembered that the main issue is in the alsa sound daemon itself.

The design is flawed when it comes to combining usb and build-in audio cards.

That was not my conclusion but that of Takashi Iwai, one of the alsa developers. So far my only solution was to simply not load any usb-audio modules and use my build-in soundcard (or vice versa). Pehaps it's already fixed now, but when I tried to use them both again (that was about 3 weeks ago) the kernel would innitialy load them both but as soon as I switch output from one to another and back, audio programs started complaining and usb-sound would stop working.

---

### Post by tahitiwibble on 2007-08-25
> **Zubzub said:**
> I remember having sound issues for quite some time now with my kensington laptop dockingstation (usb soundcard) and my build-in laptop soundcard. I´m not new to Linux (I ran ubuntu for 4 months and gentoo for nearly 2 years now) .I remembered that the main issue is in the alsa sound daemon itself.

The design is flawed when it comes to combining usb and build-in audio cards.

That was not my conclusion but that of Takashi Iwai, one of the alsa developers. So far my only solution was to simply not load any usb-audio modules and use my build-in soundcard (or vice versa). Pehaps it's already fixed now, but when I tried to use them both again (that was about 3 weeks ago) the kernel would innitialy load them both but as soon as I switch output from one to another and back, audio programs started complaining and usb-sound would stop working.

Does this explain why sometimes sound comes off my usb headphones and sometimes from my sound card?

---

