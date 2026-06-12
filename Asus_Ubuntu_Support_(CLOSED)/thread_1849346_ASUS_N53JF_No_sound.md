---
title: "ASUS N53JF No sound"
date: 2011-09-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by helixx77 on 2011-09-24
I installed ubuntu and I currently have no sound.  I am an absolute noob at this OS and I don't know what to do.  Can someone please guide me step by step so I can get sound working?

Thanks.

---

### Post by Toz on 2011-09-30
Hello and welcome to the forums.

Open a terminal window and run this command:
```
sudo bash -c "echo 'options snd-hda-intel model=auto position_fix=0' >> /etc/modprobe.d/alsa-base.conf"
```
...and reboot.
This will set an alsa configuration variable that should allow your sound to work.

If it doesn't work, the from the terminal window again, run:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
choose the upload option and post back the link it generates.

---

### Post by helixx77 on 2011-10-02
[http://www.alsa-project.org/db/?f=7c6ffbac071b10bc1f79bae684c8e70d130fe7c3](http://www.alsa-project.org/db/?f=7c6ffbac071b10bc1f79bae684c8e70d130fe7c3)

---

### Post by Toz on 2011-10-02
Edit the **/etc/modprobe.d/alsa-base.conf** file and change the line that reads:
```
options snd-hda-intel module=auto
```
...to read:
```
options snd-hda-intel model=auto position_fix=0
```
Save and reboot. 

If still no sound, please post back updated alsa-script.

---

### Post by helixx77 on 2011-10-03
[http://www.alsa-project.org/db/?f=b382492f8e5d2dc05b0a2c44f847108a9362f2b5](http://www.alsa-project.org/db/?f=b382492f8e5d2dc05b0a2c44f847108a9362f2b5)

---

### Post by Toz on 2011-10-04
The module entry is still showing up. Can you post back the contents of your **/etc/modprobe.d/alsa-base.conf** file?

---

### Post by helixx77 on 2011-10-05
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
options snd-hda-intel model=auto position_fix=0

---

### Post by Toz on 2011-10-05
Its not there. What are the contents of **/etc/modprobe.d/alsa-base.conf**?

You have an errant *snd-hda-intel: module=auto* entry that we need to find and delete.

---

### Post by helixx77 on 2011-10-05
There was a *snd-hda-intel: module=auto *entry in the alsa-base.conf.save.  I deleted it and replaced it with options snd-hda-intel model=auto position_fix=0.

---

### Post by helixx77 on 2011-10-05
new alsa-script: [http://www.alsa-project.org/db/?f=91a610fb0b9ef47121c688730c4050ec1d5ca4ba](http://www.alsa-project.org/db/?f=91a610fb0b9ef47121c688730c4050ec1d5ca4ba)

---

### Post by Toz on 2011-10-05
> **helixx77 said:**
> There was a *snd-hda-intel: module=auto *entry in the alsa-base.conf.save.  I deleted it and replaced it with options snd-hda-intel model=auto position_fix=0.

Can you please just delete that entry - do not replace it with the other one.

---

### Post by Toz on 2011-10-05
That looks better. Is there sound?

If not, check that its not muted.

---

### Post by helixx77 on 2011-10-06
Sound is working now.  thanks :)

---

### Post by Toz on 2011-10-06
Glad to hear. Please mark this thread as SOLVED from the Thread Tools link above.

---

