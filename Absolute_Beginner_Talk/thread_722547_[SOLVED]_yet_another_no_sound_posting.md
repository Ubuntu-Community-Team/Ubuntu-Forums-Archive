---
title: "[SOLVED] yet another no sound posting"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by bubonic1347 on 2008-03-12
I have a gigabyte motherboard which has the standard Intel HDA onboard sound. I installed Mythbuntu 7.10 awhile ago and everything worked great. I was running on the analog line out to speakers. Last week there was another security update and I had the update manger do its work. Then no sound!

So I re-installed from the Mythbuntu CD, starting all over again and the sound came back. When I clicked ok for updates no sound again.

It's interesting that when I type alsamixer into the terminal the little box that is the mixer appears but there aren't any columns to adjust sound. The headers at the top are there, but no sound columns.

The operating system sees the onboard sound. I'm running standard normal generic equipment. This stuff isn't my fault.

Maybe Hardy will solve things, however I'm now hesitant to update at all.

Thanks for anyone who might be interested in trying to help me track this down. I am a complete beginner.

---

### Post by mali2297 on 2008-03-12
Post the output of
```

lspci | grep [Aa]udio
aplay -l

```

---

### Post by bubonic1347 on 2008-03-12
artson@artson-desktop:~$ lspci | grep [Aa]udio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
05:00.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:00.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
05:00.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
05:00.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
05:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
05:01.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
05:01.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
artson@artson-desktop:~$ aplay -l

---

### Post by bubonic1347 on 2008-03-12
**** List of PLAYBACK Hardware Devices ****
card 2: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
artson@artson-desktop:~$

---

### Post by mali2297 on 2008-03-12
Have you tried any of the advices in this [thread]("http://ubuntuforums.org/showthread.php?t=314383")?

---

### Post by bubonic1347 on 2008-03-12
options snd-hda-intel model= lg

So I paste something like this into terminal but just substitute lg with gigabyte?

OK I'll try that and here's what happens:

artson@artson-desktop:~$ options snd-hda-intel model= gigabyte
bash: options: command not found
artson@artson-desktop:~$ 

Or if I enter say... sudo vim /etc/alsa I get:

~
~
~
~
~
~
~
~
~
--INSERT--

I have no clue what's going on.

---

### Post by bubonic1347 on 2008-03-12
So if I enter gksudo gedit /etc/modprobe.d/alsa-base
I get,  in a notepad like format:

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

I still have no clue.

---

### Post by tangibleorange on 2008-03-12
yeah just add the "options" line to the end of that file. Alternatively, it can all be done with line of code into the terminal:

```
echo 'options snd-hda-intel model=hp" | sudo tee -a /etc/modprobe.d/alsa-base
```

replacing 'hp' with your model of laptop. keep in mind that not all models will work. if the doesn't work, you can try the model as 'auto'.

---

### Post by bubonic1347 on 2008-03-12
So I paste in echo 'options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base using auto as you suggested and I get:

artson@artson-desktop:~$ echo 'options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base
> 


Is that it? There is still no sound.

I don't have a laptop I have a normal gigabyte motherboard which has probably been sold in the tens of thousands.

---

### Post by bubonic1347 on 2008-03-12
So from the other thread julian 67 posts:

 Originally Posted by julian67  View Post
A kernel upgrade or alsa upgrade probably are why you need to mess about with this sometimes. Once you have it working as desired you can go into synaptic and lock the kernel version and alsa version so they don't get updated, but you need to check security advisories and be sure that you're happy keeping your kernel version when security updates are made available.

So it seems I re-install myhbuntu and then lock the kernel down in Synaptic. I have no clue how to lock down.

---

### Post by bubonic1347 on 2008-03-12
ooops sorry tangibleorange I'm supposed to add the options thing to teh end of that long file. Sorry. So I'll try that in terminal and I get:

