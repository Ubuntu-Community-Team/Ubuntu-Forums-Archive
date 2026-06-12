---
title: "Mp3 playback is quiet"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by OA-5599 on 2007-07-28
First Amarok kept freezing if I wanted to play a mp3 file. I installed "libxine1-ffmpeg" and now it plays mp3s but they are really quiet. Mplayer and VLC are quiet, too even if i turn the player volume to 100%.
Movies play in normal volume.
I hope somebody can help me...

---

### Post by swoll1980 on 2007-07-28
Dumb question but is the volume on the amerok player it's self turned up, or if it is is the system volume turned up?

---

### Post by OA-5599 on 2007-07-28
The volume in Amarok is turned up.
I dont know how to turn up the system volume but movies play in normal volume so the system volume shouldnt be the problem, i think.

---

### Post by OA-5599 on 2007-07-29
Now Videos have different Volume levels too.
Even videos from the same format have huge differences...

---

### Post by atomkarinca on 2007-07-29
if you have alsa you should type in terminal

alsamixer

and check whether the system volume is up.

---

### Post by OA-5599 on 2007-07-29
If I put everything on 100% in alsamixer the mp3s seem to have the right volume, but then some of the videos are way too loud.

---

### Post by tomcheng76 on 2007-07-29
in alsamixer
try to lower the PCM and higher the Master
after choose a gd level
type
```

sudo alsactl store 0

```
to store it

---

### Post by grobar on 2007-07-29
I have the master and PCM at the same level and the mp3 and movie files have the same dB level.
Try that and see what happens, I had the same problem like you.

---

### Post by OA-5599 on 2007-07-29
Master is on 100% and if I lower the PCM Level It becomes too quiet again.
What is the "gd level"?

---

### Post by tomcheng76 on 2007-07-29
In amarok setting
engine,  choose xine engine , output choose alsa
or you may try other output like oss
also try this
```

sudo apt-get remove gstreamer0.10-plugins-ugly
sudo apt-get install libxine-extracodecs
sudo apt-get install libxine1-ffmpeg

```

i dunno whether it helps or not...
it seems that your sound card driver problem or something else
what is your sound card?

---

### Post by OA-5599 on 2007-07-29
changes nothing
but thank you anyhow.

Soundcard is "Sound Maker Value Series V1.2" with "C-Media 8738" Chipset

---

### Post by tomcheng76 on 2007-07-29
Movies play in normal volume.
which software au used?

here is the last resort,  just dont try it until the very end
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

---

### Post by OA-5599 on 2007-07-29
ok, its weird:

every mp3 in every player I tried (vlc, mplayer, amarok)  is quiet. 
A Live Video of Mr. Bungle in .avi format is quiet.
A Bill Hicks Video in .avi format is in normal volume.


Now I've turned up Master and PCM in alsamixer to 100% and:

Mp3s and the Mr. Bungle Video play in normal volume.
The Bill Hicks video in mplayer is really loud. If I open the same video in vlc player it's loud and the sound is distorted.

---

### Post by forestpixie on 2007-07-29
you can up the volume in amarok a bit in repect to other apps with the equaliser as well

---

