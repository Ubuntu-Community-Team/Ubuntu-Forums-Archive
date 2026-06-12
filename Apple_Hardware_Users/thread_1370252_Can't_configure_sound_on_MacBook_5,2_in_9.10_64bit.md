---
title: "Can't configure sound on MacBook 5,2 in 9.10 64bit"
date: 2010-01-02
forum: Apple Hardware Users
---

### Post by ebash on 2010-01-02
I've just installed Ubuntu 9.10 64bits on a white MacBook 5,2 and I can't configure the sound on the laptop.

I manged to have it working fine in Ubuntu 9.04 but the sound settings in gnome have changed too much and I can no longer reconfigure the sound system to work as before.

For now I can only hear music through the internal speaker(s) while previously with 9.04 I was able to use the built-in audio jack and use my external speakers. What was even better was that I was able to toggle the between the built-in speakers and the external speakers by plugin/unplugin the speakers jack. Today all of this nice features are gone...

What's the proper way for configuring sound with pulseaudio? Should I disable pulseaudio?

---

### Post by linuxopjemac on 2010-01-04
Sound

To get it working install the ALSA backport with: aptitude install linux-backports-modules-alsa-karmic-generic edit the alsa-base.conf file with gksudo gedit /etc/modprobe.d/alsa-base.conf and in the line options snd-hda-intel add model=mb31 and restart the computer.

Edit by Canavas 2010/01/01:

This worked for me tested on two 5.2 MacBooks.

Add options snd_hda_intel model=mb5 in the /etc/modprobe.d/options.conf

Restart the computer and check the audio-properties if any slider is muted 

see [https://help.ubuntu.com/community/MacBook5-2/Karmic#Sound](https://help.ubuntu.com/community/MacBook5-2/Karmic#Sound)
and [http://mac.linux.be/content/sound-mbp-52-karmic-koala](http://mac.linux.be/content/sound-mbp-52-karmic-koala)

---

### Post by ebash on 2010-01-04
> **linuxopjemac said:**
> Sound

To get it working install the ALSA backport with: aptitude install linux-backports-modules-alsa-karmic-generic edit the alsa-base.conf file with gksudo gedit /etc/modprobe.d/alsa-base.conf and in the line options snd-hda-intel add model=mb31 and restart the computer.


I've already followed the instructions from the wiki and they only got me as far as to have sound from the builtin speakers, but the output headphone socket doesn't work.

I still need a way to fix two things:
1) enable the output headphone socket
2) configure the main sound mixer for the multimedia keys (use PCM instead of master).

With the previous versions of Ubuntu 9.04 and earlier I could configure these two things through the sound properties configuration dialog. Now with Ubuntu 9.10 these options are no longer available.

---

### Post by linuxopjemac on 2010-01-04
did you try unmuting the headphone jacket with alsa-mixer ?

---

### Post by ebash on 2010-01-04
> **linuxopjemac said:**
> did you try unmuting the headphone jacket with alsa-mixer ?
I can't because alsamixer doesn't show me the same mixers as it did under Ubuntu 9.04.

The only options that I have are:
```

        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;         &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;         &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;                                 &#9484;&#9472;&#9472;&#9488;                    &#9484;&#9472;&#9472;&#9488;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;  &#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;  &#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;                    &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;        &#9474;&#9618;&#9618;&#9474;         &#9474;  &#9474;        &#9474;  &#9474;                                 &#9474;  &#9474;        6ch         &#9474;&#9618;&#9618;&#9474;        &#9474;
&#9474;       &#9500;&#9472;&#9472;&#9508;        &#9492;&#9472;&#9472;&#9496;        &#9500;&#9472;&#9472;&#9508;         &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;        &#9500;&#9472;&#9472;&#9508;        &#9492;&#9472;&#9472;&#9496;         &#9500;&#9472;&#9472;&#9508;        &#9492;&#9472;&#9472;&#9496;        &#9484;&#9472;&#9472;&#9488;        &#9484;&#9472;&#9472;&#9488;         &#9500;&#9472;&#9472;&#9508;                    &#9500;&#9472;&#9472;&#9508;        &#9474;
&#9474;       &#9474;OO&#9474;                    &#9474;OO&#9474;         &#9474;OO&#9474;        &#9474;OO&#9474;        &#9474;OO&#9474;                     &#9474;MM&#9474;                    &#9474;OO&#9474;        &#9474;OO&#9474;         &#9474;MM&#9474;                    &#9474;OO&#9474;        &#9474;
&#9474;       &#9492;&#9472;&#9472;&#9496;                    &#9492;&#9472;&#9472;&#9496;         &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;                     &#9492;&#9472;&#9472;&#9496;                    &#9492;&#9472;&#9472;&#9496;        &#9492;&#9472;&#9472;&#9496;         &#9492;&#9472;&#9472;&#9496;                    &#9492;&#9472;&#9472;&#9496;        &#9474;
&#9474;        100      100<>100    100<>100     100<>100    100<>100    100<>100     67<>67        0<>0        0<>0                                 0<>0                   59<>59       &#9474;
&#9474;      Master       PCM        Front       Surround      LFE      <  Line  >   Line Boo       Mic       Mic Boos     IEC958     IEC958 D       Beep      Channel        HP         &#9474;
&#9474;                                                                                                                                                                                  &#9474;

```

Mixers available:

Master, PCM, Front, Surround, LFE, <  Line  >, Line Boo, Mic, Mic, Boos, IEC958, IEC958 D, Beep, Channel and HP.

---

### Post by linuxopjemac on 2010-01-05
sorry, I can't help you further, anyone else here ?

---

### Post by lepukowsky on 2010-01-05
hey ebash, I have a 5.2 white macbook 64 bit as well. My sound is running perfectly, and although I forget exactly which steps I followed from the forums, you can try copying my alsa-base.conf file which is what got it to start working for me. 

Go to /etc/modprobe.d/alsa-base.conf and make a backup copy. Then open the original and replace the code with the following, which should make it work.

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
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N model=mbp3

```

I hope this works for you! I am kinda a noob with this so sorry if I am saying something obvious that you already tried. A good thread for 5.2 macbooks is [http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758).

good luck!
- LP

---

### Post by ebash on 2010-01-06
Thannks lepukowsky your configuration works. It was identical to mine with the exception that you have model=mbp3 while I had model=mbp31.

What I had to do was to plug my speakers in the socket that looks like |>o<| instead of the one with the headset label.

Being able to turnoff the internal speaker when an outside one is plugged would be nice, but I'm now a happy camper with this setting.

---

### Post by alexmurray on 2010-01-14
I've just posted a patch to enable auto-muting of speakers when headphones are plugged in on MacBook 5,2: [http://ubuntuforums.org/showthread.php?t=1379971](http://ubuntuforums.org/showthread.php?t=1379971)

---