artson@artson-desktop:~$ # autoloader aliases
artson@artson-desktop:~$ install sound-slot-0 /sbin/modprobe snd-card-0
install: target `snd-card-0' is not a directory
artson@artson-desktop:~$ install sound-slot-1 /sbin/modprobe snd-card-1
install: target `snd-card-1' is not a directory
artson@artson-desktop:~$ install sound-slot-2 /sbin/modprobe snd-card-2
install: target `snd-card-2' is not a directory

still no luck. 
artson@artson-desktop:~$ install sound-slot-3 /sbin/modprobe snd-card-3
install: target `snd-card-3' is not a directory
artson@artson-desktop:~$ install sound-slot-4 /sbin/modprobe snd-card-4
install: target `snd-card-4' is not a directory
artson@artson-desktop:~$ install sound-slot-5 /sbin/modprobe snd-card-5
install: target `snd-card-5' is not a directory
artson@artson-desktop:~$ install sound-slot-6 /sbin/modprobe snd-card-6
install: target `snd-card-6' is not a directory
artson@artson-desktop:~$ install sound-slot-7 /sbin/modprobe snd-card-7
install: target `snd-card-7' is not a directory
artson@artson-desktop:~$ 
artson@artson-desktop:~$ # Cause optional modules to be loaded above generic modules
artson@artson-desktop:~$ install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ # Cause optional modules to be loaded above sound card driver modules
artson@artson-desktop:~$ install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ 
artson@artson-desktop:~$ # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
artson@artson-desktop:~$ install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ 
artson@artson-desktop:~$ # Load snd-seq for devices that don't have hardware midi;
artson@artson-desktop:~$ #   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
artson@artson-desktop:~$ #   non-Creative Labs PCI hardware
artson@artson-desktop:~$ install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ # Prevent abnormal drivers from grabbing index 0
artson@artson-desktop:~$ options snd-bt87x index=-2
bash: options: command not found
artson@artson-desktop:~$ options cx88-alsa index=-2
bash: options: command not found
artson@artson-desktop:~$ options saa7134-alsa index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-atiixp-modem index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-intel8x0m index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-via82xx-modem index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-usb-audio index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-usb-usx2y index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-usb-caiaq index=-2
bash: options: command not found
artson@artson-desktop:~$ # Ubuntu #62691, enable MPU for snd-cmipci
artson@artson-desktop:~$ options snd-cmipci mpu_port=0x330 fm_port=0x388
bash: options: command not found
artson@artson-desktop:~$ echo 'options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base

---

### Post by mali2297 on 2008-03-12
No, no, no,.. 

Just add the line 
```

options snd-hda-intel model=auto

```
to the file via gedit,
```
 
gksudo gedit /etc/modprobe.d/alsa-base

```
(It might already be there.)

---

### Post by mali2297 on 2008-03-12
> **bubonic1347 said:**
> So from the other thread julian 67 posts:

 Originally Posted by julian67  View Post
A kernel upgrade or alsa upgrade probably are why you need to mess about with this sometimes. Once you have it working as desired you can go into synaptic and lock the kernel version and alsa version so they don't get updated, but you need to check security advisories and be sure that you're happy keeping your kernel version when security updates are made available.

So it seems I re-install myhbuntu and then lock the kernel down in Synaptic. I have no clue how to lock down.

Just don't upgrade any package that contains the words linux-image, -headers, sound or alsa.

---

### Post by bubonic1347 on 2008-03-12
So I do this in a terminal:
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
options snd-hda-intel model=auto

And I get this as a result? I am the definition of a beginner, noob, clueless
unworthy type.






