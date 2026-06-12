---
title: "lost sound on toshiba satelitte a 100"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by rubberduckie2003 on 2008-01-05
i have ubuntu 7.10 on toshiba satelitte a 100 and absolutely no sound whatsoever . 
i know that this problem appears often and has been discussed , but i am to beginner to understand what others say and i want some personal advice , step by step , if possible
what should i do ? where do i begin from ? thanks for being here for me :):KS

---

### Post by Daveth on 2008-01-05
have you visited this page?

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

exactly which Toshiba do you have- this lists the ones tested and the sound seems OK on the A100 series.

[https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba](https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba)

what does

```
aplay -l
```

typed into a terminal say? Terminal found at Applications/ Accessories

---

### Post by rubberduckie2003 on 2008-01-05
aplay -l sais :
*** List of PLAYBACK Hardware devices ***
card 0 : Intel [ HDA Intel ] , device 0 : ALC861VD Analog [ ALC861VD Analog ]
   Subdevices : 1/1
   Subdevice #0: subdevice #0
card 0 : Intel [ HDA Intel ] , device 6 : Si3054 Modem [ Si3054 Modem ]
    Subdevices : 1/1
    Subdevice #0: subdevice #0


what next?

---

### Post by Daveth on 2008-01-05
this might be a way forward

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/180471](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/180471)

esp the bits
"Toshiba Satellite P200-155"
 and 
"After installing ALSA 1.0.15 from the backport I set /etc/modprobe.d/alsa-base to pass the option 'model=toshiba' to snd-hda-intel as the mixer seems to match the hardware better with this configuration. I also now have full volume and the speakers turn off when using headphones, which did not work in Feisty and is a big improvement!"

I seems that you have to alter the model name in this config file to either Toshiba or (bizzarely) Lenovo.

So, double click on the /etc/modprobe.d/alsa-base file and read what it says and/or paste it's contents into a post back. We are looking for a line that goes on about snd-hda-intel  and its value (the = bit).
A little painful, I know.

---

### Post by rubberduckie2003 on 2008-01-05
so i looked in /etc/modprobe.d/alsa-base and i found this line
options snd-intel8x0m index=-2

is this what you where looking for ?

i put all output of cat /etc/modprobe.d/alsa-base ...

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


what else do u need?

---

### Post by kellogs908 on 2008-01-05
i have basically the same computer , that is i have the toshiba satellite a205 and I cant get sound either
here is a link to the answers i got [http://ubuntuforums.org/showthread.php?t=658634&page=2](http://ubuntuforums.org/showthread.php?t=658634&page=2)
unfortunatly it was of no luck yet, try to go through the link i gave you and see if you get the same responses that I did

and thats the first i have seen of that list but the a205 isnt on there

---

### Post by rubberduckie2003 on 2008-01-05
thanks guys
any other ideas please ?

---

### Post by balaknair on 2008-01-05
Hi
have you tried the hda-intel how to at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

if not I'll just outline a few key steps from it which I think should solve your problem

In a terminal type
```
cat /proc/asound/card0/codec#* | grep Codec
```

This will tell you what codec your card uses

Next open (usr/src/(your kernel version)/sound/alsa/alsa-configuration.txt) or check this link [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)
and find your version on it
eg: my card returned "Codec: Analog Devices AD1986A"
in the configuration file
```
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)
```

choose the description which best matches your system sound setup

Then in a terminal type
```
sudo nano /etc/modprobe.d/alsa-base
```

and paste this into the last line of the file
```
options snd-hda-intel model=MODEL
```

replace MODEL with your model from the alsa-conguration page(eg a 5.1 sound system would be a 6stack)

Reboot

Hope this solves your problem

---

### Post by rubberduckie2003 on 2008-01-06
i found no alsa in the /usrc/src/linux-headers-(kernel version)
i only have aoa, core,i2c,mips,parisc,pcmcia,soc,synth,arm,drivers,isa,oss,pci,ppc,sparc,usb and a Makefile ...

---

### Post by balaknair on 2008-01-06
Just check the link [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)
it's the same file.

---

### Post by balaknair on 2008-01-06
OK I think this should be what you need(for card ALC861VD)

options snd-hda-intel model=lenovo

just copy and paste this at the END(use the down arrow or page down key to navigate to the end of the file) of the modprobe.d/alsa-base file, save and exit and then reboot

all the best

---

