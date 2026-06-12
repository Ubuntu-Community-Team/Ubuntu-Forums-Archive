---
title: "Movie player for Ubuntu with support for various filetypes"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by moederfietser on 2006-08-30
Hello all,
Lately I tried to play an mpeg file in Totem gstreamer, but it didn't work. It said that it needed a codec. So I looked on some sites for multimedia codecs and installed them, but it still didn't work. Installed Totem xine, and it worked, sort of... The video screen is way too bright and I have no sound. I also tried Realplayer 10, but no luck, still needs plugins. I also tried Mplayer, got video and sound, but video screen too bright and artifacts running in the video screen. I don't know what to do next. Would appreciate it if someone could help me.

Thanks in advance,
moederfietser

---

### Post by Anonii on 2006-08-30
> **moederfietser said:**
> Hello all,
Lately I tried to play an mpeg file in Totem gstreamer, but it didn't work. It said that it needed a codec. So I looked on some sites for multimedia codecs and installed them, but it still didn't work. Installed Totem xine, and it worked, sort of... The video screen is way too bright and I have no sound. I also tried Realplayer 10, but no luck, still needs plugins. I also tried Mplayer, got video and sound, but video screen too bright and artifacts running in the video screen. I don't know what to do next. Would appreciate it if someone could help me.

Thanks in advance,
moederfietser
Try VLC, it always works :P

---

### Post by PPAAUULL on 2006-08-30
try installing the codec using these instructions [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

you can also use Automatix I think.

---

### Post by taurus on 2006-08-30
It doesn't matter which multimedia you are using, you need the codecs so install it first and then try playing your movie again...  Automatix is an easy and nice little util to install codecs and other things that you might need.

---

### Post by justin whitaker on 2006-08-30
> **moederfietser said:**
> Hello all,
Lately I tried to play an mpeg file in Totem gstreamer, but it didn't work. It said that it needed a codec. So I looked on some sites for multimedia codecs and installed them, but it still didn't work. Installed Totem xine, and it worked, sort of... The video screen is way too bright and I have no sound. I also tried Realplayer 10, but no luck, still needs plugins. I also tried Mplayer, got video and sound, but video screen too bright and artifacts running in the video screen. I don't know what to do next. Would appreciate it if someone could help me.

Thanks in advance,
moederfietser

Still sounds like a codec issue. Mplayer plays just about everything...artifacts on playback says to me that there is a codec missmatch.

---

### Post by PPAAUULL on 2006-08-30
Ya I would say to go and get the codecs then try it then worry about the player.

---

### Post by bruce89 on 2006-08-30
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
Will allow totem, rythmbox play pretty much anything.

---

### Post by moederfietser on 2006-08-31
I installed the codes manually, didn't work. I used Automatix and EasyUbuntu, didn't work. Also tried Pitfdll, didn't work also. I'm gonna try VLC. I'll keep you posted.

moederfietser

---

### Post by moederfietser on 2006-09-03
VLC doesn't work also. Still an over-lightened screen and atrifacts every now and then.

---

