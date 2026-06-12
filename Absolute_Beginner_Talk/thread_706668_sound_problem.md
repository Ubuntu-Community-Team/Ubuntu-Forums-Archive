---
title: "sound problem"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by mikael_b on 2008-02-24
Hi,

I have a HP dv6000, Ubuntu Gutsy 7.10, and like many others I can't get any sound out of my speakers. I have been reading trough this forum for hours trying every single tip about how to fix it, but nothing seems to work.

The strange thing is that i can mute and unmute the speakers I can tune up/down but nothing give any effect more then visual.

I have tried to change the settings System->Preferences->Sound and then to run the test, but still no sound...

Please, can anyone help me out?

/Mikael
> mikael@mikael-laptop:~$ lspci | grep -i audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


> mikael@mikael-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> mikael@mikael-laptop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 9


---

### Post by bobbybobington on 2008-02-24
It looks like you're having trouble with the intel soundcard, I have to usually fix when the updates break it. Basically I think you have to reinstall ALSA. [This post ]("http://ubuntuforums.org/showpost.php?p=3801701&postcount=5")should give you a pretty good guide.

---

### Post by mikael_b on 2008-02-24
Are you sure, this seem kind of strang when i type 

sudo aptitude remove alsa-base alsa-utils

> The following actions will resolve these dependencies:

Remove the following packages:
ekiga
fast-user-switch-applet
gdm
libpt-plugins-alsa
ubuntu-desktop

Score is 395

Accept this solution? [Y/n/q/?]


Should i answare: y ?

---

### Post by mikael_b on 2008-02-25
Anyone else that has another suggestion?

---

### Post by superprash2003 on 2008-02-25
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by mikael_b on 2008-02-25
Nope, still not working. I can change the settings but when i press test there is no sound...

---

### Post by lzfy on 2008-02-25
Same here. I even upgraded to Hardy but that didn't work either.

---

### Post by lzfy on 2008-02-27
I fixed the problem by removing alsa and installing OSS4. Works great :)

---

