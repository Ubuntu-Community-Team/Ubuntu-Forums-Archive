---
title: "VIA VT82XX Headphone Jack Issue"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Demonskitz on 2008-04-02
Hello, I've only had linux a week but am enjoying it sooo much more than evil microsoft apart from one thing: I cannot get my headphone jack to work at all either with headphones in or a line out to external speakers. The built-in speakers work fine, it is just the headphone jack that is having a spaz. 
I have read so many posts on here with similar issues but most of them refer to intel stuff and I am not sure if that applies to me, and if it does the things I have tried so far have not worked.
I am using onboard sound that came with my laptop, a hi-grade notrino something-or-other:  Intel T2130 Dual Core with VIA onboard sound and graphics:

**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
demonskitz@selene:~$ cat /proc/asound/card0/codec#* | grep codec -i
Codec: VIA VIA VT1708
Codec: Motorola Si3054


There's no tab in volume control for headphones, there's no box that I can check or uncheck anywhere relating to headphones. When I run alsamixer there is no option relating to headphones or line outs, although just in case I turned up all the volume controls I could find to full but no joy. 

I have tried linux-backports-modules-generic, that didnt affect it either. 
I have tried sudo gedit /etc/modprobe.d/alsa-base and I have tried adding options snd-hda-intel model=3stack, also model=laptop and also model=auto but that made no difference. I didn't try anything else off that really handy list somone posted because none of them really related to my soundcard. 

Anybody any ideas?

---

### Post by Demonskitz on 2008-04-02
Oh yeah, I forgot to say, I am running Ubuntu 7.10 Gutsy and the headphone jack worked ok for the few hours that my laptop had evil Vista installed on it.

---

### Post by gnuslov on 2008-05-31
Hope you managed to fix your problem since your last post, but in case not, I found [this]("http://ubuntuforums.org/showthread.php?t=556217") thread to be of great help, and it sounds like your hardware is similar.

---

