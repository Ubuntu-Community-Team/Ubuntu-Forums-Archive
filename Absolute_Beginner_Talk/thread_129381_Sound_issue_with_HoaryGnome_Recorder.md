---
title: "Sound issue with Hoary/Gnome Recorder"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Oceola on 2006-02-13
When I try and play an mp3 file uploaded by a known source and downloaded from tindeck, when I try to play the file using the Gnome Recorder under Hoary 5.04 I get the following error:
**There is no element present to handle the stream's mime type application/x-id3.**

I've got most or at least what appears to be most of the codecs which allow the playing of mp3s but and have no problems with Ogg-Vorbis. I did notice a comment in the Sound Juicer manual about some Lame Gstreamer pipeline needing to be established and a comment about establishing this pipeline but it was for CD not a direct download of a file to folder. I also have the ESD-Enlightened sound demon, and Sigmatel OSS mixers and have tried both.

Any comment other than upgrading to Breezy would be appreciated. Not being rude on Breezy, I'm on dial up and just don't have the days to spend on the upgrading  and reconfiguring right now. 

Thanks:-k

---

### Post by Stinger on 2006-02-13
Open up the synaptic package manager and try installing the "gstreamer0.8-lame" and "gstreamer0.8-mad" packages , version may differ , I'm using Breezy.
Apt-synaptic will pickup any dependencies and install them for you too.
:-D

---

### Post by Oceola on 2006-02-14
Stinger - Thanks for the answer. It's the Gstreamer0.8 MAD which also calls to libmad0 to download. Installed both , which are in the Community maintained site for Hoary. Mp3's are playing fine in the Gnome Recorder now.

Just a note, I DL'd a lot of the different Gstreamer packages trying to get this to work and the GSstreamer0.8 Lame didn't change things.

Thanks again.:D

---

### Post by David Corrales on 2006-02-14
Why don't you get one of those cool free ubuntu cd's to help your upgrade path? Or maybe wait a bit and get the dapper one since the regular cd now has tons of upgrades and considering your type of connection that's going to be a problem.

---

### Post by Stinger on 2006-02-14
[QUOTE=Oceola]
Just a note, I DL'd a lot of the different Gstreamer packages trying to get this to work and the GSstreamer0.8 Lame didn't change things.
[/QUOTE]

Well I just thought that you might need it later on when you decide to rip your own CD's , LAME supports both CBR and VBR when encoding to mp3 , I use VBR (variable bit rate) , in my opinion LAME is the best mp3 encoder.
:rolleyes:

---

