---
title: "AAC decoding issues"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by keithvella on 2007-08-26
I apologise if this question is being asked for the umpteenth time: Is it possible to listen to AAC-encoded (m4a) audio files on Feisty other than by using the xmms-mp4 plugin? It seems that a plugin from the gstreamer suite is required to play AAC files in Totem, Banshee and Rhythmbox. I have installed the gstreamer plugin suggested when I first attempted to play an mp4 file in Totem but this does not seem to work. I noticed that the file is loaded but playing is choppy and the duration of the track is incorrect. Can anyone offer a solution please?

---

### Post by Jimmyfj on 2007-08-26
Beep media/Audio player should be able to play MP4 Otherwise you could try the VLC player.

---

### Post by albesan on 2007-08-26
hi there,

this may seem really obvious but just in case, have you had a look at this:

[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)

I used this guide today on feisty and I can play anything on Amarok.

a.

---

### Post by keithvella on 2007-08-26
I forgot to mention earlier that not even VLC worked for me. I have just installed Beep Media Player but it seems to require a plugin of some sort for AAC files. I would prefer to get AAC playback working in Banshee etc., if at all possible, rather than use an alternative player which requires a plugin that does not form part of the gstreamer suite. Does this indicate that there is something wrong with the gstreamer plugin?

---

### Post by keithvella on 2007-08-26
Hi albesan,

Many thanks for your reply. I followed the instructions given in the website you pointed me to earlier on today unfortunately to no avail. I haven't had a look at Amarok yet.

Thanks,

Keith

---

### Post by keithvella on 2007-08-27
Has anyone else encountered this issue?

---

### Post by laidback on 2007-08-27
Yes I believe so. I can only play my audio files by loading them onto my ipod from Amarok, then either playback through the headphones or by attaching my active speakers to the ipod. If there is a solution for 7.04 I'd certainly like to hear of it.

Looked at the tread above but it doesn't cover 7.04.

---

### Post by keithvella on 2007-08-27
So do I have to consider another distro or God forbid Windows to solve this problem?

---

### Post by laidback on 2007-08-27
I live in hope, as I simply refuse to go back to windoz.

---

### Post by laidback on 2007-08-27
You might like to try Audacious, it's in the repositories (for 7.04 anyway). It doesn't play the files I have but the plugins suggest that it plays AAC files.

---

### Post by HighSide on 2007-09-19
Hi 

I'm having the same problems, has anyone found a fix?

---

### Post by fenian on 2007-09-19
if you haven't added the [Mediubuntu]("https://help.ubuntu.com/community/Medibuntu") repository do that first.

Then enter this in a terminal...

> sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs libmp4v2-0 libmp4v2-dev faad faac libfaac0 libfaad2-0 libfaad2-dev

This should install everything you need to play most media formats (you probably already have some of these packages installed entering the line shouldnt harm those packages).

---

