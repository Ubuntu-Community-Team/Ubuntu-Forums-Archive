---
title: "No sound after installing kubuntu"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by browny254 on 2008-03-18
Hi guys, I just switched over to kubuntu from ubuntu and everythings going fine except im not getting any sound. I have done a lot of searching and seen lots of other ppl have had the same problem, but when I try and follow their solutions it doesnt seem to work. Im still pretty new to Linux though so it could just be me doing something wrong.

heres some stuff I have done that may be able to help fixing the problem...

```

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

i also went to alsamixer and have Master and PCM, which I set both to full, and had caller-id and off-hook muted so i changed that...that was all that was there.


thanks for any help someone can give.

---

### Post by (((X))) on 2008-03-18
I have High defunition audio too, no problems with sound, however my earphones are playing sound together with speakers, so after weeks of searching on forums I decided only way I can get it to work is by recompiling my kernel ( [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)) and installing 
alsa-driver
alsa-firmware
alsa-lib
alsa-plugins
alsa-tools
after that.
I got them from [http://www.alsa-project.org](http://www.alsa-project.org)
First I removed all alsa packages through synaptic, then
just unzipped all downloaded alsa packages
and in terminal
sudo -s
cd /unzipped folder/alsa..
./configure
make
make install
If you are interested in that, I d like to answer your questions

---

### Post by mali2297 on 2008-03-18
You might need to recompile the alsa drivers, see if you can follow these instructions:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If you get into trouble, post back.:popcorn:

---

### Post by browny254 on 2008-03-18
thanks for the replies...i ended up finding this [http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463) which is more specific for my laptop but has followed pretty much what you said except you had to add 
options snd-hda-intel model= toshiba
to
sudo nano /etc/modprobe.d/alsa-base

and that has got my 99% of the way there. only problem now is that my volume control in the system tray only controls the headphone volume, even if they arent connected...to change my master volume im having to use KMix (im using Kubuntu) and change the PCM volume. If i can figure out how to change the master volume with the main volume control (the system tray and a physical scroll wheel thinggy) ill be back to normal.


Something intersting I have noticed though is that I used to have Ubuntu and I had no problems with the sound with that but my webcam wouldnt work. In Kubuntu I have had the revere...my webcam works perfectly without any setting up and the speakers required all the work...

---

### Post by mali2297 on 2008-03-19
> **browny254 said:**
>  only problem now is that my volume control in the system tray only controls the headphone volume, even if they arent connected...to change my master volume im having to use KMix (im using Kubuntu) and change the PCM volume. If i can figure out how to change the master volume with the main volume control (the system tray and a physical scroll wheel thinggy) ill be back to normal.


As I don't use Kubuntu, I can't help you. But see if there isn't a setting somewhere (right-click on the volume control?).

---

