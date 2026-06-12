---
title: "sound not working with movies"
date: 2005-06-12
forum: Absolute Beginner Talk
---

### Post by peejay82 on 2005-06-12
Hello everyone,

I'm fairly new to linux. My problem is that I get sound when playing mp3s or watching tv, but no sound at all when playing a divx movie... I've searched on these forums, alas to no avail. It happens in every movie playing app I have (xine, vlc, totem). Anyone got an idea what the problem is? 

edit: mp3s only play in xmms if i select the oss plugin, btw

Thanks in advance,

Cheers,

Peejay

---

### Post by phen on 2005-06-12
did you download the w32codecs? see www.ubuntuguide.org!

cheers,

kai

---

### Post by peejay82 on 2005-06-12
yep, I did all that
also installed the alsa plugin for vlc

maybe this can be of some help:
lsmod|grep snd
snd_bt87x              12612  1
snd_ymfpci             56768  1
snd_opl3_lib           10112  1 snd_ymfpci
snd_hwdep               9220  1 snd_opl3_lib
snd_mpu401_uart         7168  1 snd_ymfpci
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd_intel8x0           29984  2
snd_ac97_codec         64608  2 snd_ymfpci,snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  5 snd_pcm_oss
snd_pcm                84872  5 snd_bt87x,snd_ymfpci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  3 snd_ymfpci,snd_opl3_lib,snd_pcm
snd                    50276  13 snd_bt87x,snd_ymfpci,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  5 snd
snd_page_alloc          9604  4 snd_bt87x,snd_ymfpci,snd_intel8x0,snd_pcm
gameport                4608  2 snd_ymfpci,analog
root@ubuntu:/home/peejay #

---

### Post by peejay82 on 2005-06-12
Could it be that alsa is using the wrong soundcard, btw? I need it to use my yamaha based pci card and not my motherboard's intel ac97 chip

Thanks in advance,

Cheers

---

### Post by peejay82 on 2005-06-12
Nevermind, I had the multiple soundcard problem and it's fixed now.

For anyone with similar problems:

[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

---