artson@artson-desktop:~$ # autoloader aliases
artson@artson-desktop:~$ install sound-slot-0 /sbin/modprobe snd-card-0
install: target `snd-card-0' is not a directory
artson@artson-desktop:~$ install sound-slot-1 /sbin/modprobe snd-card-1
install: target `snd-card-1' is not a directory
artson@artson-desktop:~$ install sound-slot-2 /sbin/modprobe snd-card-2
install: target `snd-card-2' is not a directory
artson@artson-desktop:~$ install sound-slot-3 /sbin/modprobe snd-card-3
install: target `snd-card-3' is not a directory
artson@artson-desktop:~$ install sound-slot-4 /sbin/modprobe snd-card-4
install: target `snd-card-4' is not a directory
artson@artson-desktop:~$ install sound-slot-5 /sbin/modprobe snd-card-5
install: target `snd-card-5' is not a directory
artson@artson-desktop:~$ install sound-slot-6 /sbin/modprobe snd-card-6
install: target `snd-card-6' is not a directory
artson@artson-desktop:~$ install sound-slot-7 /sbin/modprobe snd-card-7
install: target `snd-card-7' is not a directory
artson@artson-desktop:~$ 
artson@artson-desktop:~$ # Cause optional modules to be loaded above generic modules
artson@artson-desktop:~$ install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ # Cause optional modules to be loaded above sound card driver modules
artson@artson-desktop:~$ install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ 
artson@artson-desktop:~$ # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
artson@artson-desktop:~$ install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ 
artson@artson-desktop:~$ # Load snd-seq for devices that don't have hardware midi;
artson@artson-desktop:~$ #   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
artson@artson-desktop:~$ #   non-Creative Labs PCI hardware
artson@artson-desktop:~$ install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install: unrecognized option `--ignore-install'
Try `install --help' for more information.
artson@artson-desktop:~$ # Prevent abnormal drivers from grabbing index 0
artson@artson-desktop:~$ options snd-bt87x index=-2
bash: options: command not found
artson@artson-desktop:~$ options cx88-alsa index=-2
bash: options: command not found
artson@artson-desktop:~$ options saa7134-alsa index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-atiixp-modem index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-intel8x0m index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-via82xx-modem index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-usb-audio index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-usb-usx2y index=-2
bash: options: command not found
artson@artson-desktop:~$ options snd-usb-caiaq index=-2
bash: options: command not found
artson@artson-desktop:~$ # Ubuntu #62691, enable MPU for snd-cmipci
artson@artson-desktop:~$ options snd-cmipci mpu_port=0x330 fm_port=0x388
bash: options: command not found
artson@artson-desktop:~$ options snd-hda-intel model=auto
bash: options: command not found
artson@artson-desktop:~$ 

I think I might try the lock down kernel thing in Synaptic. How do I lock down?

---

### Post by bubonic1347 on 2008-03-12
> **mali2297 said:**
> Just don't upgrade any package that contains the words linux-image, -headers, sound or alsa.

Ok I'll try that. :)

---

### Post by bubonic1347 on 2008-03-12
OK as I stated I'm a clueless noob, however here are the steps as I perceive them:

1. Open a terminal
2. Copy gksudo gedit /etc/modprobe.d/alsa-base and paste it into terminal
3. This opens a gedit file.
4. Copy options snd-hda-intel model=auto and paste it at the bottom of the file on a new separate line
5. Copy that entire gedit file and return to the original terminal and paste the whole thing in.

I think I did this right? It didn't work, still no sound.

I'm starting to feel foolish and like I shouldn't even be doing this open source thing.

---

### Post by mali2297 on 2008-03-12
> **bubonic1347 said:**
> OK as I stated I'm a clueless noob, however here are the steps as I perceive them:

1. Open a terminal
2. Copy gksudo gedit /etc/modprobe.d/alsa-base and paste it into terminal
3. This opens a gedit file.
4. Copy options snd-hda-intel model=auto and paste it at the bottom of the file on a new separate line
5. Copy that entire gedit file and return to the original terminal and paste the whole thing in.

I think I did this right? It didn't work, still no sound.

I'm starting to feel foolish and like I shouldn't even be doing this open source thing.

Strike 5. After you've added the line, save the file and reboot.

There's no guarantee that it will work.

---

### Post by bubonic1347 on 2008-03-12
Wow Thank you so much mali I'll report back! :)

---

### Post by bubonic1347 on 2008-03-12
It worked!! Thank you soooo much mali! :) :) :)

Now I have to figure out how to mark this thread as solved and thank you officially as well.

I'm feeling a little less foolish! :) :) :) :) :)

---

