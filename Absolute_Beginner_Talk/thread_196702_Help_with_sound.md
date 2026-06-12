---
title: "Help with sound"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by Ca$h on 2006-06-14
I was able to get my sound to work with ubuntu 5.10. I recently installed ubuntu 6.06 and everything works fine besides my sound. Is there annyway to get my sound to work?

---

### Post by zxee on 2006-06-14
First you can enable sound from the System>Preferences>sound menu selection, and if you still don't have sound open a shell/terminal and type sudo alsaconf <enter> Hope that helps.

---

### Post by rich257 on 2006-06-14
I had the same problem and have solved it for Gnome.

It seems that there is a problem setting the default sound device, see [this]("https://launchpad.net/distros/ubuntu/+source/control-center/+bug/44101") bug,  so that if you have more than one sound device Gnome will always use device 0, which may be the mic on your webcam, or whatever, and you don't get a lot of sound out of a microphone.

A way round this is to fix the index for your sound cards, as per [this]("http://www.ubuntuforums.org/showthread.php?t=142420") thread.

Note that you can get the name of your sound card modules using
```
lsmod | grep snd
```

---

### Post by Ca$h on 2006-06-15
Alright let me switch to ubuntu really quick, right now i am on windows because I can't get the sound to work. 

Thanks and I will let you know how it works out.:D

Edit:
zxee, when I typed in that command I got this:
```
sudo: alsaconf: command not found
```

Alright I used the command to find the name of my sound card and i got this:
```
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

```

Edit: I got it to work, thanks :D

---

