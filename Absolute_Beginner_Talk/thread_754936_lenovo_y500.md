---
title: "lenovo y500"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-14
I have installed ubuntu in my lenovo y500.
I has realtek speakers and an integrated mic but I I can't control the speakers volume nor can I use the mic.

---

### Post by sameer.india on 2008-04-14
no replies???????????????????///

---

### Post by xeth_delta on 2008-04-14
Can you hear any sound from the computer?

Let's check wht hardware you have on that machine:
```
sudo lshw -C sound
```
and
```
cat /proc/asound/card0/codec#0 | grep -i codec
```

---

### Post by sameer.india on 2008-04-14
I can hear sound

---

### Post by sameer.india on 2008-04-14
sameer@sameer-laptop:~$ sudo lshw -C sound
[sudo] password for sameer:
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by sameer.india on 2008-04-14
sameer@sameer-laptop:~$ cat /proc/asound/card0/codec#0 | grep -i codec
Codec: Realtek ALC262

---

### Post by xeth_delta on 2008-04-14
So, you simply cannot modify the volume from the mixer controls?
Can you change the sliders values in the mixer window?

---

### Post by xeth_delta on 2008-04-14
By the way, try opening a terminal and then run
```
alsamixer
```

Can you change volumes in there?

---

### Post by sameer.india on 2008-04-14
I can move the sliders up and down
but it has no effect on the volume

---

### Post by sameer.india on 2008-04-14
yeah alsa mixer works

---

### Post by sameer.india on 2008-04-14
what about the mic????????????

---

### Post by sameer.india on 2008-04-14
oh well sorry the mic has started working

---

### Post by sameer.india on 2008-04-14
Thanks

---

### Post by xeth_delta on 2008-04-14
Ok, can you change volume with the big regular mixer window? Is the problem only with the main channel volume?
You might need to change the main control to be set on PCM instead of Master. Have a look at [http://ubuntuforums.org/showthread.php?t=377821&highlight=master+channel+volume](http://ubuntuforums.org/showthread.php?t=377821&highlight=master+channel+volume) and let us know if the suggestions in there worked for you.

---

### Post by sameer.india on 2008-04-14
If i select PCM I can control the volume of my external speakers' sound volume but it has no effect on the inbuilt speakers(controlled by front) and when the front channel is at full volume along with front mic I hear all that is picked by the mic in my speakers.
Also connecting an external device doesn't mute the front speakers

---

### Post by xeth_delta on 2008-04-14
> **sameer.india said:**
> If i select PCM I can control the volume of my external speakers' sound volume but it has no effect on the inbuilt speakers(controlled by front) and when the front channel is at full volume along with front mic I hear all that is picked by the mic in my speakers.
Also connecting an external device doesn't mute the front speakers

Hmm, I am not sure what to suggest now, as it would not be exact anymore since I am a KDE user and the volume controls are slightly different.

For what it's worth, for the master channel selection in KDE one would right click on the volume icon, then choose "Select Master Channel". To mute speakers automatically when headphones are connected one would open the kmix mixer then choose the "switches" tab and check "jack sense".

Hopefully a Gnome user will chime in and offer more help. Try also checking the options in alsamixer and in the meantime perform a couple of advanced searches in the forum and order the results by relevancy. If I find something else, I'll post it here.

---

### Post by sameer.india on 2008-04-14
I'm on kubuntu

---

### Post by sameer.india on 2008-04-14
there's no jack sense check box

---

### Post by xeth_delta on 2008-04-14
I see. Check if perhaps the "line-in as output" and "mic as output" options are enabled.
I guess this can be different from sound card to sound card.

Please also post the contents of  the file "/etc/modprobe.d/alsa-base"

---

### Post by drdrewdown on 2008-04-14
there is a thread on this forum dedicated to the lenovo y510 which may apply to your needs.


search & good luck

---

### Post by xeth_delta on 2008-04-14
> **drdrewdown said:**
> there is a thread on this forum dedicated to the lenovo y510 which may apply to your needs.


search & good luck

Good suggestion, search for that thread. Feel free to ask if you need further help.

---

### Post by sameer.india on 2008-04-14
sameer@sameer-laptop:~$ cat /etc/modprobe.d/alsa-base
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

---

### Post by sameer.india on 2008-04-14
where do i check the "line-in as output" and "mic as output" options

---

### Post by xeth_delta on 2008-04-14
Ok, search for the thread drdrewdown mentioned. If that does not work we can try to add some options to the alsa-base file.

---

### Post by sameer.india on 2008-04-14
no it didn't work
mine is lenovo y500
not y510

---

### Post by sameer.india on 2008-04-14
i followed the instructions on this page.
[http://ubuntuforums.org/showthread.php?t=687663&highlight=y510&page=2](http://ubuntuforums.org/showthread.php?t=687663&highlight=y510&page=2)
 
but my soundcard is ALC262 not ALC888
and alc 262 shows no lenovo models

---

### Post by xeth_delta on 2008-04-14
> **sameer.india said:**
> i followed the instructions on this page.
[http://ubuntuforums.org/showthread.php?t=687663&highlight=y510&page=2](http://ubuntuforums.org/showthread.php?t=687663&highlight=y510&page=2)
 
but my soundcard is ALC262 not ALC888
and alc 262 shows no lenovo models

Try using "auto" as the model:
```
options snd-hda-intel model=auto
```
If that does not work, you could try other models listed in the mentioned file.
It is kind of late now here, so I will be logging out. I'll check tomorrow on how it goes.

Good luck!

---

### Post by sameer.india on 2008-04-15
Here's the latest 
now the extension mutes the internal speakers but how do I stop the mic from interfering
the noise picked up by the integrated mic comes out from the speaker
I have to adjust its  volume to zero so that it doesn't do so

---

### Post by sameer.india on 2008-04-15
Thanks now the whole audio device work as they should

---

### Post by xeth_delta on 2008-04-15
> **sameer.india said:**
> Thanks now the whole audio device work as they should

Really great to hear that. What exactly solved the issue? Adding the auto option? Please remember to mark the thread as solved.

---

### Post by aashay on 2008-04-18
Does the subwoofer work as well? I had to shift to oss as I never managed to get the sub to work with alsa

---

### Post by xeth_delta on 2008-04-18
> **aashay said:**
> Does the subwoofer work as well? I had to shift to oss as I never managed to get the sub to work with alsa

Should I understand you are connecting at least a 2.1 system o your laptop? I believe the OP was using just the built-in speakers.

What is happenning with your subwoofer?

---

### Post by aashay on 2008-04-18
The laptop has an inbuilt 2.1 setup with a small sub sticking out the bottom. This doesn't seem to work with alsa. I got it to work with oss though

---

### Post by xeth_delta on 2008-04-18
> **aashay said:**
> The laptop has an inbuilt 2.1 setup with a small sub sticking out the bottom. This doesn't seem to work with alsa. I got it to work with oss though

Ah, Ok. I had no idea. Maybe the OP will ask about that, too, in a few days.

---

